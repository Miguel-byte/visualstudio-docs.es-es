---
title: IDebugPortSupplier3::EnumPersistedPorts | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
helpviewer_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
ms.assetid: 1c3dead3-5d6c-4067-8418-4015f0b0dd07
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 269a49a21fdf2c42c716fba1ab3c8cb293e15a1a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340037"
---
# <a name="idebugportsupplier3enumpersistedports"></a>IDebugPortSupplier3::EnumPersistedPorts
Este método recupera un objeto que permite la enumeración de la lista de puertos persistentes.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT EnumPersistedPorts(
   BSTR_ARRAY         PortNames,
   IEnumDebugPorts2** ppEnum
);
```

```csharp
int EnumPersistedPorts(
   BSTR_ARRAY           PortNames,
   out IEnumDebugPorts2 ppEnum
);
```

## <a name="parameters"></a>Parámetros
`PortNames`\
[in] Un [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) estructura que contiene una lista de nombres de puerto para buscar y devolver entre los puertos persistentes. Se devolverá solo aquellos puertos persistentes con estos nombres.

`ppEnum`\
[out] Un objeto que implementa el [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) interfaz.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Puertos persistentes se cargan cuando se crea una instancia de un proveedor de puerto y guardar cuando se destruye el proveedor del puerto.

## <a name="see-also"></a>Vea también
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)