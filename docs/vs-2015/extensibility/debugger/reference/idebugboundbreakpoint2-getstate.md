---
title: IDebugBoundBreakpoint2::GetState | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::GetState
helpviewer_keywords:
- GetState method
- IDebugBoundBreakpoint2::GetState method
ms.assetid: a40a8382-295e-4916-aae6-ffe3a9cd3f2d
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b2bab406e84eee11dbfe73a70975fc69bd209930
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68156218"
---
# <a name="idebugboundbreakpoint2getstate"></a>IDebugBoundBreakpoint2::GetState
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtiene el estado de este punto de interrupción enlazado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetState(   
   BP_STATE* pState  
);  
```  
  
```csharp  
int GetState(   
   out enum_BP_STATE pState  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pState`  
 [out] Devuelve un valor de la [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) enumeración que describe el estado del punto de interrupción.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra cómo implementar este método para una sencilla `CBoundBreakpoint` objeto que expone el [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md) interfaz.  
  
```  
HRESULT CBoundBreakpoint::GetState(BP_STATE* pState)    
{    
   HRESULT hr;    
  
   // Check for a valid pointer to pState and assign the local state variable.    
   if (pState)    
   {    
      *pState = m_state;    
      hr = S_OK;    
   }    
   else    
   {    
      hr = E_INVALIDARG;    
   }    
  
   return hr;    
}    
```  
  
## <a name="see-also"></a>Vea también  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
