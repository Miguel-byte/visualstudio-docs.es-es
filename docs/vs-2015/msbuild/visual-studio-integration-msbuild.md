---
title: Integración de Visual Studio (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, reference resolution
- MSBuild, well-known target names
- MSBuild, hosting
- MSBuild, editing project files
- MSBuild, Visual Studio integration
- MSBuild, IntelliSense
- MSBuild, output groups
- MSBuild, in-process compilers
- MSBuild, design-time target execution
ms.assetid: 06cd6d7f-8dc1-4e49-8a72-cc9e331d7bca
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c90019aa24047524005ba70aa4f1aec75f89c71d
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2019
ms.locfileid: "67825420"
---
# <a name="visual-studio-integration-msbuild"></a>Integración de Visual Studio (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio hospeda [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] para cargar y compilar proyectos administrados. Puesto que [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] es responsable del proyecto, prácticamente cualquier proyecto con el formato de [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] puede utilizarse correctamente en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], aunque el proyecto lo haya creado una herramienta diferente y tenga un proceso de compilación personalizado.  
  
 En este tema se describen los aspectos específicos del hospedaje de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] en [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] que deben tenerse en cuenta al personalizar los proyectos y los archivos .targets que se carguen y se compilen en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Le ayudarán a garantizar que las características de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] como IntelliSense y la depuración funcionan para el proyecto personalizado.  
  
 Para obtener información sobre proyectos de C++, vea [Archivos de proyecto](/cpp/build/reference/project-files).  
  
## <a name="project-file-name-extensions"></a>Extensiones de nombre de archivo de los proyectos  
 MSBuild.exe reconoce cualquier extensión de nombre de archivo de proyecto que coincida con el patrón .*proj. Sin embargo, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] solamente reconoce un subconjunto de estas extensiones de nombre de archivo de proyecto, que determinan el sistema de proyectos específico del lenguaje que cargará el proyecto. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] no dispone de ningún sistema de proyectos independiente del lenguaje basado en [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].  
  
 Por ejemplo, el sistema de proyectos de [!INCLUDE[csprcs](../includes/csprcs-md.md)] carga archivos .csproj, pero [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] no puede cargar ningún archivo .xxproj. Un archivo de proyecto para archivos de origen en un lenguaje arbitrario debe usar la misma extensión que los archivos de proyecto de [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] o [!INCLUDE[csprcs](../includes/csprcs-md.md)] que se van a cargar en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="well-known-target-names"></a>Nombres de destino conocidos  
 Al hacer clic en el comando **Compilar** en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], se ejecutará el destino predeterminado del proyecto. A menudo, este destino también se denomina `Build`. Al elegir el comando **Recompilar** o **Limpiar** , se intentará ejecutar un destino del mismo nombre en el proyecto. Al hacer clic en **Publicar** , se ejecutará un destino denominado `PublishOnly` en el proyecto.  
  
## <a name="configurations-and-platforms"></a>Configuraciones y plataformas  
 Las configuraciones se representan en los proyectos de [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] mediante propiedades agrupadas en un elemento `PropertyGroup` que contiene un atributo `Condition`. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] examina estas condiciones para crear una lista de las configuraciones y plataformas del proyecto que se van a mostrar. Para extraer correctamente esta lista, las condiciones deben tener un formato similar al siguiente:  
  
```  
Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' "  
Condition=" '$(Configuration)' == 'Release' "   
Condition=" '$(Something)|$(Configuration)|$(SomethingElse)' == 'xxx|Debug|yyy' "  
```  
  
 Con este fin, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] examina las condiciones en `PropertyGroup`, `ItemGroup`, `Import`, la propiedad y los elementos.  
  
## <a name="additional-build-actions"></a>Acciones de compilación adicionales  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] permite cambiar el nombre de los tipos de elemento de un archivo en un proyecto con la propiedad **Acción de compilación** de la ventana [Propiedades de archivo](https://msdn.microsoft.com/013c4aed-08d6-4dce-a124-ca807ca08959). Los nombres de tipo de elemento`Compile`, `EmbeddedResource`, `Content`y `None` siempre se muestran en este menú, junto con otros nombres de tipo de elemento ya presentes en el proyecto. Para garantizar que los nombres de los tipos de elemento personalizados siempre estén disponibles en este menú, puede agregarlos a un tipo de elemento denominado `AvailableItemName`. Por ejemplo, al agregar lo siguiente al archivo de proyecto, se agregará el tipo personalizado `JScript` a este menú para todos los proyectos que lo importen:  
  
