---
title: IEnumDebugPropertyInfo2 | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2
helpviewer_keywords:
- IEnumDebugPropertyInfo2
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ee305083957f6d2f2ada09aec1747497fcf6db68
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68147822"
---
# <a name="ienumdebugpropertyinfo2"></a>IEnumDebugPropertyInfo2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esta interfaz enumera [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) estructuras.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IEnumDebugPropertyInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (DE) implementa esta interfaz para representar la información para una propiedad determinada.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Llame a [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) para obtener esta interfaz que representa los elementos secundarios de una propiedad determinada. Llame a [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) para obtener esta interfaz que representa las propiedades de un marco de pila determinado.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IEnumDebugPropertyInfo2`.  
  
|Método|DESCRIPCIÓN|  
|------------|-----------------|  
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|Recupera un número especificado de [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) estructuras en una secuencia de enumeración.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|Omite un número especificado de [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) estructuras en una secuencia de enumeración.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|Restablece una secuencia de enumeración al principio.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)|Obtiene el número de [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) estructuras en un enumerador.|  
  
## <a name="remarks"></a>Comentarios  
 En general, una propiedad es una jerarquía de información que puede incluir un nombre, valor, dirección y tipo, así como cualquier otra información adecuada para el marco de pila o el objeto de propiedad asociado. Consulte [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) para obtener más detalles.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces del núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
