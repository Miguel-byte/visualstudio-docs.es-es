---
title: 'CA1816: llama a GC. SuppressFinalize correctamente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1816
- DisposeMethodsShouldCallSuppressFinalize
helpviewer_keywords:
- DisposeMethodsShouldCallSuppressFinalize
- CA1816
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: acc86c278faa877897d294e72632762eff834a76
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668385"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816: Llamar a GC.SuppressFinalize correctamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|Identificador de comprobación|CA1816|
|Categoría|Microsoft. Uso|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo

- Un método que es una implementación de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> no llama a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

- Un método que no es una implementación de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> llama a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

- Un método llama a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> y pasa algo distinto de This (me en Visual Basic).

## <a name="rule-description"></a>Descripción de la regla
 El método <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> permite a los usuarios liberar recursos en cualquier momento antes de que el objeto esté disponible para la recolección de elementos no utilizados. Si se llama al método <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>, libera los recursos del objeto. Esto hace que la finalización sea innecesaria. <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> debe llamar a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> para que el recolector de elementos no utilizados no llame al finalizador del objeto.

 Para evitar que los tipos derivados con finalizadores tengan que volver a implementar [System. IDisposable] (<!-- TODO: review code entity reference <xref:assetId:///System.IDisposable?qualifyHint=True&amp;autoUpgrade=False>  -->) y para llamarlo, los tipos no sellados sin finalizadores deben seguir llamando a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla:

 Si el método es una implementación de <xref:System.IDisposable.Dispose%2A>, agregue una llamada a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

 Si el método no es una implementación de <xref:System.IDisposable.Dispose%2A>, quite la llamada a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> o muévala a la implementación de <xref:System.IDisposable.Dispose%2A> del tipo.

 Cambie todas las llamadas a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> para pasarlas (me en Visual Basic).

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Solo debe suprimir una advertencia de esta regla si va a deshacer el uso de <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> para controlar la duración de otros objetos. No suprima una advertencia de esta regla si una implementación de <xref:System.IDisposable.Dispose%2A> no llama a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>. En esta situación, si no se puede suprimir la finalización, se degrada el rendimiento y no se proporcionan ventajas.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un método que llama incorrectamente a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly.vb#1)]

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un método que llama correctamente a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2215: Los métodos Dispose deben llamar al método Dispose de la clase base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA2216: Los tipos descartables deben declarar el finalizador](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>Vea también
 [Patrón de Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
