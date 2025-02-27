---
title: 'CA1023: los indizadores no deben ser multidimensionales | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IndexersShouldNotBeMultidimensional
- CA1023
helpviewer_keywords:
- CA1023
- IndexersShouldNotBeMultidimensional
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1b7c4c82add8644a1c2c213536c2ad3c0097c3a6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661990"
---
# <a name="ca1023-indexers-should-not-be-multidimensional"></a>CA1023: Los indizadores no deben ser multidimensionales
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IndexersShouldNotBeMultidimensional|
|Identificador de comprobación|CA1023|
|Categoría|Microsoft. Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo público o protegido contiene un indexador público o protegido que usa más de un índice.

## <a name="rule-description"></a>Descripción de la regla
 Los indexadores, es decir, las propiedades indizadas, deben usar un solo índice. Los indexadores multidimensionales pueden reducir significativamente la facilidad de uso de la biblioteca. Si el diseño requiere varios índices, reconsidere si el tipo representa un almacén de datos lógico. Si no es así, use un método.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie el diseño para usar un índice de cadena o entero solitario, o bien use un método en lugar del indexador.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla solo después de considerar detenidamente la necesidad del indexador no estándar.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo, `DayOfWeek03`, con un indexador multidimensional que infringe la regla. El indizador se puede ver como un tipo de conversión y, por tanto, se expone más adecuadamente como un método. El tipo se ha rediseñado en `RedesignedDayOfWeek03` para satisfacer la regla.

 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/cpp/FxCop.Design.OneDimensionForIndexer.cpp#1)]
 [!code-csharp[FxCop.Design.OneDimensionForIndexer#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/cs/FxCop.Design.OneDimensionForIndexer.cs#1)]
 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/vb/FxCop.Design.OneDimensionForIndexer.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1043: Utilizar argumento integral o de cadena para los indizadores](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)

 [CA1024: Utilizar las propiedades donde corresponda](../code-quality/ca1024-use-properties-where-appropriate.md)
