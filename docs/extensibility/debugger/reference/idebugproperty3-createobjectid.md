---
title: IDebugProperty3::CreateObjectID | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ee1d2a66a5ed655c132526c5d73b6673a680c971
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66339856"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
Crea un identificador único para esta propiedad para asegurarse de que es único entre todas las demás propiedades.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT CreateObjectID(
   void
);
```

```csharp
int CreateObjectID();
```

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Este método se llama cuando el Administrador de sesión de depuración desea asegurarse de que esta propiedad se identifica entre todas las demás propiedades. El motor de depuración (DE) es compatible con este método, a menos que ya de forma exclusiva se identifican las propiedades que se ocupa. Si la DE no admite este método, devuelve `E_NOTIMPL`.

 Cualquier identificador creado con `CreateObjectID` se destruye cuando la [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) se llama al método; Esto también señala el final de la necesidad de forma única que identifica esta propiedad.

> [!NOTE]
> No hay ningún método para recuperar este identificador único, por lo que puede hacer la DE cualquier valor para los identificadores únicos cuando la `CreateObjectID` se llama al método.

## <a name="see-also"></a>Vea también
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)