```  
<ItemGroup>  
    <AvailableItemName Include="JScript"/>  
</ItemGroup>  
```  
  
> [!NOTE]
> Algunos nombres de tipo de elemento son específicos de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], pero no se muestran en esta lista desplegable.  
  
## <a name="in-process-compilers"></a>Compiladores activos  
 Cuando sea posible, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] intentará utilizar la versión activa del compilador de [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] con el fin de mejorar el rendimiento. (No es aplicable a [!INCLUDE[csprcs](../includes/csprcs-md.md)]). Para que esto funcione correctamente, se deben cumplir las condiciones siguientes:  
  
- En un destino del proyecto, debe haber una tarea denominada `Vbc` para los proyectos de [!INCLUDE[vbprvb](../includes/vbprvb-md.md)].  
  
- El parámetro `UseHostCompilerIfAvailable` de la tarea debe tener el valor true.  
  
## <a name="design-time-intellisense"></a>IntelliSense en tiempo de diseño  
 Para obtener compatibilidad con IntelliSense en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] antes de que una compilación haya generado un ensamblado de salida, se deben cumplir las condiciones siguientes:  
  
- Debe haber un destino denominado `Compile`.  
  
- El destino `Compile` o alguna de sus dependencias deben llamar a la tarea de compilador para el proyecto, como `Csc` o `Vbc`.  
  
- El destino `Compile` o alguna de sus dependencias debe hacer que el compilador reciba todos los parámetros necesarios para IntelliSense, en particular todas las referencias.  
  
- Se deben cumplir las condiciones que aparecen en la sección "Compiladores activos".  
  
## <a name="building-solutions"></a>Compilar soluciones  
 En [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], el propio [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] controla el archivo de solución y el orden de compilación de los proyectos. Al compilar una solución con msbuild.exe en la línea de comandos, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] analiza el archivo de solución y ordena las compilaciones del proyecto. En ambos casos, los proyectos se compilan individualmente en orden de dependencia y no se recorren las referencias entre proyectos. Por el contrario, cuando los proyectos individuales se compilan con msbuild.exe, se recorren las referencias entre proyectos.  
  
 Para compilar en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], la propiedad `$(BuildingInsideVisualStudio)` se establece en `true`. Esto se puede utilizar en el proyecto o en archivos .targets para que la compilación se comporte de manera diferente.  
  
## <a name="displaying-properties-and-items"></a>Mostrar propiedades y elementos  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] reconoce algunos nombres y valores de propiedad. Por ejemplo, la propiedad siguiente de un proyecto hará que aparezca **Aplicación Windows** en el cuadro **Tipo de aplicación** del **Diseñador de proyectos**.  
  
```  
<OutputType>WinExe</OutputType>  
```  
  
 El valor de propiedad se puede editar en el **Diseñador de proyectos** y guardar en el archivo del proyecto. Si al editar la propiedad manualmente se le da un valor no válido, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] mostrará una advertencia cuando se cargue el proyecto y reemplazará el valor no válido por un valor predeterminado.  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] puede aplicar valores predeterminados a algunas propiedades. Estas propiedades no se conservarán en el archivo del proyecto a menos que tengan valores no predeterminados.  
  
 Las propiedades con nombres arbitrarios no se muestran en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Para modificar las propiedades arbitrarias en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], debe abrir el archivo del proyecto en el editor XML y editarlas a mano. Para obtener más información, consulte la sección [Editing Project Files in Visual Studio](#BKMK_EditingProjects) más adelante en este tema.  
  
 Los elementos definidos en el proyecto con nombres de tipo de elemento arbitrarios se muestran de forma predeterminada en el Explorador de soluciones bajo su nodo de proyecto. Para ocultar un elemento, establezca los metadatos `Visible` en `false`. Por ejemplo, el elemento siguiente participará en el proceso de compilación pero no se mostrará en el Explorador de soluciones.  
  
```  
<ItemGroup>  
    <IntermediateFile Include="cache.temp">  
        <Visible>false</Visible>  
    </IntermediateFile>  
</ItemGroup>  
```  
  
 De forma predeterminada, no se muestran los elementos declarados en archivos importados al proyecto. Los elementos creados durante el proceso de compilación nunca se muestran en el Explorador de soluciones.  
  
## <a name="conditions-on-items-and-properties"></a>Condiciones en elementos y propiedades  
 Durante una compilación, se respetan totalmente todas las condiciones.  
  
 Al determinar los valores de propiedad que se van a mostrar, las propiedades que [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] considera dependientes de la configuración se evalúan de manera diferente que las que considera independientes. Para las propiedades que considera dependientes de la configuración, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] establece las propiedades `Configuration` y `Platform` de manera apropiada e indica a [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] que vuelva a evaluar el proyecto. En el caso de las propiedades que considera como independientes de la configuración, no importa cómo se evalúen las condiciones.  
  
 Las expresiones condicionales en los elementos siempre se omiten al decidir si el elemento debe mostrarse en el Explorador de soluciones.  
  
