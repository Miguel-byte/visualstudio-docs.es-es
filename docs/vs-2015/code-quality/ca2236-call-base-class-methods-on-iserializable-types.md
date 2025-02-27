---
title: 'CA2236: llamar a métodos de clase base en tipos ISerializable | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
helpviewer_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
ms.assetid: 5a15b20d-769c-4640-b31a-36e07077daae
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1d06d4acff24b724388e36de66038f563b1f5dc6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666708"
---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>LCA2236: Llamar a métodos de clase base en tipos ISerializable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallBaseClassMethodsOnISerializableTypes|
|Identificador de comprobación|CA2236|
|Categoría|Microsoft. Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Un tipo se deriva de un tipo que implementa la interfaz <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> y se cumple una de las condiciones siguientes:

- El tipo implementa el constructor de serialización, es decir, un constructor con la firma del parámetro <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>, <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>, pero no llama al constructor de serialización del tipo base.

- El tipo implementa el método <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> pero no llama al método <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> del tipo base.

## <a name="rule-description"></a>Descripción de la regla
 En un proceso de serialización personalizado, un tipo implementa el método <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> para serializar sus campos y el constructor de serialización para deserializar los campos. Si el tipo se deriva de un tipo que implementa la interfaz <xref:System.Runtime.Serialization.ISerializable>, se debe llamar al método de <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> y al constructor de serialización para serializar o deserializar los campos del tipo base. De lo contrario, el tipo no se serializará y deserializará correctamente. Tenga en cuenta que si el tipo derivado no agrega ningún campo nuevo, el tipo no necesita implementar el método <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> ni el constructor de serialización ni llamar a los equivalentes de tipo base.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, llame al tipo base <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método o al constructor de serialización desde el constructor o el método de tipo derivado correspondiente.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo derivado que satisface la regla llamando al constructor de serialización y <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método de la clase base.

 [!code-csharp[FxCop.Usage.CallBaseISerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/cs/FxCop.Usage.CallBaseISerializable.cs#1)]
 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/vb/FxCop.Usage.CallBaseISerializable.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2240: Implementar ISerializable correctamente](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Implementar constructores de serialización](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Implementar métodos de serialización correctamente](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Marcar todos los campos no serializables](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: Marcar los tipos ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: Proporcionar métodos de deserialización para campos opcionales](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Proteger los constructores de serializaciones](../code-quality/ca2120-secure-serialization-constructors.md)
