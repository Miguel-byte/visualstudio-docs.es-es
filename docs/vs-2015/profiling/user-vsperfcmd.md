---
title: User (VSPerfCmd) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ee1a478e-374d-4f30-ae28-d260b9d4723a
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 311d02ad3e15f184f8b7e21b5794d73c41a8d4fb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68145388"
---
# <a name="user-vsperfcmd"></a>User (VSPerfCmd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La opción **User** especifica el dominio y el nombre de usuario de la cuenta propietaria del proceso para el que se han generado perfiles. Esta opción solamente es necesaria si el proceso se está ejecutando como otro usuario distinto del usuario que inició sesión. El propietario del proceso se muestra en la columna Nombre de usuario de la pestaña Procesos del Administrador de tareas de Windows.  
  
 El **usuario** opción solo se puede especificar en una línea de comandos que también contenga la **iniciar** opción.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName /User:[Domain\]UserName [Options]  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Domain`  
 Nombre del dominio de usuario.  
  
 `UserName`  
 Nombre del usuario.  
  
## <a name="required-options"></a>Opciones necesarias  
 La opción **User** solo se puede usar con la opción **Start**.  
  
 **Start:** `Method`  
 Inicializa el generador de perfiles en el método de generación de perfiles especificado.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la opción **User**.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM  
```  
  
## <a name="see-also"></a>Otras referencias  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles para aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Generar perfiles de servicios](../profiling/command-line-profiling-of-services.md)
