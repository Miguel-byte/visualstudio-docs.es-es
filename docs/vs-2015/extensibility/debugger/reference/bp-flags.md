---
title: BP_FLAGS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_FLAGS
helpviewer_keywords:
- BP_FLAGS enumeration
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7238f41e1971437caaaf3f5aa0c6939c47e27e55
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68153519"
---
# <a name="bpflags"></a>BP_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Proporciona marcas opcionales que pueden utilizarse para especificar información adicional al establecer un punto de interrupción.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
enum enum_BP_FLAGS {   
   BP_FLAG_NONE            = 0x0000,  
   BP_FLAG_MAP_DOCPOSITION = 0x0001,  
   BP_FLAG_DONT_STOP       = 0x0002  
};  
typedef DWORD BP_FLAGS;  
```  
  
```csharp  
public enum enum_BP_FLAGS {   
   BP_FLAG_NONE            = 0x0000,  
   BP_FLAG_MAP_DOCPOSITION = 0x0001,  
   BP_FLAG_DONT_STOP       = 0x0002  
};  
```  
  
## <a name="members"></a>Miembros  
 BP_FLAG_NONE  
 No especifica ninguna marca de punto de interrupción.  
  
 BP_FLAG_MAP_DOCPOSITION  
 Especifica que el motor de depuración (DE) debe asignar el punto de interrupción con la posición del documento. Esto solo es aplicable a puntos de interrupción establecidos en archivos de origen orientado a secuencias de comandos, como las páginas Active Server (ASP).  
  
 BP_FLAG_DONT_STOP  
 Especifica que el punto de interrupción debe procesarse por el motor de depuración, pero que el motor de depuración en última instancia, no debería detener allí (es decir, un [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) no se debe enviar el objeto de evento). Esta marca está diseñada para su uso principalmente con puntos de seguimiento.  
  
## <a name="remarks"></a>Comentarios  
 Utilizado para la `dwFlags` miembro de la [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) y [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) estructuras.  
  
 Estos valores se pueden combinar con un bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
