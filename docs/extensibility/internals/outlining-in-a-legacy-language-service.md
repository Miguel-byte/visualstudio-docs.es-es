---
title: Esquematización en un servicio de lenguaje heredado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6b2ba55a2e77a1f7261812a181ad780c2ef2b71
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726175"
---
# <a name="outlining-in-a-legacy-language-service"></a>Esquematización en un servicio de lenguaje heredado
La esquematización permite contraer un programa complejo en una introducción o un esquema. Por ejemplo, en C# todos los métodos se puede contraer en una sola línea, mostrando solo la firma del método. Además, las estructuras y las clases se pueden contraer para mostrar solo los nombres de las estructuras y las clases. Dentro de un único método, la lógica compleja se puede contraer para mostrar el flujo global mostrando solo la primera línea de instrucciones, como `foreach`, `if` y `while`.

 Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la forma más reciente de implementar las características del servicio de lenguaje es usar extensiones de MEF. Para obtener más información, vea [Tutorial: esquematización](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
> Le recomendamos que empiece a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento del servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.

## <a name="enabling-support-for-outlining"></a>Habilitar la compatibilidad con la esquematización
 La entrada del registro `AutoOutlining` está establecida en 1 para habilitar la esquematización automática. La esquematización automática configura un análisis de todo el origen cuando se carga o se cambia un archivo con el fin de identificar regiones ocultas y mostrar los glifos de esquematización. El usuario también puede controlar manualmente la esquematización.

 El valor de la entrada del registro `AutoOutlining` se puede obtener a través de la propiedad <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> de la clase <xref:Microsoft.VisualStudio.Package.LanguagePreferences>. La entrada del registro `AutoOutlining` se puede inicializar con un parámetro con nombre en el atributo <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> (consulte [registro de un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md) para obtener más información).

## <a name="the-hidden-region"></a>La región oculta
 Para proporcionar la esquematización, el servicio de lenguaje debe admitir regiones ocultas. Se trata de intervalos de texto que se pueden expandir o contraer. Las regiones ocultas se pueden delimitar mediante símbolos de lenguaje estándar, como llaves o símbolos personalizados. Por ejemplo, C# tiene un `#region` / `#endregion` par que delimita una región oculta.

 Las regiones ocultas se administran mediante el administrador de regiones ocultas, que se expone como la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>.

 En la esquematización se usan regiones ocultas la interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> y contienen el intervalo de la región oculta, el estado visible actual y el banner que se va a mostrar cuando se contrae el intervalo.

 El analizador del servicio de lenguaje usa el método <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> para agregar una nueva región oculta con el comportamiento predeterminado para las regiones ocultas, mientras que el método <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> permite personalizar la apariencia y el comportamiento del contorno. Una vez que se proporcionan regiones ocultas a la sesión de la región oculta, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] administra las regiones ocultas para el servicio de lenguaje.

 Si tiene que determinar cuándo se destruye la sesión de la región oculta, se cambia una región oculta o debe asegurarse de que una región oculta determinada esté visible; debe derivar una clase de la <xref:Microsoft.VisualStudio.Package.Source> clase e invalidar los métodos adecuados, <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A>, <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A> y <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>, respectivamente.

### <a name="example"></a>Ejemplo
 Este es un ejemplo simplificado de la creación de regiones ocultas para todos los pares de llaves. Se supone que el lenguaje proporciona coincidencia de llaves y que las llaves que deben coincidir incluyen al menos las llaves ({y}). Este enfoque se utiliza únicamente con fines ilustrativos. Una implementación completa tendría un control completo de los casos en <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>. En este ejemplo también se muestra cómo establecer la preferencia <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> en `true` temporalmente. Una alternativa consiste en especificar el `AutoOutlining` parámetro con nombre en el atributo de `ProvideLanguageServiceAttribute` en el paquete de idioma.

 En este ejemplo C# se da por supuesto reglas para comentarios, cadenas y literales.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace MyLanguagePackage
{

    public class MyLanguageService : LanguageService
    {
        private LanguagePreferences m_preferences;

        public override LanguagePreferences  GetLanguagePreferences()
        {
            if (m_preferences == null)
            {
                m_preferences = new LanguagePreferences(this.Site,
                                                        typeof(MyLanguageService).GUID,
                                                        Name);
                m_preferences.Init();
                // Temporarily enabled auto-outlining
                m_preferences.AutoOutlining = true;
            }
            return m_preferences;
        }

        public override AuthoringScope  ParseSource(ParseRequest req)
        {
            Source source = (Source) this.GetSource(req.FileName);
            switch (req.Reason)
            {
               case ParseReason.HighlightBraces:
               case ParseReason.MatchBraces:
               case ParseReason.MemberSelectAndHighlightBraces:
                  if (source.Braces != null)
                  {
                      foreach (TextSpan[] brace in source.Braces)
                      {
                         if (brace.Length == 2)
                         {
                             if (req.Sink.HiddenRegions == true
                                   && source.GetText(brace[0]).Equals("{")
                                   && source.GetText(brace[1]).Equals("}"))
                             {
                                //construct a TextSpan of everything between the braces
                                TextSpan hideSpan = new TextSpan();
                                hideSpan.iStartIndex = brace[0].iStartIndex;
                                hideSpan.iStartLine = brace[0].iStartLine;
                                hideSpan.iEndIndex = brace[1].iEndIndex;
                                hideSpan.iEndLine = brace[1].iEndLine;
                                req.Sink.ProcessHiddenRegions = true;
                                req.Sink.AddHiddenRegion(hideSpan);
                             }
                             req.Sink.MatchPair(brace[0], brace[1], 1);
                         }
                         else if (brace.Length >= 3)
                             req.Sink.MatchTriple(brace[0], brace[1], brace[2], 1);
                  }
        }
                   break;
               default:
                   break;
      }
            // Must always return a valid AuthoringScope object.
            return new MyAuthoringScope();
        }
    }
}
```

## <a name="see-also"></a>Vea también
- [Características del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-features1.md)
- [Registro de un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md)