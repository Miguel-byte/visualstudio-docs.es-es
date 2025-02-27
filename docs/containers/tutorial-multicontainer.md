---
title: Tutorial sobre aplicaciones de varios contenedores con Docker Compose y ASP.NET Core
author: ghogen
description: Aprenda a usar varios contenedores con Docker Compose
ms.author: ghogen
ms.date: 02/21/2019
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: ce6e98e2d068cd569247c4c4ea869c4280101d47
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2019
ms.locfileid: "71126092"
---
# <a name="tutorial-create-a-multi-container-app-with-docker-compose"></a>Tutorial: Creación de una aplicación de varios contenedores con Docker Compose

En este tutorial se aprende a administrar más de un contenedor y a comunicarse entre ellos mediante las herramientas de contenedor de Visual Studio.  La administración de varios contenedores requiere *orquestación de contenedor* y un orquestador como Docker Compose, Kubernetes o Service Fabric. Aquí se va a usar Docker Compose. Docker Compose es ideal para las pruebas y la depuración locales durante el ciclo de desarrollo.

## <a name="prerequisites"></a>Requisitos previos

::: moniker range="vs-2017"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) con las cargas de trabajo **Desarrollo web**, **Azure Tools** o **Desarrollo multiplataforma de .NET Core** instaladas
::: moniker-end

