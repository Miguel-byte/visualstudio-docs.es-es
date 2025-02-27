---
title: METADATA_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3d608e4e9bf9987eb1dd430a9e22660c1da6a90a
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2019
ms.locfileid: "66746697"
---
# <a name="metadatatype"></a>METADATA_TYPE
Esta estructura especifica información sobre un tipo de campo que se toman de los metadatos.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct _tagTYPE_METADATA {
   ULONG32  ulAppDomainID;
   GUID     guidModule;
   _mdToken tokClass;
} METADATA_TYPE;
```

```csharp
public struct METADATA_TYPE {
   public uint ulAppDomainID;
   public Guid guidModule;
   public int  tokClass;
};
```

## <a name="parameters"></a>Parámetros
 `ulAppDomainID`\
 Identificador de la aplicación del que procede el símbolo. Esto se utiliza para identificar de forma exclusiva una instancia de la aplicación.

 `guidModule`\
 El GUID del módulo que contiene este campo.

 `tokClass`\
 El identificador de token de metadatos de este tipo.

 [C++] `_mdToken` es un `typedef` para 32 bits `int`.

## <a name="remarks"></a>Comentarios
 Esta estructura aparece como parte de la unión en el [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) estructura cuando la `dwKind` campo de la `TYPE_INFO` estructura está establecida en `TYPE_KIND_METADATA` (un valor de la [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) enumeración).

 El `tokClass` valor es un token de metadatos que identifica un tipo. Para obtener más información sobre cómo interpretar los bits superiores del identificador del token de metadatos, vea el `CorTokenType` enumeración en el archivo corhdr.h en .NET Framework SDK.

## <a name="requirements"></a>Requisitos
 Encabezado: sh.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)