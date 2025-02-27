---
title: 'CA1821: quita los finalizadores vacíos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords:
- CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3d340d69ee32de20142abf740f7fedc871c9733a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657474"
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821: Quitar los finalizadores vacíos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|RemoveEmptyFinalizers|
|Identificador de comprobación|CA1821|
|Categoría|Microsoft. performance|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un tipo implementa un finalizador que está vacío, llama solo al finalizador de tipo base o llama únicamente a métodos emitidos condicionalmente.

## <a name="rule-description"></a>Descripción de la regla
 Siempre que pueda, evite los finalizadores debido a la sobrecarga de rendimiento adicional necesaria para el seguimiento de la duración del objeto. El recolector de elementos no utilizados ejecutará el finalizador antes de recopilar el objeto. Esto significa que se requerirán dos colecciones para recopilar el objeto. Un finalizador vacío incurrirá en esta sobrecarga adicional sin ninguna ventaja.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Quite el finalizador vacío. Si se requiere un finalizador para la depuración, incluya el finalizador completo en las directivas de `#if DEBUG / #endif`.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima un mensaje de esta regla. Un error al suprimir la finalización disminuye el rendimiento y no proporciona ninguna ventaja.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un finalizador vacío que se debe quitar, un finalizador que debe incluirse en las directivas de `#if DEBUG / #endif` y un finalizador que usa las directivas de `#if DEBUG / #endif` correctamente.

 [!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.RemoveEmptyFinalizers/cs/FxCop.Performance.RemoveEmptyFinalizers.cs#1)]
