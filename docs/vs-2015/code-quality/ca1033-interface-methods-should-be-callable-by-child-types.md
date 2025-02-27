---
title: 'CA1033: los tipos secundarios deben poder llamar a los métodos de interfaz | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InterfaceMethodsShouldBeCallableByChildTypes
- CA1033
helpviewer_keywords:
- CA1033
- InterfaceMethodsShouldBeCallableByChildTypes
ms.assetid: 9f171497-a5e3-4769-a77b-7aed755b2662
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2ee44537ba4f7f7efd65de2c8a27d139d9750b77
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661865"
---
# <a name="ca1033-interface-methods-should-be-callable-by-child-types"></a>CA1033: Los tipos secundarios deberían poder llamar a los métodos de interfaz
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InterfaceMethodsShouldBeCallableByChildTypes|
|Identificador de comprobación|CA1033|
|Categoría|Microsoft. Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un tipo no sellado visible externamente proporciona un método explícito de implementación de una interfaz pública pero no proporciona un método visible externamente alternativo con el mismo nombre.

## <a name="rule-description"></a>Descripción de la regla
 Considere un tipo base que implementa explícitamente un método de interfaz pública. Un tipo que se deriva del tipo base solo puede tener acceso al método de interfaz heredado a través de una referencia a la instancia C#actual (`this` en) que se convierte en la interfaz. Si el tipo derivado vuelve a implementar (explícitamente) el método de interfaz heredado, ya no se puede tener acceso a la implementación base. La llamada a través de la referencia de la instancia actual invocará la implementación derivada; Esto produce una recursividad y un desbordamiento de pila eventual.

 Esta regla no notifica una infracción de una implementación explícita de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> cuando se proporciona un método de `Close()` o `System.IDisposable.Dispose(Boolean)` visible externamente.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, implemente un nuevo método que exponga la misma funcionalidad y sea visible para los tipos derivados o cambie a una implementación no explícita. Si un cambio importante es aceptable, una alternativa es convertir el tipo en sellado.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si se proporciona un método visible externamente con la misma funcionalidad pero con un nombre diferente del método implementado explícitamente.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo, `ViolatingBase`, que infringe la regla y un tipo, `FixedBase`, que muestra una corrección para la infracción.

 [!code-csharp[FxCop.Design.ExplicitMethodImplementations#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExplicitMethodImplementations/cs/FxCop.Design.ExplicitMethodImplementations.cs#1)]

## <a name="see-also"></a>Vea también
 [Interfaces](https://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37)
