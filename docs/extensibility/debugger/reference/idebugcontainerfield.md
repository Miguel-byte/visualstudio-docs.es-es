---
title: IDebugContainerField | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d633b7e42f8c7f64a818539694837b954ea31e72
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332511"
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
Esta interfaz representa un tipo que es un contenedor para otros tipos o los símbolos o símbolos.

## <a name="syntax"></a>Sintaxis

```
IDebugContainerField : IDebugField
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un proveedor de símbolos implementa esta interfaz en el mismo objeto que implementa el [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaz. Esta interfaz también es la clase base para todas las interfaces que representan contenedores.

## <a name="notes-for-callers"></a>Notas para los llamadores
 Muchos métodos en muchas interfaces devuelven esta interfaz. Porque se trata de una clase base para todos los contenedores, puede obtener interfaces más especializadas de esta interfaz mediante [QueryInterface](/cpp/atl/queryinterface). Estas interfaces incluyen [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md), [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md), y [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md).

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 Además de los métodos en el [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaz, esta interfaz implementa el método siguiente:

|Método|Descripción|
|------------|-----------------|
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|Crea un enumerador para los campos del contenedor.|

## <a name="remarks"></a>Comentarios
 Matrices (contenedores para las variables), (contenedores para los métodos y variables) de las clases y métodos (contenedores para los parámetros y variables locales) son ejemplos de contenedores.

## <a name="requirements"></a>Requisitos
 Encabezado: sh.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)