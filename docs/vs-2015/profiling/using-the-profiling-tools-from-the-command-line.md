---
title: Usar las herramientas de generación de perfiles desde la línea de comandos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- command line, performance tools
- command-line tools, performance tools
- profiling tools,command line
- tools, command-line
- command line, tools
ms.assetid: 6593fa82-181e-4009-a0ed-02aa24c2c063
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ebd0fbabb73d4c77d1d888b207882e7403f46aab
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431619"
---
# <a name="using-the-profiling-tools-from-the-command-line"></a>Usar las herramientas de generación de perfiles desde la línea de comandos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede utilizar las herramientas de línea de comandos de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para generar perfiles de aplicaciones en el símbolo del sistema y automatizar la generación de perfiles mediante archivos por lotes y scripting. También puede generar archivos de informe en un símbolo del sistema. Puede utilizar el generador de perfiles independiente ligero para recopilar datos en los equipos que no tienen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] instalado.  
  
> [!NOTE]
> Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas. Las aplicaciones de la Tienda Windows también requieren nuevas técnicas de recolección. Consulte [Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Tareas comunes  
  
|Tarea|Contenido relacionado|  
|----------|---------------------|  
|**Establecer la ubicación de los símbolos:** Para mostrar los nombres de funciones y parámetros, el generador de perfiles debe tener acceso a los archivos de símbolos (.pdb) de los archivos binarios perfilados. Estos archivos deben incluir los archivos de símbolos para el sistema operativo de Microsoft y las aplicaciones que desea ver en el análisis. Puede usar el servidor de símbolos público de Microsoft para asegurarse de que tiene los archivos .pdb correctos para los binarios de Microsoft.|-   [Cómo: Especificación de ubicaciones de archivos de símbolos desde la línea de comandos](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md)|  
|**Perfil de la aplicación:** Las herramientas de línea de comandos y opciones que usa para generar perfiles de una aplicación de destino dependen del tipo de aplicación, del método de generación de perfiles y de si el destino es una aplicación administrada o nativa.|-   [Usar los métodos de generación de perfiles desde la línea de comandos](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)<br />-   [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)<br />-   [Generar perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)<br />-   [Generar perfiles para servicios](../profiling/command-line-profiling-of-services.md)|  
|**Crear informes .xml y. csv:** La generación de perfiles en el símbolo del sistema crea archivos de datos que se pueden ver en la interfaz de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. También puede generar archivos de valores separados por comas (.csv) o .xml de los datos mediante la herramienta de línea de comandos VSPerfReport.|-   [Crear informes del generador de perfiles desde la línea de comandos](../profiling/creating-profiler-reports-from-the-command-line.md)<br />-   [VSPerfReport](../profiling/vsperfreport.md)|  
|**Generar perfiles de código en equipos sin Visual Studio:** Puede usar el generador de perfiles independiente de las Herramientas de generación de perfiles para recopilar datos de aplicaciones en equipos que no tienen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] instalado.|-   [Cómo: Instalación del generador de perfiles independiente](../profiling/how-to-install-the-stand-alone-profiler.md)|  
  
## <a name="reference"></a>Referencia  
 [Referencia de las herramientas de generación de perfiles de la línea de comandos](../profiling/command-line-profiling-tools-reference.md)  
  
## <a name="see-also"></a>Vea también  
 [Explorador de rendimiento](../profiling/performance-explorer.md)
