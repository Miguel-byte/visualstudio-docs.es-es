---
title: 'Iactivescriptsitedebug (:: GetRootApplicationNode | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.GetRootApplicationNode
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::GetRootApplicationNode
ms.assetid: 2393f566-6b97-47c0-8041-4dd7e3b1d3a3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b19ed10178d03be0b96393ad08f1eab88ce40329
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570061"
---
# <a name="iactivescriptsitedebuggetrootapplicationnode"></a>IActiveScriptSiteDebug::GetRootApplicationNode
Obtiene el nodo de aplicación bajo el que se deben agregar los documentos de script.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetRootApplicationNode(  
   IDebugApplicationNode**  ppdanRoot  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppdanRoot`  
 enuncia El nodo de la aplicación de depuración que contiene documentos de script. Puede ser `NULL`.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método devuelve el nodo de aplicación bajo el que se deben agregar los documentos de script. El método puede devolver `NULL` para `ppdanRoot` si los documentos de script deben ser de nivel superior.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptSiteDebug (Interfaz)](../../winscript/reference/iactivescriptsitedebug-interface.md)