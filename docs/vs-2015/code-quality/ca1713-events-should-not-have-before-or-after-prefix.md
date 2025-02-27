---
title: 'CA1713: los eventos no deben tener el prefijo before o After | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- EventsShouldNotHaveBeforeOrAfterPrefix
- CA1713
helpviewer_keywords:
- CA1713
- EventsShouldNotHaveBeforeOrAfterPrefix
ms.assetid: 855772a4-aa9e-410b-88c1-c5fba1ca63da
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7286272e121cf5054013576c4278f787c8423d79
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669152"
---
# <a name="ca1713-events-should-not-have-before-or-after-prefix"></a>CA1713: Los eventos no deberían tener prefijos antes ni después
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|EventsShouldNotHaveBeforeOrAfterPrefix|
|Identificador de comprobación|CA1713|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 El nombre de un evento empieza por ' Before ' o ' After '.

## <a name="rule-description"></a>Descripción de la regla
 Los nombres de evento deben describir la acción que genera el evento. Para nombrar los eventos relacionados que se provocan en una secuencia específica, utilice el tiempo presente o pasado para indicar la posición relativa en la secuencia de acciones. Por ejemplo, al asignar un nombre a un par de eventos que se genera al cerrar un recurso, puede asignarle el nombre ' closing ' y ' Closed ', en lugar de ' BeforeClose ' y ' AfterClose '.

 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Quite el prefijo del nombre del evento y considere la posibilidad de cambiar el nombre para utilizar el pasador presente o pasado de un verbo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.
