---
title: IDebugModule2::ReloadSymbols_Deprecated | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2::ReloadSymbols
helpviewer_keywords:
- IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 635e305c0dd88d72017048da6353f813fcc46406
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323959"
---
# <a name="idebugmodule2reloadsymbolsdeprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
OBSOLETO. NO USE. Vuelve a cargar los símbolos para este módulo.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT ReloadSymbols( 
   LPCOLESTR pszUrlToSymbols,
   BSTR*     pbstrDebugMessage
);
```

```csharp
int ReloadSymbols( 
   string     pszUrlToSymbols,
   out string pbstrDebugMessage
);
```

## <a name="parameters"></a>Parámetros
`pszUrlToSymbols`\
[in] La ruta de acceso al almacén de símbolos.

`pbstrDebugMessage`\
[out] Devuelve un mensaje informativo, como un mensaje de error o estado, que se muestra a la derecha del nombre del módulo en la ventana módulos.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. Siempre debe devolver un motor de depuración `E_FAIL`.

## <a name="remarks"></a>Comentarios
 Este método ya no se admite. Implemente el [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md) método en su lugar.

## <a name="see-also"></a>Vea también
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)