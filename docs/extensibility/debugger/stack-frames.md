---
title: Marcos de pila | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de3a0267d366f926fa5705c7455b237cafe4820a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348510"
---
# <a name="stack-frames"></a>Marcos de pila
En la arquitectura de depurador, un *marco de pila*:

- Es una abstracción de una pila que proporciona el contexto de ejecución de un subproceso. Un subproceso siempre se ejecuta dentro de una función. Un marco de pila contiene las variables locales de la función y los argumentos a él. Para depurar con Visual Studio, el lenguaje o entorno que se está depurando debe admitir los marcos de pila.

- Puede identificar y describirse a sí mismos y puede devolver el subproceso asociado. También puede devolver un marco de pila que representa el puntero de instrucción actual y la documentación asociada al contexto del código y contextos de evaluación de expresión.

- Tiene propiedades que describen el nombre, tipo y valor de argumentos y variables locales y cuáles deben aparecer en varias ventanas de depuración IDE.

- Se representa mediante un [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interfaz, suelen ser creado por un motor de depuración (DE) o una máquina virtual como consecuencia de ejecución de un subproceso.

## <a name="see-also"></a>Vea también
- [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)
- [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)
- [Motor de depuración](../../extensibility/debugger/debug-engine.md)
- [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)