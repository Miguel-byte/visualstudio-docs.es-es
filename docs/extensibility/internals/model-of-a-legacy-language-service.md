---
title: Modelo de un servicio de lenguaje heredado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5b87106060d3fd66b3659f5d49159ebbb9be9ef6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726386"
---
# <a name="model-of-a-legacy-language-service"></a>Modelo de un servicio de lenguaje heredado
Un servicio de lenguaje define los elementos y las características de un lenguaje específico y se usa para proporcionar al editor información específica de ese idioma. Por ejemplo, el editor necesita conocer los elementos y las palabras clave del lenguaje con el fin de admitir el color de la sintaxis.

 El servicio de lenguaje funciona estrechamente con el búfer de texto administrado por el editor y la vista que contiene el editor. La opción **información rápida** de Microsoft IntelliSense es un ejemplo de una característica proporcionada por un servicio de lenguaje.

## <a name="a-minimal-language-service"></a>Un servicio de lenguaje mínimo
 El servicio de lenguaje más básico contiene los dos objetos siguientes:

- El *servicio de lenguaje* implementa la interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>. Un servicio de lenguaje tiene información sobre el lenguaje, incluidos el nombre, las extensiones de nombre de archivo, el administrador de la ventana de código y el coloreador.

- El *coloreador* implementa la interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>.

  El siguiente dibujo conceptual muestra un modelo de un servicio de lenguaje básico.

  ![Gráfico de modelo de servicio de lenguaje](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel") Modelo de servicio de lenguaje básico

  La ventana de documento hospeda la *vista de documento* del editor, en este caso, el editor de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Core. La vista de documento y el búfer de texto son propiedad del editor. Estos objetos funcionan con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a través de una ventana de documento especializada denominada *ventana de código*. La ventana de código se encuentra en un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objeto creado y controlado por el IDE.

  Cuando se carga un archivo con una extensión determinada, el editor busca el servicio de lenguaje asociado a esa extensión y lo pasa a la ventana de código llamando al método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>. El servicio de lenguaje devuelve un *Administrador de ventanas de código*, que implementa la interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>.

  En la tabla siguiente se proporciona información general sobre los objetos del modelo.

| Componente | Object | Función |
|------------------| - | - |
| Búfer de texto | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> | Secuencia de texto de lectura/escritura Unicode. El texto puede usar otras codificaciones. |
| Ventana Código | <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> | Ventana de documento que contiene una o más vistas de texto. Cuando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] está en modo de interfaz de múltiples documentos (MDI), la ventana de código es un elemento secundario de MDI. |
| Vista de texto | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> | Ventana que permite al usuario navegar y ver texto mediante el teclado y el mouse. Aparece una vista de texto para el usuario como editor. Puede usar vistas de texto en ventanas de editor normales, en la ventana de salida y en la ventana inmediato. Además, puede configurar una o varias vistas de texto dentro de una ventana de código. |
| Administrador de texto | Administrado por el servicio <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>, desde el que se obtiene un puntero <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> | Componente que mantiene la información común compartida por todos los componentes descritos anteriormente. |
| Servicio de lenguaje | Dependiente de la implementación; implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> | Objeto que proporciona al editor información específica del lenguaje, como el resaltado de sintaxis, la finalización de instrucciones y la coincidencia de llaves. |

## <a name="see-also"></a>Vea también
- [Datos de documento y vista de documento en editores personalizados](../../extensibility/document-data-and-document-view-in-custom-editors.md)