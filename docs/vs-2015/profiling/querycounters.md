---
title: QueryCounters | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cdd2707a6af2b9d03e73c696884dc12413437b04
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68178269"
---
# <a name="querycounters"></a>QueryCounters
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La opción **QueryCounters** enumera los contadores de rendimiento de CPU (hardware) que están disponibles en el equipo.  
  
 **QueryCounters** debe ser la única opción en la línea de comandos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
VSPerfCmd.exe /QueryCounters  
```  
  
#### <a name="parameters"></a>Parámetros  
 None  
  
## <a name="remarks"></a>Comentarios  
 Cuando se utiliza el método de instrumentación, el generador de perfiles puede recopilar los valores de uno o varios contadores de rendimiento de CPU en cada evento de recopilación de datos. Cuando se utiliza el método de generación de perfiles de muestreo, puede especificar un evento de contador y el número de repeticiones del evento que se usará como el intervalo de muestreo.  
  
 Diferentes procesadores exponen distintos contadores de rendimiento de CPU. El generador de perfiles define un conjunto de contadores genéricos que se pueden utilizar en casi todos los procesadores. La opción **QueryCounters** muestra los nombres tanto de los contadores genéricos como de los contadores que son específicos del procesador.  
  
## <a name="see-also"></a>Otras referencias  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles para aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Generar perfiles de servicios](../profiling/command-line-profiling-of-services.md)
