---
title: Los puntos de interrupción (SDK de Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 39c13271bad984291f609ef45505549855bee99f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68146425"
---
# <a name="breakpoints-visual-studio-sdk"></a>Puntos de interrupción (Visual Studio SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Hay tres tipos de puntos de interrupción: pendientes enlazados y error.  
  
 **Un punto de interrupción:**  
  
- Es una abstracción que contiene toda la información necesaria para enlazar un punto de interrupción a uno o más contextos de código en uno o más programas. Cada vez que un programa que se está depurando código causa para cargar, el motor de depuración comprueba todos los puntos de interrupción pendientes para ver si pueden estar limitados.  
  
   Un punto de interrupción pendiente propio nunca se enlaza al código, pero en su lugar recopila y se dice que contienen todos los puntos de interrupción enlazados que genera.  
  
- Se representa mediante un [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interfaz.  
  
  **Un punto de interrupción enlazado:**  
  
- Es una abstracción para un punto de interrupción asociada o enlazada a un contexto de código único. Cada punto de interrupción enlazado se genera en respuesta a un punto de interrupción pendiente. Un punto de interrupción pendiente sin embargo, puede generar más de un punto de interrupción enlazado.  
  
   Cuando se descarga código, un punto de interrupción enlazado puede independientes y se descartan.  
  
- Se representa mediante un [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) interfaz.  
  
  **Un punto de interrupción de error:**  
  
- Es una abstracción para describir un error al intentar enlazar un punto de interrupción pendiente a un contexto de código. Un punto de interrupción de error describe un error en la ubicación o en la propia expresión de punto de interrupción. Para obtener más información, consulte [enlace puntos de interrupción](../../extensibility/debugger/binding-breakpoints.md).  
  
   El error de punto de interrupción puede ser un error o una advertencia.  
  
- Se representa mediante un [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) interfaz.  
  
## <a name="see-also"></a>Vea también  
 [Programas](../../extensibility/debugger/programs.md)   
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [Contexto de código](../../extensibility/debugger/code-context.md)   
 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
