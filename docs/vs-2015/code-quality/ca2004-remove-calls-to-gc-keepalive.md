---
title: 'CA2004: Quite las llamadas a GC. KeepAlive | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e34a8e7d4860a599155554410e13df5a6eb3bfe1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672489"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: Quitar las llamadas a GC.KeepAlive
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|RemoveCallsToGCKeepAlive|
|Identificador de comprobación|CA2004|
|Categoría|Microsoft.Reliability|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Las clases usan `SafeHandle` pero todavía contienen llamadas a `GC.KeepAlive`.

## <a name="rule-description"></a>Descripción de la regla
 Si va a realizar la conversión a `SafeHandle` uso, quite todas las llamadas a `GC.KeepAlive` (objeto). En este caso, las clases no deben tener que llamar a `GC.KeepAlive`, suponiendo que no tienen un finalizador pero confían en `SafeHandle` para completar el identificador del sistema operativo.  Aunque el costo de dejar en una llamada a `GC.KeepAlive` puede ser insignificante según el rendimiento, la percepción de que una llamada a `GC.KeepAlive` es necesaria o suficiente para solucionar un problema de duración que puede que ya no exista, hace que el código sea más difícil de mantener.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Quite las llamadas a `GC.KeepAlive`.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Puede suprimir esta advertencia solo si no es técnicamente correcta convertir a `SafeHandle` uso en la clase.
