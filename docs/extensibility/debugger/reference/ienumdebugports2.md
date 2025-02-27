---
title: IEnumDebugPorts2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2
helpviewer_keywords:
- IEnumDebugPorts2
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c24edcd5ef47408cd4c11b3d0548ad34516702a1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326508"
---
# <a name="ienumdebugports2"></a>IEnumDebugPorts2
Esta interfaz enumera los puertos de un proveedor de puerto o de máquina.

## <a name="syntax"></a>Sintaxis

```
IEnumDebugPorts2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un proveedor de puerto personalizado implementa esta interfaz para representar una lista de los puertos creados por el proveedor. Visual Studio implementa esta interfaz para respaldar su propio proveedor del puerto.

## <a name="notes-for-callers"></a>Notas para los llamadores
 Llame a [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) para obtener esta interfaz que representa una lista de los puertos creados por el proveedor del puerto. Llame a [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) para obtener esta interfaz que representa una lista de puertos que se guardaron en el disco.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 La tabla siguiente muestran los métodos de `IEnumDebugPorts2`.

|Método|Descripción|
|------------|-----------------|
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|Recupera un número especificado de puertos en una secuencia de enumeración.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|Omite un número especificado de puertos en una secuencia de enumeración.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|Restablece una secuencia de enumeración al principio.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugports2-getcount.md)|Obtiene el número de puertos en un enumerador.|

## <a name="remarks"></a>Comentarios
 Visual Studio usa esta interfaz para rellenar una lista de puertos que se usan para asociar a procesos.

 Normalmente, un motor de depuración no utiliza esta interfaz.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)