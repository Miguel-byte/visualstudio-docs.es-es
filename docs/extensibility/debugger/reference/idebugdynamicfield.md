---
title: IDebugDynamicField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 58a4838afc0d52ab60ae0a11de419393d68dfc06
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351343"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
Esta interfaz representa un tipo de una variable.

## <a name="syntax"></a>Sintaxis

```
IDebugDynamicField : IDebugField
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Esta interfaz se implementa mediante proveedores de símbolos como una clase base para cualquier tipo que se puede determinar en tiempo de ejecución. Esto es solo para código administrado.

## <a name="notes-for-callers"></a>Notas para los llamadores
 Esta interfaz representa una clase base desde la que se pueden derivar las interfaces más especializadas.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 Esta interfaz no proporciona ningún método distinto de los heredados de `IDebugField`.

## <a name="requirements"></a>Requisitos
 Encabezado: sh.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)