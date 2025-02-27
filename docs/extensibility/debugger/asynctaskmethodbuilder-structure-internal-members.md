---
title: 'AsyncTaskMethodBuilder Structure: miembros internos | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3f080e7a0fef7a03b878c253f09661338b5704df
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317639"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>AsyncTaskMethodBuilder structure: miembros internos
En este tema se describe los miembros internos de la <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> clase. Para obtener información general acerca de esta clase, vea el <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> tema de referencia.

 **Espacio de nombres:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Ensamblado:** mscorlib (en mscorlib.dll)

 Dado que no se puede obtener acceso a estos miembros internos de .NET Framework, la sintaxis siguiente se proporciona el lenguaje intermedio en común (CIL).

## <a name="syntax"></a>Sintaxis

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Miembros internos

|Name|Descripción|
|----------|-----------------|
|[Propiedad ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Obtiene un objeto que puede utilizarse para identificar de forma única este generador para el depurador.|
|[campo m_builder](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Representa el objeto de generador de genérico a la que se delega esta instancia no genérica.|

## <a name="see-also"></a>Vea también
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>
- [Parámetros internos de extensiones paralelas para .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)