---
title: Procedimiento Adjuntar el Profiler a una aplicación Web ASP.NET para recopilar datos de simultaneidad mediante la línea de comandos | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 0e215fdd-55f8-43ef-9534-06542eefe223
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d720779019ab4106fa6c4b727e9994f168a2d8f2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68179282"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line"></a>Procedimiento Adjuntar al Profiler a una aplicación Web ASP.NET para recopilar datos de simultaneidad mediante la línea de comandos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tema se describe cómo utilizar las herramientas de línea de comandos de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para adjuntar el generador de perfiles a una aplicación ASP.NET y recopilar datos de simultaneidad de procesos y subprocesos.  

 Las herramientas de línea de comandos de las Herramientas de generación de perfiles se encuentran en el subdirectorio \Team Tools\Performance Tools del directorio de instalación de Visual Studio. En equipos de 64 bits, están disponibles las dos versiones de las herramientas, la de 64 bits y la de 32 bits. Para utilizar el generador de perfiles en un símbolo del sistema, debe agregar la ruta de acceso de las herramientas a la variable de entorno PATH de la ventana **Símbolo del sistema** o agregarla al propio comando. Para obtener más información, consulte [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Para recopilar datos de simultaneidad, debe asociarse el generador de perfiles al proceso de trabajo de ASP.NET que hospeda el sitio web. Mientras el generador de perfiles está adjunto a la aplicación, puede pausar y reanudar la recolección de datos. Para finalizar una sesión de generación de perfiles, el generador de perfiles no debe estar ya adjunto a la aplicación y debe apagarse explícitamente. En la mayoría de los casos, debe borrar las variables de entorno de la generación de perfiles al final de una sesión.  

## <a name="attaching-the-profiler"></a>Adjuntar el generador de perfiles  

#### <a name="to-attach-the-profiler-to-a-aspnet-application"></a>Para adjuntar el generador de perfiles a una aplicación ASP.NET  

1. Escriba el siguiente comando para iniciar el generador de perfiles:  

    [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency /output:** `OutputFile` [`Options`]  

   - La opción [/start](../profiling/start.md) inicializa el generador de perfiles para recopilar datos de contención de recursos.  

   - La opción [/output](../profiling/output.md) **:** `OutputFile` es necesaria con **/start**. `OutputFile` especifica el nombre y la ubicación del archivo de datos de generación de perfiles (.vsp).  

     Puede utilizar cualquier opción de la tabla siguiente con la opción **/start**.  

   |                               Opción                               |                                                                     DESCRIPCIÓN                                                                      |
   |--------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/user](../profiling/user-vsperfcmd.md) **:** [`Domain\`]`UserName` |                           Especifica el dominio y el nombre de usuario opcionales de la cuenta a la que se va a conceder acceso al generador de perfiles.                           |
   |           [/crosssession](../profiling/crosssession.md)            |                                               Habilita la generación de perfiles de procesos en otros inicios de sesión.                                                |
   |  [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`  |                                      Especifica un contador de rendimiento de Windows que se va a recopilar durante la generación de perfiles.                                       |
   |       [/automark](../profiling/automark.md) **:** `Interval`       | Utilizar solo con **/wincounter**. Especifica el número de milisegundos entre eventos de recopilación de contadores de rendimiento de Windows. El valor predeterminado es 500. |
   |     [/events](../profiling/events-vsperfcmd.md) **:** `Config`     |       Especifica un evento de Seguimiento de eventos para Windows (ETW) que se va a recopilar durante la generación de perfiles. Los eventos ETW se recopilan en un archivo (.etl) independiente.       |

2. Inicie la aplicación ASP.NET de la manera habitual.  

3. Escriba el siguiente comando para adjuntar el generador de perfiles al proceso de trabajo de ASP.NET: **VSPerfCmd /attach:** `PID` [ **/targetclr:** `Version`]  

   - `PID` especifica el identificador o nombre del proceso de trabajo de ASP.NET. Puede ver los identificadores de todos los procesos que se están ejecutando en el Administrador de tareas de Windows.  

   - [/targetclr](../profiling/targetclr.md) **:** `Version` especifica la versión de Common Language Runtime (CLR) para generar perfiles cuando se carga más de una versión del runtime en una aplicación. Este parámetro es opcional.  

## <a name="controlling-data-collection"></a>Controlar la recolección de datos  
 Mientras se ejecuta la aplicación, puede controlar la recolección de datos iniciando o deteniendo la escritura de los datos en el archivo con las opciones de VSPerfCmd.exe. Al controlar la recolección de datos, puede recopilar datos de una parte específica de la ejecución de un programa, como por ejemplo el inicio o el cierre de una aplicación.  

#### <a name="to-start-and-stop-data-collection"></a>Para iniciar y detener la recolección de datos  

- Los pares de opciones de VSPerfCmd de la tabla siguiente inician y detienen la recolección de datos. Especifique cada opción en una línea de comandos diferente. Puede activar y desactivar la recolección de datos varias veces.  

    |Opción|DESCRIPCIÓN|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Inicia ( **/globalon**) o detiene ( **/globaloff**) la recolección de datos para todos los procesos.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID`  [processoff](../profiling/processon-and-processoff.md) **:** `PID`|Inicia ( **/processon**) o detiene ( **/processoff**) la recolección de datos para el proceso que especifica el identificador de proceso (`PID`).|  
    |[/attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[ **:** {`PID`&#124;`ProcName`}]|**/attach** inicia la recolección de datos para el proceso especificado por el identificador de proceso (`PID`) o por el nombre de proceso (*ProcName*). **/detach** detiene la recolección de datos para el proceso especificado o para todos los procesos si no se especifica uno.|  

## <a name="ending-the-profiling-session"></a>Finalizar la sesión de generación de perfiles  
 Para finalizar la sesión de generación de perfiles, el generador de perfiles no debe estar recopilando datos. Para detener la recolección de datos de una aplicación de la que se generan el perfil con el método de simultaneidad, reinicie el proceso de trabajo de ASP.NET o invoque la opción **VSPerfCmd /detach**. Después, invoque la opción **VSPerfCmd /shutdown** para desactivar el generador de perfiles y cerrar el archivo de datos de generación de perfiles. El comando **VSPerfClrEnv /globaloff** borra las variables de entorno de generación de perfiles, pero la configuración del sistema no se restablece hasta que se reinicia el equipo.  

#### <a name="to-end-a-profiling-session"></a>Para finalizar una sesión de generación de perfiles  

1. Desasocie el generador de perfiles de la aplicación de destino cerrándolo o escribiendo lo siguiente en un símbolo del sistema:  

     **VSPerfCmd /detach**  

2. Apague el generador de perfiles escribiendo el siguiente comando en un símbolo del sistema:  

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)  

## <a name="see-also"></a>Vea también  
 [Generar perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Generación rápida de perfiles de sitio web con VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)
