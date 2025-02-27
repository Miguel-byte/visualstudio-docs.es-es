---
title: 'CA2213: los campos desechables se deben desechar | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8ebeae3e5e367bb2c1a09bc1cb38dcc80d2c3826
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662893"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: Aplique Dispose a los campos a los que se pueda
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|Identificador de comprobación|CA2213|
|Categoría|Microsoft. Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Un tipo que implementa <xref:System.IDisposable?displayProperty=fullName> declara campos que son de tipos que también implementan <xref:System.IDisposable>. El método de <xref:System.IDisposable.Dispose%2A> del tipo declarativo no llama al método <xref:System.IDisposable.Dispose%2A> del campo.

## <a name="rule-description"></a>Descripción de la regla
 Un tipo es responsable de la eliminación de todos sus recursos no administrados. Esto se logra implementando <xref:System.IDisposable>. Esta regla comprueba si un tipo descartable `T` declara un campo `F` que es una instancia de un tipo descartable `FT`. Para cada `F` de campo, la regla intenta encontrar una llamada a `FT.Dispose`. La regla busca los métodos llamados por `T.Dispose` y un nivel inferior (los métodos llamados por los métodos llamados por `FT.Dispose`).

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, llame a <xref:System.IDisposable.Dispose%2A> en los campos que son de tipos que implementan <xref:System.IDisposable> si es responsable de la asignación y la liberación de los recursos no administrados mantenidos por el campo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si no es responsable de liberar el recurso mantenido por el campo, o si la llamada a <xref:System.IDisposable.Dispose%2A> tiene lugar en un nivel de llamada más profundo que las comprobaciones de la regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo `TypeA` que implementa <xref:System.IDisposable> (`FT` en la explicación anterior).

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo `TypeB` que infringe esta regla al declarar un campo `aFieldOfADisposableType` (`F` en la explicación anterior) como un tipo descartable (`TypeA`) y no llamar a <xref:System.IDisposable.Dispose%2A> en el campo. `TypeB` corresponde a `T` de la explicación anterior.

 [!code-csharp[FxCop.Usage.IDisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableFields/cs/FxCop.Usage.IDisposableFields.cs#1)]

## <a name="see-also"></a>Vea también
 <xref:System.IDisposable?displayProperty=fullName> [modelo de Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
