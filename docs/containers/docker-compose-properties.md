---
title: Configuración de compilación de Docker Compose en las herramientas de contenedor de Visual Studio
author: ghogen
description: Información general del proceso de compilación de las herramientas de contenedor
ms.author: ghogen
ms.date: 08/12/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 2178881c6ea0e597aef5e25074e3648162d3f6e9
ms.sourcegitcommit: 6ae0a289f1654dec63b412bfa22035511a2ef5ad
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71950639"
---
# <a name="docker-compose-build-properties"></a>Propiedades de compilación de Docker Compose

Además de las propiedades que controlan los proyectos individuales de Docker, descritas en [Propiedades de compilación de las herramientas de contenedor](container-msbuild-properties.md), también puede personalizar el modo en que Visual Studio compila los proyectos de Docker Compose si configura las propiedades de Docker Compose que MSBuild usa para compilar la solución. También puede controlar el modo en que el depurador de Visual Studio ejecuta las aplicaciones de Docker Compose estableciendo etiquetas de archivo en los archivos de configuración de Docker Compose.

## <a name="how-to-set-the-msbuild-properties"></a>Cómo establecer las propiedades de MSBuild

Para establecer el valor de una propiedad, edite el archivo del proyecto. En el caso de las propiedades de Docker Compose, este archivo del proyecto es el que tiene una extensión .dcproj, a menos que se indique lo contrario en la tabla de la sección siguiente. Por ejemplo, supongamos que desea especificar que se inicie el explorador al iniciar la depuración. Puede establecer la propiedad `DockerLaunchAction` en el archivo del proyecto .dcproj como se indica a continuación.

```xml
<PropertyGroup>
   <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
</PropertyGroup>
```

Puede agregar el valor de la propiedad a un elemento `PropertyGroup` existente o, si no hay ninguno, crear un nuevo elemento `PropertyGroup`.

## <a name="docker-compose-msbuild-properties"></a>Propiedades de MSBuild de Docker Compose

En la tabla siguiente se muestran las propiedades de MSBuild disponibles para proyectos de Docker Compose.

| Nombre de la propiedad | Ubicación | DESCRIPCIÓN | Valor predeterminado  |
|---------------|----------|-------------|----------------|
|DockerComposeBuildArguments|dcproj|Especifica los parámetros adicionales que se van a pasar al comando `docker-compose build`. Por ejemplo, `--parallel --pull`. |
|DockerComposeDownArguments|dcproj|Especifica los parámetros adicionales que se van a pasar al comando `docker-compose down`. Por ejemplo, `--timeout 500`.|-|  
|DockerComposeProjectPath|csproj o vbproj|La ruta de acceso relativa al archivo del proyecto docker-compose (dcproj). Establezca esta propiedad al publicar el proyecto de servicio para buscar la configuración de compilación de la imagen asociada que se almacena en el archivo docker-compose.yml.|-|
|DockerComposeUpArguments|dcproj|Especifica los parámetros adicionales que se van a pasar al comando `docker-compose up`. Por ejemplo, `--timeout 500`.|-|
|DockerLaunchAction| dcproj | Especifica la acción de inicio que se va a realizar en F5 o Ctrl+F5.  Los valores permitidos son None, LaunchBrowser y LaunchWCFTestClient|None|
|DockerLaunchBrowser| dcproj | Indica si se va a iniciar el explorador. Se omite si se especifica DockerLaunchAction. | False |
|DockerServiceName| dcproj|Si se especifican DockerLaunchAction o DockerLaunchBrowser, DockerServiceName es el nombre del servicio que se debe iniciar.  Use esta propiedad para determinar cuál de los varios proyectos a los que potencialmente puede hacer referencia un archivo docker-compose se iniciará.|-|
|DockerServiceUrl| dcproj | Esta dirección URL se usa al iniciar el explorador.  Los tokens de reemplazo válidos son "{ServiceIPAddress}", "{ServicePort}" y "{Scheme}".  Por ejemplo: {Scheme}://{ServiceIPAddress}:{ServicePort}|-|
|DockerTargetOS| dcproj | El sistema operativo de destino que se usa al compilar la imagen de Docker.|-|

> [!NOTE]
> DockerComposeBuildArguments, DockerComposeDownArguments y DockerComposeUpArguments son nuevos en Visual Studio 2019 versión 16.3.

## <a name="docker-compose-file-labels"></a>Etiquetas de archivo de Docker Compose

También puede invalidar ciertas opciones de configuración si coloca un archivo denominado *docker-compose.vs.debug.yml* (para la configuración **Debug**) o *docker-compose.vs.release.yml* (para la configuración **Release**) en el mismo directorio que su archivo *docker-compose.yml*.  En este archivo, puede especificar la configuración de la siguiente manera:

```yml
services:
  webapplication1:
    labels:
      com.microsoft.visualstudio.debuggee.workingdirectory: "C:\\my_app_folder"
```

Use comillas dobles alrededor de los valores, como en el ejemplo anterior, y use la barra diagonal inversa como carácter de escape para las barras diagonales inversas en las rutas de acceso.

|Un nombre de etiqueta|DESCRIPCIÓN|
|----------|-----------|
|com.microsoft.visualstudio.debuggee.arguments|Los argumentos que se pasan al programa al iniciar la depuración. En el caso de las aplicaciones de .NET Core, estos argumentos normalmente son rutas de búsqueda adicionales para los paquetes NuGet, seguidas de la ruta de acceso al ensamblado de salida del proyecto.|
|com.microsoft.visualstudio.debuggee.killprogram|Este comando se usa para detener el programa de depurado que se ejecuta dentro del contenedor (si es necesario).|
|com.microsoft.visualstudio.debuggee.program|El programa que se inicia al iniciar la depuración. En el caso de las aplicaciones de .NET Core, este valor suele ser **dotnet**.|
|com.microsoft.visualstudio.debuggee.workingdirectory|El directorio que se usa como directorio de inicio al iniciar la depuración. Este valor suele ser */app* para los contenedores de Linux o *C:\app* para los contenedores de Windows.|

## <a name="next-steps"></a>Pasos siguientes

Para obtener información sobre las propiedades de MSBuild en general, vea [Propiedades de MSBuild](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Vea también

[Propiedades de compilación de las herramientas de contenedor](container-msbuild-properties.md)

[Configuración de inicio de las herramientas de contenedor](container-launch-settings.md)

[Propiedades reservadas y conocidas de MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
