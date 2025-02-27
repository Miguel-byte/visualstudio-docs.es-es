---
title: 'DA0012: Cantidad considerable de reflexión | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAReflection
- vs.performance.12
- vs.performance.rules.DA0012
- vs.performance.DA0011
ms.assetid: c92a1d76-21fa-426e-8b1b-a3c08e9bcbca
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6257ce96e139e173fca804221b495f7467fc6b20
ms.sourcegitcommit: bb5425b9c6d8fd7135d9584c2963831754071347
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/29/2019
ms.locfileid: "73024653"
---
# <a name="da0012-significant-amount-of-reflection"></a>DA0012: Cantidad considerable de reflexión

|||
|-|-|
|Identificador de regla|DA0012|
|Categoría|Uso de .NET Framework|
|Métodos de generación de perfiles|Muestreo|
|Mensaje|Quizá está usando reflexión en exceso. Se trata de una operación que utiliza muchos recursos.|
|Tipo de regla|Advertencia|

## <a name="cause"></a>Motivo
 Las llamadas a métodos System.Reflection, como InvokeMember y GetMember, o a métodos Type, como MemberInvoke, constituyen una proporción considerable de los datos de generación de perfiles. Cuando sea posible, considere la posibilidad de reemplazar estos métodos con enlace anticipado a los métodos de ensamblados dependientes.

## <a name="rule-description"></a>Descripción de la regla
 La reflexión es una herramienta flexible de .NET Framework que puede utilizar para realizar el enlace tardío de la aplicación a un ensamblado de run-time dependiente o para crear y ejecutar dinámicamente nuevos tipos durante el run-time. Sin embargo, estas técnicas pueden disminuir el rendimiento si se utilizan con frecuencia o se llaman en bucles de pequeñas dimensiones.

 Para obtener más información, consulte la sección [Reflexión y enlace tardío](/previous-versions/msp-n-p/ff647790(v=pandp.10)#reflection-and-late-binding) de Capítulo 5: Mejorar el rendimiento de código administrado en el volumen Mejorar el rendimiento y la escalabilidad de las aplicaciones .NET de la biblioteca Patrones y prácticas de Microsoft de MSDN.

## <a name="how-to-investigate-a-warning"></a>Cómo investigar una advertencia
 Haga doble clic en el mensaje en la ventana Lista de errores para navegar a la [vista Detalles de la función](../profiling/function-details-view.md) de los datos de generación de perfiles. Examine las funciones de llamada del método System.Type o System.Reflection para encontrar las secciones del programa que hacen un uso más frecuente de las API de reflexión de .NET. Evite usar métodos que devuelvan metadatos. Cuando el rendimiento de su aplicación es crítico, debe evitar el uso de enlace tardío y la creación dinámica de tipos en run-time.