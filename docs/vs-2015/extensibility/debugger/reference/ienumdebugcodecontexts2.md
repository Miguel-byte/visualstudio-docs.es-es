---
title: IEnumDebugCodeContexts2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2
helpviewer_keywords:
- IEnumDebugCodeContexts2
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f36da19e6bc47d70010dd96a26256537803ccb29
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62551623"
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esta interfaz enumera los contextos de código asociados con la sesión de depuración, o con un determinado programa o documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IEnumDebugCodeContexts2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (DE) implementa esta interfaz para representar una lista de contextos de código para una posición de texto determinado en un programa o una lista de contextos de código para un contexto de documento en particular.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Llame a [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) para obtener esta interfaz que representa una lista de contextos de código para una posición de un texto específico en el documento de origen de un programa.  
  
 Llame a [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) para obtener esta interfaz que representa una lista de todos los contextos de código en un documento de origen determinado.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IEnumDebugCodeContexts2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|Recupera un número especificado de contextos de código en una secuencia de enumeración.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|Omite un número especificado de contextos de código en una secuencia de enumeración.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|Restablece una secuencia de enumeración al principio.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|Obtiene el número de contextos de código en un enumerador.|  
  
## <a name="remarks"></a>Comentarios  
 Llamadas visuales Studio [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) para rellenar una lista de contextos de código, el usuario puede elegir al establecer la instrucción siguiente o mostrar el desensamblado de un archivo de origen. Por ejemplo, varios contextos de código pueden producirse cuando hay varias instancias de una plantilla de estilo de C++.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces del núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)
