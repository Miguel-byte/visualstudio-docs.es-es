---
title: 'CA1039: las listas están fuertemente tipadas | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1039
- ListsAreStronglyTyped
helpviewer_keywords:
- CA1039
- ListsAreStronglyTyped
ms.assetid: 5ac366c4-fd87-4d5c-95d5-f755510c8e5c
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8845fb8bcd08f076ddc3c509a37948cf008e0623
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661802"
---
# <a name="ca1039-lists-are-strongly-typed"></a>CA1039: Las listas están fuertemente tipadas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ListsAreStronglyTyped|
|Identificador de comprobación|CA1039|
|Categoría|Microsoft. Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 El tipo público o protegido implementa <xref:System.Collections.IList?displayProperty=fullName> pero no proporciona un método fuertemente tipado para uno o varios de los siguientes elementos:

- IList. Item

- IList. Add

- IList. Contains

- IList. IndexOf

- IList. Insert

- IList. Remove

## <a name="rule-description"></a>Descripción de la regla
 Esta regla requiere que las implementaciones de <xref:System.Collections.IList> proporcionen miembros fuertemente tipados para que los usuarios no necesiten convertir los argumentos en el tipo de <xref:System.Object?displayProperty=fullName> cuando utilicen la funcionalidad proporcionada por la interfaz. La interfaz de <xref:System.Collections.IList> se implementa mediante colecciones de objetos a los que se puede tener acceso por índice. Esta regla supone que el tipo que implementa <xref:System.Collections.IList> lo hace para administrar una colección de instancias de un tipo que es más seguro que <xref:System.Object>.

 <xref:System.Collections.IList> implementa las interfaces <xref:System.Collections.ICollection?displayProperty=fullName> y <xref:System.Collections.IEnumerable?displayProperty=fullName>. Si implementa <xref:System.Collections.IList>, debe proporcionar los miembros fuertemente tipados necesarios para <xref:System.Collections.ICollection>. Si los objetos de la colección amplían <xref:System.ValueType?displayProperty=fullName>, debe proporcionar un miembro fuertemente tipado para <xref:System.Collections.IEnumerable.GetEnumerator%2A> para evitar la disminución del rendimiento que se debe a la conversión boxing; Esto no es necesario cuando los objetos de la colección son un tipo de referencia.

 Para cumplir esta regla, implemente los miembros de interfaz explícitamente utilizando nombres con el formato InterfaceName. Nombredemiembrodeinterfaz, como <xref:System.Collections.IList.Add%2A>. Los miembros de interfaz explícitos usan los tipos de datos declarados por la interfaz. Implemente los miembros fuertemente tipados utilizando el nombre del miembro de interfaz, como `Add`. Declare los miembros fuertemente tipados como públicos y declare los parámetros y los valores devueltos para que sean del tipo seguro administrado por la colección. Los tipos seguros reemplazan a los tipos más débiles como <xref:System.Object> y <xref:System.Array> declarados por la interfaz.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, implemente explícitamente <xref:System.Collections.IList> miembros y proporcione alternativas fuertemente tipadas para los miembros que se han mencionado anteriormente. Para el código que implementa correctamente la interfaz <xref:System.Collections.IList> y proporciona los miembros fuertemente tipados necesarios, vea el ejemplo siguiente.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla al implementar una nueva colección basada en objetos, como una lista vinculada, donde los tipos que extienden la nueva colección determinan el tipo seguro. Estos tipos deben cumplir esta regla y exponer miembros fuertemente tipados.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente, el tipo `YourType` extiende <xref:System.Collections.CollectionBase?displayProperty=fullName>, al igual que todas las colecciones fuertemente tipadas. Tenga en cuenta que <xref:System.Collections.CollectionBase> proporciona la implementación explícita de la interfaz <xref:System.Collections.IList>. Por lo tanto, debe proporcionar solo los miembros fuertemente tipados para <xref:System.Collections.IList> y <xref:System.Collections.ICollection>.

 [!code-csharp[FxCop.Design.IListStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IListStrongTypes/cs/FxCop.Design.IListStrongTypes.cs#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1035: Las implementaciones de ICollection tienen miembros fuertemente tipados](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1038: Los enumeradores deben estar fuertemente tipados](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

## <a name="see-also"></a>Vea también
 <xref:System.Collections.CollectionBase?displayProperty=fullName> <xref:System.Collections.ICollection?displayProperty=fullName>
 <xref:System.Collections.IEnumerable?displayProperty=fullName>
 <xref:System.Collections.IList?displayProperty=fullName>
 <xref:System.Object?displayProperty=fullName>