## <a name="debugging"></a>Depuración  
 Para buscar e iniciar el ensamblado de salida y asociar el depurador, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] necesita que las propiedades `OutputPath`, `AssemblyName` y `OutputType` estén definidas correctamente. El depurador no podrá realizar la asociación si el proceso de compilación no hiciera que el compilador generase un archivo .pdb.  
  
## <a name="design-time-target-execution"></a>Ejecución del destino en tiempo de diseño  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] intenta ejecutar los destinos con algunos nombres cuando carga un proyecto. Estos destinos incluyen `Compile`, `ResolveAssemblyReferences`, `ResolveCOMReferences`, `GetFrameworkPaths` y `CopyRunEnvironmentFiles`. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ejecuta estos destinos para que el compilador pueda inicializarse con el fin de proporcionar IntelliSense, el depurador pueda inicializarse y las referencias mostradas en el Explorador de soluciones puedan resolverse. Si estos destinos no están presentes, el proyecto se cargará y se compilará correctamente pero la experiencia en tiempo de diseño de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] no será totalmente funcional.  
  
## <a name="BKMK_EditingProjects"></a> Editing Project Files in Visual Studio  
 Para editar directamente un proyecto de [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], puede abrir el archivo del proyecto en el editor XML de Visual Studio.  
  
#### <a name="to-unload-and-edit-a-project-file-in-visual-studio"></a>Para descargar y editar un archivo de proyecto en Visual Studio  
  
1. En el **Explorador de soluciones**, abra el menú contextual del proyecto y, a continuación, elija **Descargar el proyecto**.  
  
     El proyecto aparecerá marcado como **(no disponible)** .  
  
2. En el **Explorador de soluciones**, abra el menú contextual del proyecto no disponible y seleccione **Editar\<Archivo de proyecto>** .  
  
     El archivo de proyecto se abrirá en el Editor XML de Visual Studio.  
  
3. Edite, guarde y, a continuación, cierre el archivo de proyecto.  
  
4. En el **Explorador de soluciones**, abra el menú contextual del proyecto no disponible y, a continuación, elija **Volver a cargar el proyecto**.  
  
## <a name="intellisense-and-validation"></a>IntelliSense y validación  
 Al utilizar el editor XML para modificar archivos de proyecto, los archivos de esquema de [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] administran la validación e IntelliSense. Estos archivos se instalan en la caché del esquema, que se encuentra en *\<directorio de instalación de Visual Studio >* \Xml\Schemas\1033\MSBuild.  
  
 Los tipos básicos de [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] se definen en Microsoft.Build.Core.xsd y los tipos comunes utilizados por [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] se definen en Microsoft.Build.CommonTypes.xsd. Para personalizar los esquemas con el fin de disponer de IntelliSense y de la validación para los nombres de tipo de elemento, propiedades y tareas personalizados, puede editar Microsoft.Build.xsd o crear su propio esquema que incluya los esquemas CommonTypes o Core. Si crea su propio esquema, tendrá que dirigir el editor XML para que lo busque mediante la ventana **Propiedades** .  
  
## <a name="editing-loaded-project-files"></a>Editar archivos de proyecto cargados  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] almacena en memoria caché el contenido de los archivos de proyecto y de los archivos importados por los archivos de proyecto. Si edita un archivo de proyecto cargado, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pedirá automáticamente que recargue el proyecto para que se apliquen los cambios. Sin embargo, si edita un archivo importado por un proyecto cargado, no habrá ninguna solicitud y deberá descargar y recargar el proyecto manualmente para que se apliquen los cambios.  
  
