---
title: Control de ejecución y evaluación de estado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bda531e94bdea07ee37eed2b0b79e6f0667ba28e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315226"
---
# <a name="execution-control-and-state-evaluation"></a>Evaluación de control y el estado de ejecución
Depurar una aplicación requiere la implementación de funcionalidades de control de ejecución como ejecutar funciones, la detención en puntos de interrupción y continuar la ejecución. Bases de depuración de Visual Studio su control de ejecución en los eventos se envía entre los componentes del depurador.

## <a name="in-this-section"></a>En esta sección
 [Control del programa](../../extensibility/debugger/program-control.md) se enumeran las rutinas siguientes que se producen en el nivel de programa: establecer la instrucción siguiente, ejecutar, ejecución paso a paso, continuar, suspender y reanudar.

 [Métodos relacionados con el punto de interrupción](../../extensibility/debugger/breakpoint-related-methods.md) define el límite y pendiente de tipos de puntos de interrupción que es compatible con Visual Studio.

 [Llame a la evaluación de la pila](../../extensibility/debugger/call-stack-evaluation.md) la implementación de los métodos que permiten la visualización de los marcos de pila de la pila de llamadas durante el modo de interrupción.

 [Evaluación de expresiones](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md) explica cómo el motor de depuración (DE), la evaluación de expresiones (EE) y el Administrador de depuración de sesión están implicados en el análisis y la evaluación de una expresión que se celebra una de las ventanas del IDE.

 [Controlar eventos](../../extensibility/debugger/control-events.md) se aborda la interfaz que se usa para enviar eventos durante la ejecución del programa controlada.