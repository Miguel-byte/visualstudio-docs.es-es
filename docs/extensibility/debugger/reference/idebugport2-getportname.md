---
title: 'IDebugPort2:: GetPortName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortName
helpviewer_keywords:
- IDebugPort2::GetPortName
ms.assetid: 4478b3d5-aa30-4105-8d05-e3bae2f8917a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0a382a77693fc8839721c0cdd139af2dd5208c69
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727722"
---
# <a name="idebugport2getportname"></a>IDebugPort2::GetPortName
Obtiene el nombre de puerto.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetPortName( 
   BSTR* pbstrName
);
```

```csharp
int GetPortName( 
   out string pbstrName
);
```

## <a name="parameters"></a>Parámetros
`pbstrName`\
enuncia Devuelve el nombre del puerto.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)