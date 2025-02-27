---
title: 'Error: No se puede ir automáticamente al servidor | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.causality_no_server_response
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- remote debugging, notification error
ms.assetid: 9a370ccc-d358-429c-b285-9b6c0649bc68
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c8dcb8fa757f1cccf2f3aef6c2520e0c61da0b9f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65682681"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>Error: No se puede depurar paso a paso por instrucciones el servidor automáticamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El error reza como sigue:  
  
 No se puede ir al servidor automáticamente. El depurador no recibió una notificación antes de que se ejecutase el procedimiento remoto  
  
 Este error puede aparecer cuando intenta ir a un servicio Web (vea [Ejecutar paso a paso un servicio Web XML](https://msdn.microsoft.com/8e67de38-bf5f-41cc-a457-1b88ce63d764)). Puede producirse cuando [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] no se configura correctamente.  
  
 Las posibles causas son:  
  
- No se ha establecido la depuración en "true" en el archivo web.config de la aplicación [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] (vea [Modo de depuración en aplicaciones ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)).  
  
- Se instaló una versión de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] después de instalar Visual Studio. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] debe instalarse antes que Visual Studio. Use el **Panel de control**de Windows, **Programas y características** para reparar su instalación de Visual Studio.  
  
## <a name="see-also"></a>Vea también  
 [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)
