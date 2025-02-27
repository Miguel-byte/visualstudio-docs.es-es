---
title: Introducción a extensibilidad del depurador | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 99e2dabf18d3d00034d65a94c41f2e435ad64114
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350015"
---
# <a name="get-started-with-debugger-extensibility"></a>Empezar a trabajar con la extensibilidad del depurador
El [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] proporciona la información que necesita para crear y personalizar los componentes del depurador para depurar programas desde el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuración ha agregado mejoras que se deriva de la facilidad de uso extenso las pruebas realizadas en anteriores [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuradores. Puede usar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuración paso a través de una aplicación de varios idioma, o puede implementar en marcha de edición de las variables durante la depuración de aplicaciones y soluciones de varios idiomas.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la depuración es ejecutada fuera de proceso con el programa que se está depurando y, por tanto, es menos intrusiva en el espacio de proceso de la aplicación. Por lo tanto, es más fácil escribir componentes que interactúan con el depurador sin que afecte a su programa de depuración.

 Mejor forma de usar el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], debe estar familiarizado con los siguientes elementos:

- El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado (IDE)

- El lenguaje de programación de C++

- ATL COM

## <a name="in-this-section"></a>En esta sección
 [Guía básica para ampliar el depurador](../../extensibility/debugger/roadmap-for-extending-the-debugger.md) describe el proceso de implementación de depuración en su producto, según el compilador y su salida.

 [Componentes del depurador](../../extensibility/debugger/debugger-components.md) proporciona información general sobre el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depurar componentes, que se incluyen el motor de depuración (DE), el evaluador de expresiones (EE) y el controlador de símbolos (SH).

 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md) describe los principales conceptos de arquitectura de depuración.

 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md) explica cómo el motor de depuración (DE) funciona simultáneamente dentro de los contextos de evaluación de expresión, documentación y código. Se describen para cada uno de los tres contextos, la ubicación, posición o evaluación pertinente a él.

 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md) contiene vínculos a diversas tareas de depuración, como iniciar un programa y evaluar expresiones.