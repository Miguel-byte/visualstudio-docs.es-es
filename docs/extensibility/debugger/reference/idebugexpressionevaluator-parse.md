---
title: IDebugExpressionEvaluator::Parse | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::Parse
helpviewer_keywords:
- IDebugExpressionEvaluator::Parse method
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b732369aa5cf5a828dfad512c643f109346abcb7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325655"
---
# <a name="idebugexpressionevaluatorparse"></a>IDebugExpressionEvaluator::Parse
Este método convierte una cadena de expresión en una expresión analizada.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Parse( 
   LPCOLESTR                upstrExpression,
   PARSEFLAGS               dwFlags,
   UINT                     nRadix,
   BSTR*                    pbstrError,
   UINT*                    pichError,
   IDebugParsedExpression** ppParsedExpression
);
```

```csharp
int Parse(
   string                     upstrExpression,
   enum_PARSEFLAGS            dwFlags,
   uint                       nRadix,
   out string                 pbstrError,
   out uint                   pichError,
   out IDebugParsedExpression ppParsedExpression
);
```

## <a name="parameters"></a>Parámetros
`upstrExpression`\
[in] La cadena de expresión que se va a analizar.

`dwFlags`\
[in] Una colección de [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) constantes que determinan cómo se puede analizar la expresión.

`nRadix`\
[in] Base que se usará para interpretar toda la información numérica.

`pbstrError`\
[out] Devuelve el error como texto legible.

`pichError`\
[out] Devuelve la posición del carácter de inicio del error en la cadena de expresión.

`ppParsedExpression`\
[out] Devuelve la expresión analizada en un [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) objeto.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Este método produce una expresión analizada, no un valor real. Una expresión analizada está lista para ser evaluada, es decir, convertir en un valor.

## <a name="see-also"></a>Vea también
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
- [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)