---
title: Habilitación de un programa que se desea depurar | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b939b692e4e93243f5f346fcd2fcb2872e989615
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341644"
---
# <a name="enable-a-program-to-be-debugged"></a>Habilitar un programa que se desea depurar
Antes de que el motor de depuración (DE) puede depurar un programa, primero debe iniciar la DE o adjuntarlo a un programa existente.

## <a name="in-this-section"></a>En esta sección
 [Obtener un puerto](../../extensibility/debugger/getting-a-port.md) se explica cómo obtener un puerto como el primer paso para habilitar un programa que se desea depurar.

 [Registrar el programa](../../extensibility/debugger/registering-the-program.md) explica el paso siguiente para habilitar un programa que se desea depurar: registrarlo con el puerto. Una vez registrado, se puede depurar el programa mediante el proceso de adjuntar o depuración just-in-time (JIT).

 [Adjunte al programa](../../extensibility/debugger/attaching-to-the-program.md) explica el siguiente paso: asociar el depurador al programa.

 [Basado en Inicio asociar](../../extensibility/debugger/launch-based-attachment.md) describe basado en el lanzamiento de los datos adjuntos a un programa, que es automático al iniciarse por el SDM.

 [Enviar los eventos necesarios](../../extensibility/debugger/sending-the-required-events.md) le guiará por los eventos necesarios al crear un motor de depuración (DE) y conectarlo a un programa.

## <a name="related-sections"></a>Secciones relacionadas
 [Creación de un motor de depuración](../../extensibility/debugger/creating-a-custom-debug-engine.md) define un motor de depuración (DE) y se describen los servicios implementados a través de las interfaces DE y cómo pueden provocar el depurador en la transición entre distintos modos de funcionamiento.