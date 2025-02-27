---
title: 'CA1027: marcar enumeraciones con FlagsAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkEnumsWithFlags
- CA1027
helpviewer_keywords:
- CA1027
- MarkEnumsWithFlags
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6f2dc7dcd79fbcaf47a2db3cf49f22f3467a06ab
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661932"
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027: Marcar enumeraciones con FlagsAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkEnumsWithFlags|
|Identificador de comprobación|CA1027|
|Categoría|Microsoft. Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Los valores de una enumeración pública son potencias de dos o son combinaciones de otros valores que se definen en la enumeración y el atributo <xref:System.FlagsAttribute?displayProperty=fullName> no está presente. Para reducir los falsos positivos, esta regla no notifica una infracción de las enumeraciones que tienen valores contiguos.

## <a name="rule-description"></a>Descripción de la regla
 Una enumeración es un tipo de valor que define un conjunto de constantes con nombre relacionadas. Aplique <xref:System.FlagsAttribute> a una enumeración cuando se puedan combinar con sentido las constantes con nombre. Por ejemplo, considere una enumeración de los días de la semana en una aplicación que realiza un seguimiento de los recursos del día que están disponibles. Si la disponibilidad de cada recurso se codifica mediante la enumeración que tiene <xref:System.FlagsAttribute>, se puede representar cualquier combinación de días. Sin el atributo, solo se puede representar un día de la semana.

 En el caso de los campos que almacenan enumeraciones combinables, los valores de enumeración individuales se tratan como grupos de bits en el campo. Por lo tanto, estos campos a veces se denominan *campos de bits*. Para combinar los valores de enumeración para el almacenamiento en un campo de bits, utilice los operadores condicionales booleanos. Para probar un campo de bits para determinar si un valor de enumeración específico está presente, utilice los operadores lógicos booleanos. Para un campo de bits para almacenar y recuperar correctamente los valores de enumeración combinados, cada valor que se define en la enumeración debe ser una potencia de dos. A menos que esto sea así, los operadores lógicos booleanos no podrán extraer los valores de enumeración individuales almacenados en el campo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, agregue <xref:System.FlagsAttribute> a la enumeración.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla si no desea que los valores de enumeración sean combinables.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente, `DaysEnumNeedsFlags` es una enumeración que cumple los requisitos para usar <xref:System.FlagsAttribute>, pero no lo tiene. La enumeración `ColorEnumShouldNotHaveFlag` no tiene valores que sean potencias de dos, pero especifica incorrectamente <xref:System.FlagsAttribute>. Esto infringe la regla [CA2217: no marcar enumeraciones con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md).

 [!code-csharp[FxCop.Design.EnumFlags#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumFlags/cs/FxCop.Design.EnumFlags.cs#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2217: No marcar enumeraciones con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Vea también
 <xref:System.FlagsAttribute?displayProperty=fullName>