::: moniker range=">= vs-2019"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) con las cargas de trabajo **Desarrollo web**, **Azure Tools** o **Desarrollo multiplataforma de .NET Core** instaladas
* [Herramientas de desarrollo de .NET Core 2.2](https://dotnet.microsoft.com/download/dotnet-core/2.2) para el desarrollo con .NET Core 2.2
::: moniker-end

## <a name="create-a-web-application-project"></a>Creación de un proyecto de aplicación web

En Visual Studio, cree un proyecto **Aplicación web ASP.NET Core** denominado `WebFrontEnd`. Seleccione **Aplicación web** para crear una aplicación web con Razor Pages. 
  
::: moniker range="vs-2017"

No seleccione **Habilitar compatibilidad con Docker**. Esta se agrega más adelante.

![Captura de pantalla de la creación del proyecto web](./media/tutorial-multicontainer/docker-tutorial-enable-docker-support.png)

::: moniker-end

::: moniker range="vs-2019"

![Captura de pantalla de la creación del proyecto web](./media/tutorial-multicontainer/vs-2019/new-aspnet-core-project1.png)

No seleccione **Habilitar compatibilidad con Docker**. Esta se agrega más adelante.

![Captura de pantalla de la creación del proyecto web](./media/tutorial-multicontainer/vs-2019/new-aspnet-core-project.png)

::: moniker-end

## <a name="create-a-web-api-project"></a>Creación de un proyecto de API web

Agregue un proyecto a la misma solución y asígnele el nombre *MyWebAPI*. Seleccione **API** como tipo de proyecto y desactive la casilla de **Configure for HTTPS** (Configurar para HTTPS). En este diseño solo se usa SSL para la comunicación con el cliente, no para la comunicación entre contenedores de la misma aplicación web. Solo `WebFrontEnd` necesita HTTPS.

::: moniker range="vs-2017"
   ![Captura de pantalla de la creación del proyecto de API web](./media/tutorial-multicontainer/docker-tutorial-mywebapi.png)
::: moniker-end
::: moniker range="vs-2019"
   ![Captura de pantalla de la creación del proyecto de API web](./media/tutorial-multicontainer/vs-2019/web-api-project.png)
::: moniker-end

## <a name="add-code-to-call-the-web-api"></a>Adición de código para llamar a la API web

1. En el proyecto `WebFrontEnd`, abra el archivo *Index.cshtml.cs* y reemplace el método `OnGet` por el código siguiente.

   ```csharp
    public async Task OnGet()
    {
       ViewData["Message"] = "Hello from webfrontend";

       using (var client = new System.Net.Http.HttpClient())
       {
          // Call *mywebapi*, and display its response in the page
          var request = new System.Net.Http.HttpRequestMessage();
          request.RequestUri = new Uri("http://mywebapi/api/values/1");
          var response = await client.SendAsync(request);
          ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
       }
    }
   ```

1. En el archivo *Index.cshtml*, agregue una línea para mostrar `ViewData["Message"]` para que el archivo sea similar al código siguiente:
    
      ```cshtml
      @page
      @model IndexModel
      @{
          ViewData["Title"] = "Home page";
      }
    
      <div class="text-center">
          <h1 class="display-4">Welcome</h1>
          <p>Learn about <a href="https://docs.microsoft.com/aspnet/core">building Web apps with ASP.NET Core</a>.</p>
          <p>@ViewData["Message"]</p>
      </div>
      ```

1. Ahora, en el proyecto de API web, agregue código al controlador Valores para personalizar el mensaje devuelto por la API para la llamada agregada desde *webfrontend*.
    
      ```csharp
        // GET api/values/5
        [HttpGet("{id}")]
        public ActionResult<string> Get(int id)
        {
            return "webapi (with value " + id + ")";
        }
      ```

1. En el proyecto `WebFrontEnd`, seleccione **Agregar > Compatibilidad con el orquestador de contenedores**. Aparece el cuadro de diálogo **Opciones de soporte técnico de Docker**.

1. Seleccione **Docker Compose**.

1. Seleccione el sistema operativo de destino, por ejemplo, Linux.

   ![Captura de pantalla de la elección del sistema operativo de destino](media/tutorial-multicontainer/docker-tutorial-docker-support-options.PNG)

   Visual Studio crea un archivo *docker-compose.yml* y un archivo *.dockerignore* en el nodo **docker-compose** de la solución, y ese proyecto se muestra en negrita, lo que indica que es el proyecto de inicio.

   ![Captura de pantalla del Explorador de soluciones con el proyecto docker-compose agregado](media/tutorial-multicontainer/multicontainer-solution-explorer.png)

   *docker-compose.yml* aparece de la manera siguiente:

   ```yaml
   version: '3.4'

    services:
      webfrontend:
        image: ${DOCKER_REGISTRY-}webfrontend
        build:
          context: .
          dockerfile: WebFrontEnd/Dockerfile
   ```

   El archivo *.dockerignore* contiene los tipos de archivo y las extensiones que no quiere que Docker incluya en el contenedor. Normalmente, estos archivos están asociados al entorno de desarrollo y el control de código fuente, no forman parte de la aplicación o el servicio que se está desarrollando.

   Vea la sección **Herramientas de contenedor** del panel de salida para obtener detalles de los comandos que se ejecutan.  Puede ver que la herramienta de línea de comandos docker-compose se usa para configurar y crear los contenedores en tiempo de ejecución.

1. En el proyecto de API web, vuelva a hacer clic con el botón derecho en el nodo del proyecto y seleccione **Agregar** > **Compatibilidad con el orquestador de contenedores**. Seleccione **Docker Compose** y, después, el mismo sistema operativo de destino.  

    > [!NOTE]
    > En este paso, Visual Studio le ofrece crear un Dockerfile. Si lo hace en un proyecto que ya tiene compatibilidad con Docker, se le pregunta si quiere sobrescribir el Dockerfile existente. Si ha realizado cambios que quiere conservar en el Dockerfile, seleccione no.

    Visual Studio realiza algunos cambios en el archivo YML de Docker Compose. Ahora ambos servicios están incluidos.

    ```yaml
    version: '3.4'
    
    services:
      webfrontend:
        image: ${DOCKER_REGISTRY-}webfrontend
        build:
          context: .
          dockerfile: WebFrontEnd/Dockerfile
    
      mywebapi:
        image: ${DOCKER_REGISTRY-}mywebapi
        build:
          context: .
          dockerfile: MyWebAPI/Dockerfile
    ```

1. Ejecute el sitio localmente ahora (F5 o Ctrl + F5) para comprobar que funciona según lo previsto. Si todo está configurado correctamente, aparece el mensaje "Hello from webfrontend and webapi (with value 1)" (Hola desde webfrontend y webapi [con valor 1]).

   El primer proyecto que se usa al agregar la orquestación de contenedores está configurado para iniciarse al ejecutar o depurar. Puede configurar la acción de inicio en las **Propiedades del proyecto** del proyecto docker-compose.  En el nodo del proyecto docker-compose, haga clic con el botón derecho para abrir el menú contextual y luego seleccione **Propiedades** o use Alt + Entrar.  En la captura de pantalla siguiente se muestran las propiedades deseables para la solución que se usa aquí.  Por ejemplo, puede cambiar la página que se carga mediante la personalización de la propiedad **URL de servicio**.

   ![Captura de pantalla de las propiedades del proyecto docker-compose](media/tutorial-multicontainer/launch-action.png)

   Esto es lo que se ve cuando se inicia:

   ![Captura de pantalla de la aplicación web en ejecución](media/tutorial-multicontainer/webfrontend.png)

## <a name="next-steps"></a>Pasos siguientes

Vea las opciones para implementar [contenedores en Azure](/azure/containers).

## <a name="see-also"></a>Vea también
  
[Docker Compose](https://docs.docker.com/compose/)  
[Herramientas de contenedor](/visualstudio/containers/)
