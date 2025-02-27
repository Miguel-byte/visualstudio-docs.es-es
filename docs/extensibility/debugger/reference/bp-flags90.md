---
title: BP_FLAGS90 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5c423b8ecf0e4591913be5ef875057a947f42614
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319154"
---
# <a name="bpflags90"></a>BP_FLAGS90
Enumera los valores válidos para las marcas opcionales. Las marcas opcionales pueden utilizarse para especificar información adicional al establecer un punto de interrupción. Esta enumeración se extiende el [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) enumeración.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_BP_FLAGS90
{
    // VS 8.0 values
    BP90_FLAG_NONE               = 0x0000,
    BP90_FLAG_MAP_DOCPOSITION    = 0x0001,
    BP90_FLAG_DONT_STOP          = 0x0002,

    // Values added in VS 9.0
    BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,
};
typedef DWORD BP_FLAGS90;
```

```csharp
public enum enum_BP_FLAGS90
{
    // VS 8.0 values
    BP90_FLAG_NONE                = 0x0000,
    BP90_FLAG_MAP_DOCPOSITION     = 0x0001,
    BP90_FLAG_DONT_STOP           = 0x0002,

    // Values added in VS 9.0
    BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,
};
```

## <a name="fields"></a>Campos
`BP90_FLAG_NONE`\
No especifica ninguna marca de punto de interrupción.

`BP90_FLAG_MAP_DOCPOSITION`\
Especifica que el motor de depuración (DE) debe asignar el punto de interrupción mediante el uso de la posición del documento. Esto solo es aplicable a puntos de interrupción establecidos en archivos de origen orientado a secuencias de comandos, como las páginas Active Server (ASP).

`BP90_FLAG_DONT_STOP`\
Especifica que el punto de interrupción debe procesarse por el motor de depuración, pero que el motor de depuración en última instancia, no debería detener es decir, un [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) no se debe enviar el objeto de evento. Esta marca está diseñada para su uso principalmente con puntos de seguimiento.

`BP90_FLAG_TRACEPOINT_CONTINUE`\
Usa el motor de depuración nativo para determinar si se debe borrar el estado de ejecución paso a paso. Difiere BP90_FLAG_DONT_STOP porque BP90_FLAG_DONT_STOP no se establece si el punto de seguimiento ejecuta una macro.

## <a name="requirements"></a>Requisitos
Encabezado: Msdbg90.h

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
