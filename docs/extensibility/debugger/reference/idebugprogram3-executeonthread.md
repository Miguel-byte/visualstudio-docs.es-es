---
title: IDebugProgram3::ExecuteOnThread | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 798a0caca394a21d6ee12a99efeacb2f27f6969c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343604"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
Ejecuta el programa de depurador. El subproceso se devuelve para proporcionar la información del depurador en el subproceso que el usuario está viendo cuando se ejecuta el programa.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT ExecuteOnThread(
   [in] IDebugThread2* pThread)
```

```csharp
int ExecuteOnThread(
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>Parámetros
`pThread`\
[in] Un [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Hay tres maneras diferentes que puede reanudar la ejecución después de detener un depurador:

- Ejecute: Cancelar cualquier paso anterior y ejecutar hasta el siguiente punto de interrupción y así sucesivamente.

- Paso: Cancelar cualquier paso anterior y ejecutar hasta que se complete el paso nuevo.

- Continuar: Ejecute de nuevo y dejar activa cualquier paso anterior.

  El subproceso pasa a `ExecuteOnThread` es útil al decidir qué paso para cancelar. Si no conoce el subproceso, que se ejecuta ejecutar cancela todos los pasos. Con el conocimiento del subproceso, solo deberá cancelar el paso en el subproceso activo.

## <a name="see-also"></a>Vea también
- [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)
- [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)