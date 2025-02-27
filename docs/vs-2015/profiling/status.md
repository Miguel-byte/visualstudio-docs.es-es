---
title: Status | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ba656fa4-ef9d-4d8c-a3b6-739c3b5d23ae
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3f64364caf914c030fef806c5ae17e90a8368fa3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157784"
---
# <a name="status"></a>Situación
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La opción **Status** de VSPerfCmd.exe muestra información sobre el estado del generador de perfiles y los procesos de los que actualmente se está generando el perfil.  
  
 La opción **Status** debe ser la única especificada en la línea de comandos. El generador de perfiles se debe inicializar con la opción **Start** de VSPerfCmd.exe antes de que se pueda mostrar cualquier estado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
VSPerfCmd.exe /Status  
```  
  
#### <a name="parameters"></a>Parámetros  
 None  
  
## <a name="remarks"></a>Comentarios  
 La opción **Status** muestra la siguiente información de estado para el generador de perfiles.  
  
 **Nombre del archivo de salida**  
 La ruta de acceso y el nombre del archivo de datos actual del generador de perfiles.  
  
 **Modo de recopilación**  
 SAMPLE o TRACE  
  
 **Procesos máximos**  
 El número máximo de procesos de los que se puede generar perfiles al mismo tiempo y el número de procesos actualmente activos.  
  
 **Máximo de subprocesos**  
 El número máximo de subprocesos de los que se pueden generar perfiles de una vez.  
  
 **Número de búferes**  
 El número de búferes de memoria dedicados a escribir datos de generación de perfiles.  
  
 **Tamaño de búferes**  
 El tamaño de un búfer de memoria en bytes.  
  
 La opción **Status** muestra la siguiente información de estado para cada proceso del que actualmente se generan perfiles.  
  
 **Process**  
 Nombre del proceso del que se generan perfiles.  
  
 **Identificador del proceso**  
 Identificador del sistema del proceso.  
  
 **Número de subprocesos**  
 Número de subprocesos que se están ejecutando actualmente.  
  
 **Recuento de inicios y paradas**  
 El recuento del generador de perfiles interno principal para controlar la recopilación de datos para este proceso. El recuento debe ser igual a uno para recopilar los datos. El recuento de inicios y paradas se puede manipular con las API del generador de perfiles y las opciones **GlobalOn**, **GlobalOff**, **ProcessOn**, **ProcessOff**, **ThreadOn** y **ThreadOff** de VSPerfCmd.  
  
 **Recuento de suspensiones y reanudaciones**  
 El recuento del generador de perfiles interno secundario para controlar la recopilación de datos para este proceso. El número debe ser menor o igual que cero para recopilar los datos. El recuento de **suspensiones y reanudaciones** solo se puede manipular con las API del generador de perfiles.  
  
 **Usuarios con derechos de acceso al monitor**  
 Enumera los nombres de los usuarios que tienen acceso al generador de perfiles. Se puede conceder acceso a usuarios adicionales mediante la opción **Admin** de VSPerfCmd.exe  
  
## <a name="see-also"></a>Otras referencias  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles para aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Generar perfiles de servicios](../profiling/command-line-profiling-of-services.md)
