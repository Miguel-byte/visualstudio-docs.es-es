---
title: 'CA1038: los enumeradores deben tener establecimiento inflexible de tipos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
helpviewer_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c3a08f4987fe57a94aaee8f3df6129782fd6448c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661765"
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038: Los enumeradores deben estar fuertemente tipados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|EnumeratorsShouldBeStronglyTyped|
|Identificador de comprobación|CA1038|
|Categoría|Microsoft. Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo público o protegido implementa <xref:System.Collections.IEnumerator?displayProperty=fullName> pero no proporciona una versión fuertemente tipada de la propiedad <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName>. Los tipos que se derivan de los tipos siguientes están exentos de esta regla:

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

## <a name="rule-description"></a>Descripción de la regla
 Esta regla requiere que las implementaciones de <xref:System.Collections.IEnumerator> también proporcionen una versión fuertemente tipada de la propiedad <xref:System.Collections.IEnumerator.Current%2A> para que no sea necesario que los usuarios conviertan el valor devuelto al tipo Strong cuando utilicen la funcionalidad proporcionada por la interfaz. Esta regla supone que el tipo que implementa <xref:System.Collections.IEnumerator> contiene una colección de instancias de un tipo que es más seguro que <xref:System.Object>.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, implemente explícitamente la propiedad de interfaz (declárela como `IEnumerator.Current`). Agregue una versión pública fuertemente tipada de la propiedad, declarada como `Current`, y haga que devuelva un objeto fuertemente tipado.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla al implementar un enumerador basado en objetos para usarlo con una colección basada en objetos, como un árbol binario. Los tipos que extienden la nueva colección definirán el enumerador fuertemente tipado y expondrán la propiedad fuertemente tipada.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra la manera correcta de implementar un tipo de <xref:System.Collections.IEnumerator> fuertemente tipado.

 [!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IEnumeratorStrongTypes/cs/FxCop.Design.IEnumeratorStrongTypes.cs#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1035: Las implementaciones de ICollection tienen miembros fuertemente tipados](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1039: Las listas están fuertemente tipadas](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Vea también
 <xref:System.Collections.IEnumerator?displayProperty=fullName> <xref:System.Collections.CollectionBase?displayProperty=fullName>
 <xref:System.Collections.DictionaryBase?displayProperty=fullName>
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
