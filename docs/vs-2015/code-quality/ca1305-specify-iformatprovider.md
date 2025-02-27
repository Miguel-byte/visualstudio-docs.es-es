---
title: 'CA1305: especifique IFormatProvider | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyIFormatProvider
- CA1305
helpviewer_keywords:
- CA1305
- SpecifyIFormatProvider
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 299e8bfec526dc3a5e8dc166d9ab405d51037cbe
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661437"
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305: Especificar IFormatProvider
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyIFormatProvider|
|Identificador de comprobación|CA1305|
|Categoría|Microsoft. Globalization|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un método o constructor llama a uno o varios miembros que tienen sobrecargas que aceptan un parámetro <xref:System.IFormatProvider?displayProperty=fullName>, y el método o constructor no llama a la sobrecarga que toma el parámetro <xref:System.IFormatProvider>. Esta regla omite las llamadas a métodos [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] que se documentan como omitir el parámetro <xref:System.IFormatProvider> y, además, los métodos siguientes:

- <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>

## <a name="rule-description"></a>Descripción de la regla
 Cuando no se proporciona un objeto <xref:System.Globalization.CultureInfo?displayProperty=fullName> o <xref:System.IFormatProvider>, es posible que el valor predeterminado proporcionado por el miembro sobrecargado no tenga el efecto deseado en todas las configuraciones regionales. Además, los miembros de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] eligen la referencia cultural y el formato predeterminados en función de las suposiciones que podrían no ser correctas para el código. Para asegurarse de que el código funciona según lo previsto en los escenarios, debe proporcionar información específica de la referencia cultural según las siguientes directrices:

- Si el valor se va a mostrar al usuario, use la referencia cultural actual. Consulte <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.

- Si el valor se almacenará y tendrá acceso a él el software (almacenado en un archivo o base de datos), use la referencia cultural de todos los idiomas. Consulte <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.

- Si no conoce el destino del valor, haga que el consumidor de datos o el proveedor especifiquen la referencia cultural.

  Tenga en cuenta que <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> solo se utiliza para recuperar recursos localizados mediante una instancia de la clase <xref:System.Resources.ResourceManager?displayProperty=fullName>.

  Incluso si el comportamiento predeterminado del miembro sobrecargado es adecuado para sus necesidades, es mejor llamar explícitamente a la sobrecarga específica de la referencia cultural para que el código se autodocumente y se mantenga más fácilmente.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, use la sobrecarga que toma un <xref:System.Globalization.CultureInfo> o <xref:System.IFormatProvider> y especifique el argumento de acuerdo con las instrucciones que se enumeraron anteriormente.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla cuando está seguro de que el proveedor de formato o referencia cultural predeterminado es la opción correcta y donde el mantenimiento del código no es una prioridad de desarrollo importante.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente, `BadMethod` provoca dos infracciones de esta regla. `GoodMethod` corrige la primera infracción pasando la referencia cultural de todos los idiomas a <xref:System.String.Compare%2A> y corrige la segunda infracción pasando la referencia cultural actual a <xref:System.String.ToLower%2A> porque `string3` se muestra al usuario.

 [!code-csharp[FxCop.Globalization.CultureInfo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.CultureInfo/cs/FxCop.Globalization.CultureInfo.cs#1)]

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra el efecto de la referencia cultural actual en el <xref:System.IFormatProvider> predeterminado seleccionado por el tipo de <xref:System.DateTime>.

 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.IFormatProvider/cs/FxCop.Globalization.IFormatProvider.cs#1)]

 Este ejemplo produce el siguiente resultado:

 **6/4/1900 12:15:12 PM** 
**06/04/1900 12:15:12**
## <a name="related-rules"></a>Reglas relacionadas
 [CA1304: Especificar CultureInfo](../code-quality/ca1304-specify-cultureinfo.md)

## <a name="see-also"></a>Vea también
 [NIB: usar la clase CultureInfo](https://msdn.microsoft.com/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)
