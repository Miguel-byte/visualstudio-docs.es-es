---
title: 'CA2111: los punteros no deben ser visibles | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PointersShouldNotBeVisible
- CA2111
helpviewer_keywords:
- CA2111
- PointersShouldNotBeVisible
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a0d5546c6f6a2f5dbd0c6063f4a1dfd40ce1d7bb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658735"
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111: Los punteros no deberían estar visibles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PointersShouldNotBeVisible|
|Identificador de comprobación|CA2111|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un campo <xref:System.IntPtr?displayProperty=fullName> o <xref:System.UIntPtr?displayProperty=fullName> público o protegido no es de solo lectura.

## <a name="rule-description"></a>Descripción de la regla
 <xref:System.IntPtr> y <xref:System.UIntPtr> son tipos de puntero que se utilizan para tener acceso a la memoria no administrada. Si un puntero no es privado, interno o de solo lectura, el código malintencionado puede cambiar el valor del puntero, permitiendo potencialmente el acceso a ubicaciones arbitrarias en memoria o provocando errores del sistema o de la aplicación.

 Si desea proteger el acceso al tipo que contiene el campo de puntero, vea [CA2112: los tipos seguros no deben exponer los campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Proteja el puntero haciéndolo de solo lectura, interno o privado.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla si no se basa en el valor del puntero.

## <a name="example"></a>Ejemplo
 En el código siguiente se muestran punteros que infringen y satisfacen la regla. Observe que los punteros no privados también infringen la regla [CA1051: no declarar campos de instancia visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

 [!code-csharp[FxCop.Security.PointersArePrivate#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PointersArePrivate/cs/FxCop.Security.PointersArePrivate.cs#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2112: Los tipos seguros no deberían exponer campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA1051: No declarar campos de instancia visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Vea también
 <xref:System.IntPtr?displayProperty=fullName> <xref:System.UIntPtr?displayProperty=fullName>
