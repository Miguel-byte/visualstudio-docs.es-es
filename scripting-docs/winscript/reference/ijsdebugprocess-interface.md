---
title: Interfaz IJsDebugProcess | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a7ad5525-55b7-4c68-a4f7-c508f7877712
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9200515b2c975fb1fa5b2acda7c261cb684d85b4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577342"
---
# <a name="ijsdebugprocess-interface"></a>IJsDebugProcess (Interfaz)
Proporciona rutinas para inspeccionar y controlar el proceso de destino.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
IJsDebugProcess : public IUnknown;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IJsDebugProcess::CreateBreakPoint (Método)](../../winscript/reference/ijsdebugprocess-createbreakpoint-method.md)|Establece el punto de interrupción en la posición del documento especificada.|  
|[IJsDebugProcess::CreateStackWalker (Método)](../../winscript/reference/ijsdebugprocess-createstackwalker-method.md)|Método de generador para el rastreador de pila.|  
|[IJsDebugProcess::PerformAsyncBreak (Método)](../../winscript/reference/ijsdebugprocess-performasyncbreak-method.md)|Pone el motor de scripts en modo de interrupción, haciendo que se detenga en la siguiente instrucción de script.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag. h  
  
## <a name="see-also"></a>Vea también  
 [Referencia de interfaces de Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)