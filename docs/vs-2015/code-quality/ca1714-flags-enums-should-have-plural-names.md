---
title: 'CA1714: las enumeraciones Flags deben tener nombres en plural | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- FlagsEnumsShouldHavePluralNames
- CA1714
helpviewer_keywords:
- CA1714
- FlagsEnumsShouldHavePluralNames
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ca3709411f50d0b65f33bb8eed6457cfd1325ff6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669132"
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714: Las enumeraciones Flags deberían tener nombres en plural
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|FlagsEnumsShouldHavePluralNames|
|Identificador de comprobación|CA1714|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Una enumeración pública tiene el <xref:System.FlagsAttribute?displayProperty=fullName> y su nombre no termina en ' '.

## <a name="rule-description"></a>Descripción de la regla
 Los tipos marcados con <xref:System.FlagsAttribute> tienen nombres en plural porque el atributo indica que se puede especificar más de un valor. Por ejemplo, una enumeración que define los días de la semana puede estar pensada para su uso en una aplicación donde se pueden especificar varios días. Esta enumeración debe tener el <xref:System.FlagsAttribute> y se podría llamar ' Days '. Una enumeración similar que permite especificar un solo día no tendría el atributo y se podría llamar ' Day '.

 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Haga que el nombre de la enumeración sea una palabra plural o quite el atributo <xref:System.FlagsAttribute> si no se deben especificar varios valores de enumeración simultáneamente.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una infracción si el nombre es una palabra en plural pero no termina en ' '. Por ejemplo, si la enumeración de varios días que se ha descrito anteriormente se denominara "DaysOfTheWeek", esto infringiría la lógica de la regla pero no su intención. Dichas infracciones deben suprimirse.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1027: Marcar enumeraciones con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: No marcar enumeraciones con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Vea también
 <xref:System.FlagsAttribute?displayProperty=fullName> [diseño de enumeración](https://msdn.microsoft.com/library/dd53c952-9d9a-4736-86ff-9540e815d545)