## <a name="output-groups"></a>Grupos de resultados  
 Algunos destinos definidos en Microsoft.Common.targets tienen nombres acabados en `OutputGroups` o `OutputGroupDependencies`. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] llama a estos destinos para obtener listas específicas de las salidas del proyecto. Por ejemplo, el destino `SatelliteDllsProjectOutputGroup` crea una lista de todos los ensamblados satélite que creará una compilación. Características como la publicación, la implementación y las referencias entre proyectos utilizan estos grupos de resultados. Los proyectos que no los definen se cargarán y compilarán en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], pero es posible que algunas características no funcionen correctamente.  
  
## <a name="reference-resolution"></a>Resolución de referencias  
 La resolución de referencias es el proceso de utilizar los elementos de referencia almacenados en un archivo del proyecto para buscar los ensamblados reales. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] debe desencadenar una resolución de referencias para que se muestren las propiedades detalladas de cada referencia en la ventana **Propiedades**. En la lista siguiente se describen los tres tipos de referencias y cómo se resuelven.  
  
- Referencias de ensamblado:  
  
  El sistema de proyectos llama a un destino con el nombre conocido `ResolveAssemblyReferences`. Este destino debe generar elementos con el nombre de tipo `ReferencePath`. Cada uno de estos elementos debe tener una especificación de elemento (el valor del atributo `Include` de un elemento) que contenga la ruta completa a la referencia. Los elementos deben tener todos los metadatos de los elementos de entrada recorridos, además de los nuevos metadatos siguientes:  

  - `CopyLocal`, que indica si el ensamblado debe copiarse en la carpeta de salida, establecida en true o en false.  

  - `OriginalItemSpec`, que contiene la especificación del elemento original de la referencia.  

  - `ResolvedFrom`, establecido en "{TargetFrameworkDirectory}" si se ha resuelto en el directorio de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
- Referencias COM:  
  
     El sistema de proyectos llama a un destino con el nombre conocido `ResolveCOMReferences`. Este destino debe generar elementos con el nombre de tipo `ComReferenceWrappers`. Cada uno de estos elementos debe tener una especificación del elemento que contiene la ruta de acceso completa al ensamblado de interoperabilidad para obtener la referencia COM. Los elementos deben tener todos los metadatos de los elementos de entrada recorridos, además de los nuevos metadatos con el nombre `CopyLocal`, que indica si el ensamblado se debe copiar en la carpeta de salida, establecido en true o false.  
  
- Referencias nativas  
  
     El sistema de proyectos llama a un destino con el nombre conocido `ResolveNativeReferences`. Este destino debe generar elementos con el nombre de tipo `NativeReferenceFile`. Los elementos deben tener todos los metadatos de los elementos de entrada recorridos, además de un nuevo fragmento de metadatos denominado `OriginalItemSpec`, que contiene la especificación del elemento original de la referencia.  
  
## <a name="performance-shortcuts"></a>Métodos abreviados de rendimiento  
 Si inicia la depuración en la interfaz de usuario de Visual Studio (eligiendo la tecla F5 o **Depurar**, **Iniciar depuración** en la barra de menús), el proceso de compilación utiliza una comprobación de actualización rápida para mejorar el rendimiento. En algunos casos en los que las compilaciones personalizadas crean archivos que, a su vez, se compilan, la comprobación de actualización rápida no identifica correctamente los archivos modificados. Los proyectos que necesitan otras comprobaciones de actualización más completas pueden desactivar la comprobación rápida estableciendo la variable de entorno `DISABLEFASTUPTODATECHECK=1`. O bien, los proyectos pueden establecerla como una propiedad de MSBuild en el proyecto o en un archivo que el proyecto importe.  
  
 Para las compilaciones periódicas en Visual Studio, no se aplica la comprobación de actualización rápida y el proyecto se compilará como si se invocara la compilación en un símbolo del sistema.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Extender el proceso de compilación de Visual Studio](../msbuild/how-to-extend-the-visual-studio-build-process.md)   
 [Iniciar una compilación desde el IDE](../msbuild/starting-a-build-from-within-the-ide.md)   
 [Registrar las extensiones de .NET Framework](../msbuild/registering-extensions-of-the-dotnet-framework.md)   
 [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)   
 [Elemento Item (MSBuild)](../msbuild/item-element-msbuild.md)   
 [Elemento Property (MSBuild)](../msbuild/property-element-msbuild.md)   
 [Elemento Target (MSBuild)](../msbuild/target-element-msbuild.md)   
 [Csc (tarea)](../msbuild/csc-task.md)   
 [Tarea Vbc](../msbuild/vbc-task.md)
