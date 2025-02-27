---
title: 'Error: El Microsoft Visual Studio Monitor de depuración remota en el equipo remoto se está ejecutando como otro usuario | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
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
- -anyuser option
- anyuser option
- Remote Debugging Monitor
- remote debugging, Remote Debugging Monitor
- msvsmon.exe
ms.assetid: e5b18734-2daf-4c58-b5de-24ae1295703e
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dffaafbca80828a7501f5f7d24e525225284f5a8
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697311"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>Error: El Monitor de depuración remota de Microsoft Visual Studio del equipo remoto se está ejecutando como usuario distinto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al intentar realizar una depuración remota, es posible recibir el siguiente mensaje de error:  
  
 El Monitor de depuración remota de Microsoft Visual Studio del equipo remoto se está ejecutando como usuario distinto.  
  
## <a name="cause"></a>Motivo  
 Este mensaje aparece cuando se lleva a cabo la depuración en modo Sin autenticación y el usuario que inició msvsmon no es el usuario que ejecuta Visual Studio.  
  
## <a name="solution"></a>Soluciones  
 La solución mejor y más segura es ejecutar el Monitor de depuración remota (msvsmon.exe) con la misma cuenta de usuario que Visual Studio. Si no es posible hacerlo, puede ejecutar el Monitor de depuración remota con otra cuenta activando la opción **Permitir que cualquier usuario depure** en el cuadro de diálogo **Opciones** del Monitor de depuración remota.  
  
> [!CAUTION]
> Si se concede permiso a otros usuarios para que se conecten, existe la posibilidad de que se conecten accidentalmente a la sesión de depuración remota equivocada. Llevar a cabo la depuración en modo **Sin autenticación** no es seguro y debe utilizarse con precaución.  
  
 Para obtener más información, consulte [iniciar el Monitor de depuración remota](https://msdn.microsoft.com/library/55b60ce7-834b-4e83-a10e-fe4248260a4c).  
  
## <a name="see-also"></a>Vea también  
 [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)
