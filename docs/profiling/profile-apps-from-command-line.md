---
title: Medir el uso de CPU desde la línea de comandos
description: Mida el rendimiento de la CPU de la aplicación desde la línea de comandos.
ms.custom: ''
ms.date: 02/19/2019
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, command-line
- Diagnostics Tools, command-line
- CPU Usage, command-line
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 87bf0c236f34e753866ea114dfc7f45e8f16a979
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62972426"
---
# <a name="measure-application-performance-from-the-command-line"></a>Medir el rendimiento de la aplicación desde la línea de comandos

Puede recopilar información de rendimiento sobre una aplicación mediante herramientas de línea de comandos.

En el ejemplo descrito en este artículo, se recopila información de rendimiento de Bloc de notas, aunque puede usarse el mismo método para generar perfiles de cualquier proceso.

## <a name="prerequisites"></a>Requisitos previos

* Visual Studio 2019 Preview 3 o versiones posteriores

* Familiaridad con las herramientas de línea de comandos

## <a name="collect-performance-data"></a>Recopilar datos de rendimiento

La generación de perfiles mediante las herramientas de la CLI de diagnósticos de Visual Studio funciona al asociar la herramienta de generación de perfiles, junto con uno de los agentes recopiladores, a un proceso. Al asociar la herramienta de generación de perfiles, se inicia una sesión de diagnóstico que captura y almacena datos de generación de perfiles hasta que se detiene la herramienta, momento en que esos datos se exportan a un archivo *diagsession*. Luego se puede abrir este archivo en Visual Studio para analizar los resultados.

1. Inicie Bloc de notas y luego abra el Administrador de tareas para obtener su identificador de proceso (PID). En el Administrador de tareas, busque el PID en la pestaña **Detalles**.

1. Abra un símbolo del sistema y cambie al directorio con el ejecutable del agente recopilador, normalmente aquí.

   ```<Visual Studio installation folder>\2019\Preview\Team Tools\DiagnosticsHub\Collector\```

1. Inicie *VSDiagnostics.exe* al escribir el siguiente comando.

   ```cmd
   VSDiagnostics.exe start <id> /attach:<pid> /loadConfig:<configFile>
   ```

   Los argumentos que se deben incluir son:

   * \<*id*> Identifica la sesión de recopilación. El identificador debe ser un número entre 1 y 255.
   * \<*pid*> PID del proceso cuyo perfil se quiere generar, en este caso el PID del paso 1.
   * \<*configFile*> Archivo de configuración del agente recopilador que quiere iniciar. Para obtener más información, vea [Archivos de configuración de agentes](#config_file).

1. Cambie el tamaño de Bloc de notas o escriba algo en él con el fin de asegurarse de que se recopile alguna información interesante de generación de perfiles.

1. Detenga la sesión de recopilación y envíe la salida a un archivo al escribir el comando siguiente.

   ```cmd
   VSDiagnostics.exe stop <id> /output:<path to file>
   ```

1. Vaya a la salida del archivo desde el comando anterior y ábrala en Visual Studio para examinar la información recopilada.

## <a name="config_file"></a> Archivos de configuración de agentes

Los agentes recopiladores son componentes intercambiables que recopilan diferentes tipos de datos en función de lo que se intente medir.

Por comodidad, puede almacenar esa información en un archivo de configuración de agente. El archivo de configuración es un archivo *.json* que contiene como mínimo el nombre de la *.dll* y su CLSID COM. Estos son los archivos de configuración de ejemplo que se pueden encontrar en la siguiente carpeta:

```<Visual Studio installation folder>\2019\Preview\Team Tools\DiagnosticsHub\Collector\AgentConfigs\```

* Configuraciones de CpuUsage (Base/Alta/Baja), que corresponden a los datos recopilados de la herramienta de generación de perfiles [Uso de CPU](../profiling/cpu-usage.md).
* Configuraciones de DotNetObjectAlloc (Base/Baja), que corresponden a los datos recopilados de la [herramienta de asignación de objetos .NET](https://devblogs.microsoft.com/visualstudio/visual-studio-2017-version-15-8-preview-3/#tooling).

Las configuraciones Base/Baja/Alta hacen referencia a la velocidad de muestreo. Por ejemplo, Baja es 100 muestras por segundo y Alta es 4000 muestras por segundo.

Para que la herramienta *VSDiagnostics.exe* funcione con un agente recopilador, requiere un archivo DLL y un CLSID COM para el agente adecuado; además, el agente podría tener opciones de configuración adicionales. Si usa a un agente sin un archivo de configuración, use el formato del siguiente comando.

```cmd
VSDiagnostics.exe start <id> /attach:<pid> /loadAgent:<agentCLSID>;<agentName>[;<config>]
```

## <a name="permissions"></a>Permisos

Para generar el perfil de una aplicación que requiera permisos elevados, debe hacerlo desde un símbolo del sistema con privilegios elevados.
