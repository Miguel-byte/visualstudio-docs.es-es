---
title: 'CA1018: marcar atributos con AttributeUsageAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
helpviewer_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 404ef250726d12300e2b72150ff42b4f0b7bfb24
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662048"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018: Marcar atributos con AttributeUsageAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAttributesWithAttributeUsage|
|Identificador de comprobación|CA1018|
|Categoría|Microsoft. Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 El atributo <xref:System.AttributeUsageAttribute?displayProperty=fullName> no está presente en el atributo personalizado.

## <a name="rule-description"></a>Descripción de la regla
 Al definir un atributo personalizado, márquelo con <xref:System.AttributeUsageAttribute> para indicar en qué lugar del código fuente se puede aplicar el atributo personalizado. El significado de un atributo y el uso que se le va a dar determinará sus ubicaciones válidas en código. Por ejemplo, podría definir un atributo que identifique a la persona responsable de mantener y mejorar cada tipo en una biblioteca, y esa responsabilidad siempre se asigna en el nivel de tipo. En este caso, los compiladores deberían habilitar el atributo en las clases, enumeraciones e interfaces, pero no deben habilitarlo en métodos, eventos o propiedades. Las directivas y los procedimientos de la organización determinarán si el atributo debe estar habilitado en los ensamblados.

 La enumeración <xref:System.AttributeTargets?displayProperty=fullName> define los destinos que se pueden especificar para un atributo personalizado. Si omite <xref:System.AttributeUsageAttribute>, el atributo personalizado será válido para todos los destinos, tal y como se define en el valor `All` de <xref:System.AttributeTargets> enumeración.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, especifique los destinos para el atributo mediante <xref:System.AttributeUsageAttribute>. Vea el ejemplo siguiente.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Debe corregir una infracción de esta regla en lugar de excluir el mensaje. Incluso si el atributo hereda <xref:System.AttributeUsageAttribute>, el atributo debe estar presente para simplificar el mantenimiento del código.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se definen dos atributos. `BadCodeMaintainerAttribute` omite incorrectamente la instrucción <xref:System.AttributeUsageAttribute> y `GoodCodeMaintainerAttribute` implementa correctamente el atributo descrito anteriormente en esta sección. Tenga en cuenta que la regla de diseño requiere la `DeveloperName` de la propiedad [CA1019: definir los descriptores de acceso para los argumentos de atributo](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) y se incluye por integridad.

 [!code-csharp[FxCop.Design.AttributeUsage#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeUsage/cs/FxCop.Design.AttributeUsage.cs#1)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeUsage/vb/FxCop.Design.AttributeUsage.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1019: Definir descriptores de acceso para los argumentos de atributo](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1813: Evitar atributos no sellados](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Vea también
 [Atributos](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)
