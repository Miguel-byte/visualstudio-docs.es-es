---
title: IDebugPendingBreakpoint2::EnumBoundBreakpoints | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::EnumBoundBreakpoints
helpviewer_keywords:
- EnumBoundBreakpoints method
- IDebugPendingBreakpoint2::EnumBoundBreakpoints method
ms.assetid: 179c7c54-8446-462d-b099-e0f9cf06dc52
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ccbd3e3d54382550201771ecc8f9fbad3bca849d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68194480"
---
# <a name="idebugpendingbreakpoint2enumboundbreakpoints"></a>IDebugPendingBreakpoint2::EnumBoundBreakpoints
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Enumera todos los puntos de interrupción enlazados desde este punto de interrupción pendiente.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT EnumBoundBreakpoints(   
   IEnumDebugBoundBreakpoints2** ppEnum  
);  
```  
  
```csharp  
int EnumBoundBreakpoints(   
   out IEnumDebugBoundBreakpoints2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppEnum`  
 [out] Devuelve un [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) objeto que enumera los puntos de interrupción enlazados.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. Devuelve `E_BP_DELETED` si se ha eliminado el punto de interrupción.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra cómo implementar este método para una sencilla `CPendingBreakpoint` objeto que expone el [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interfaz.  
  
```cpp#  
HRESULT CPendingBreakpoint::EnumBoundBreakpoints(IEnumDebugBoundBreakpoints2** ppEnum)    
{    
   HRESULT hr;    
  
   // Verify that the passed IEnumDebugBoundBreakpoints2 interface pointer   
   // is valid.    
   if (ppEnum)    
   {    
      *ppEnum = NULL;  
  
      // Verify that the pending breakpoint has not been deleted. If   
      // deleted, then return hr = E_BP_DELETED.    
      if (m_state.state != PBPS_DELETED)    
      {    
         // If the bound breakpoint member variable is valid.  
         if (m_pBoundBP)    
         {    
            // Get the bound breakpoint.    
            CComPtr<IDebugBoundBreakpoint2> spBoundBP;    
            hr = m_pBoundBP->QueryInterface(&spBoundBP);    
            assert(hr == S_OK);    
            if (hr == S_OK)    
            {    
               // Create the bound breakpoint enumerator.    
               CComObject<CEnumDebugBoundBreakpoints>* pBoundEnum;    
               hr = CComObject<CEnumDebugBoundBreakpoints>::CreateInstance(&pBoundEnum);    
               assert(hr == S_OK);    
               if (hr == S_OK)    
               {    
                  // Initialize the enumerator of bound breakpoints with   
                  // the IDebugBoundBreakpoint2 information.      
                  IDebugBoundBreakpoint2* rgBoundBP[] = { spBoundBP.p };    
                  hr = pBoundEnum->Init(rgBoundBP, &(rgBoundBP[1]), NULL, AtlFlagCopy);    
                  if (hr == S_OK)    
                  {    
                     // Verify that the passed IEnumDebugBoundBreakpoints2     
                     // interface can be queried by the created  
                     // CEnumDebugBoundBreakpoints object.    
                     hr = pBoundEnum->QueryInterface(ppEnum);    
                     assert(hr == S_OK);    
                  }    
  
                  // Otherwise, delete the CEnumDebugBoundBreakpoints object.    
                  if (FAILED(hr))    
                  {    
                     delete pBoundEnum;    
                  }    
               }    
            }    
         }    
         else    
         {    
            hr = S_FALSE;    
         }    
      }    
      else    
      {    
         hr = E_BP_DELETED;    
      }    
   }    
   else    
   {    
      hr = E_INVALIDARG;    
   }    
  
   return hr;    
}    
```  
  
## <a name="see-also"></a>Vea también  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)
