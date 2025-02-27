---
title: 'Nueva generación de proyectos: en el capó, parte uno | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 41b2b229fe343c9f6d515ba757e4bd976ee7fda5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726528"
---
# <a name="new-project-generation-under-the-hood-part-one"></a>Nueva generación de proyectos: aspectos técnicos, primera parte
¿Alguna vez ha pensado en cómo crear su propio tipo de proyecto? ¿Se pregunta qué ocurre realmente cuando se crea un nuevo proyecto? Echemos un vistazo al Capó y veamos lo que está ocurriendo realmente.

 Hay varias tareas que Visual Studio coordina:

- Muestra un árbol de todos los tipos de proyecto disponibles.

- Muestra una lista de plantillas de aplicación para cada tipo de proyecto y le permite elegir una.

- Recopila información del proyecto para la aplicación, como el nombre y la ruta de acceso del proyecto.

- Pasa esta información al generador de proyectos.

- Genera elementos y carpetas de proyecto en la solución actual.

## <a name="the-new-project-dialog-box"></a>Cuadro de diálogo nuevo proyecto
 Todo comienza cuando se selecciona un tipo de proyecto para un proyecto nuevo. Para empezar, haga clic en **nuevo proyecto** en el menú **archivo** . Aparece el cuadro de diálogo **nuevo proyecto** , que tiene un aspecto similar al siguiente:

 ![Cuadro de diálogo nuevo proyecto](../../extensibility/internals/media/newproject.gif "NewProject")

 Echemos un vistazo más de cerca. En el árbol **tipos de proyecto** se muestran los distintos tipos de proyecto que se pueden crear. Al seleccionar un tipo de proyecto como **Visual C# Windows**, verá una lista de plantillas de aplicación para comenzar. **Las plantillas instaladas de Visual Studio** se instalan con Visual Studio y están disponibles para cualquier usuario del equipo. Las nuevas plantillas que cree o recopile se pueden agregar a **Mis plantillas** y solo están disponibles para usted.

 Al seleccionar una plantilla como **aplicación de Windows**, aparece una descripción del tipo de aplicación en el cuadro de diálogo. en este caso, **un proyecto para crear una aplicación con una interfaz de usuario de Windows**.

 En la parte inferior del cuadro de diálogo **nuevo proyecto** , verá varios controles que recopilan más información. Los controles que se ven dependen del tipo de proyecto, pero generalmente incluyen un cuadro de texto de **nombre** de proyecto, un cuadro de texto de **Ubicación** y un botón de **exploración** relacionado, y un cuadro de texto de **nombre de solución** y un **Directorio de creación relacionado para la solución.** casilla.

## <a name="populating-the-new-project-dialog-box"></a>Rellenar el cuadro de diálogo nuevo proyecto
 ¿De dónde obtiene el cuadro de diálogo **nuevo proyecto** su información? Hay dos mecanismos en el trabajo aquí, uno de ellos en desuso. El cuadro de diálogo **nuevo proyecto** combina y muestra la información obtenida de ambos mecanismos.

 El método anterior (en desuso) utiliza las entradas del registro del sistema y los archivos. vsdir. Este mecanismo se ejecuta cuando se abre Visual Studio. El método más reciente utiliza los archivos. vstemplate. Este mecanismo se ejecuta cuando se inicializa Visual Studio, por ejemplo, mediante la ejecución de

```
devenv /setup
```

 o

```
devenv /installvstemplates
```

### <a name="project-types"></a>Tipos de proyecto
 La posición y los nombres de los nodos raíz de **tipos de proyecto** , como **Visual C#**  y **otros lenguajes**, vienen determinados por las entradas del registro del sistema. La organización de los nodos secundarios, como la **base de datos** y **Smart Device**, refleja la jerarquía de las carpetas que contienen los archivos. vstemplate correspondientes. Echemos un vistazo primero a los nodos raíz.

#### <a name="project-type-root-nodes"></a>Nodos raíz de tipo de proyecto
 Cuando se inicializa [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], se recorren las subclaves de la clave del registro del sistema HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\NewProjectTemplates\TemplateDirs para compilar y nombrar los nodos raíz del árbol de **tipos de proyecto** . Esta información se almacena en caché para su uso posterior. Observe la clave TemplateDirs \\ {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC} \\/1. Cada entrada es un GUID de VSPackage. Se omite el nombre de la subclave (/1), pero su presencia indica que se trata de un nodo raíz de **tipos de proyecto** . Un nodo raíz puede, A su vez, tener varias subclaves que controlan su apariencia en el árbol de **tipos de proyecto** . Echemos un vistazo a algunos de ellos.

##### <a name="default"></a>(Predeterminado)
 Es el identificador de recurso de la cadena traducida que nombra el nodo raíz. El recurso de cadena se encuentra en el archivo DLL satélite seleccionado por el GUID del VSPackage.

 En el ejemplo, el GUID de VSPackage es

 {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}

 y el ID. de recurso (valor predeterminado) del nodo raíz (/1) es #2345

 Si busca el GUID en la clave de paquetes cercanos y examina la subclave SatelliteDll, puede encontrar la ruta de acceso del ensamblado que contiene el recurso de cadena:

 Ruta de instalación de \<Visual StudioVC#> \ \VCSPackages\1033\csprojui.dll

 Para comprobarlo, abra el explorador de archivos y arrastre csprojui. dll al directorio de Visual Studio. La tabla de cadenas muestra que el #2345 de recursos tiene el valor **Visual C#** de la leyenda.

##### <a name="sortpriority"></a>SortPriority
 Determina la posición del nodo raíz en el árbol de **tipos de proyecto** .

 SortPriority REG_DWORD 0x00000014 (20)

 Cuanto menor sea el número de prioridad, mayor será la posición en el árbol.

##### <a name="developeractivity"></a>DeveloperActivity
 Si esta subclave está presente, la posición del nodo raíz se controla mediante el cuadro de diálogo Configuración del desarrollador. Por ejemplo,

 DeveloperActivity REG_SZVC#

 indica que el C# visual será un nodo raíz si Visual Studio está establecido para el desarrollo de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]. De lo contrario, será un nodo secundario de **otros lenguajes**.

##### <a name="folder"></a>Carpeta
 Si esta subclave está presente, el nodo raíz se convierte en un nodo secundario de la carpeta especificada. Aparece una lista de las carpetas posibles bajo la clave

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\NewProjectTemplates\PseudoFolders

 Por ejemplo, la entrada proyectos de base de datos tiene una clave de carpeta que coincide con la entrada otros tipos de proyectos de PseudoFolders. Por lo tanto, en el árbol **tipos de proyecto** , los proyectos de **base de datos** serán un nodo secundario de **otros tipos de proyecto**.

#### <a name="project-type-child-nodes-and-vstdir-files"></a>Nodos secundarios de tipo de proyecto y archivos. vstdir
 La posición de los nodos secundarios en el árbol **tipos de proyecto** sigue a la jerarquía de las carpetas de las carpetas ProjectTemplates. En el caso de las plantillas de máquina (**plantillas instaladas de Visual Studio**), la ubicación típica es \Archivos de Programa\microsoft Visual Studio 14.0 \ Common7\IDE\ProjectTemplates\ y para plantillas de usuario (**Mis plantillas**), la ubicación típica es \Mis documentos \ @No__t_2 de Visual Studio 14.0 \ Templates\ProjectTemplates. Las jerarquías de carpetas de estas dos ubicaciones se combinan para crear el árbol de **tipos de proyecto** .

 En Visual Studio con C# la configuración de desarrollador, el árbol de **tipos de proyecto** tiene un aspecto similar al siguiente:

 ![Tipos de proyecto](../../extensibility/internals/media/projecttypes.png "ProjectTypes")

 La carpeta ProjectTemplates correspondiente tiene el siguiente aspecto:

 ![Plantillas de proyecto](../../extensibility/internals/media/projecttemplates.png "ProjectTemplates")

 Cuando se abre el cuadro de diálogo **nuevo proyecto** , [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] recorre la carpeta ProjectTemplates y vuelve a crear su estructura en el árbol **tipos de proyecto** con algunos cambios:

- El nodo raíz del árbol de **tipos de proyecto** viene determinado por la plantilla de aplicación.

- El nombre del nodo se puede localizar y puede contener caracteres especiales.

- Se puede cambiar el criterio de ordenación.

##### <a name="finding-the-root-node-for-a-project-type"></a>Buscar el nodo raíz de un tipo de proyecto
 Cuando Visual Studio atraviesa las carpetas ProjectTemplates, abre todos los archivos. zip y extrae los archivos. vstemplate. Un archivo. vstemplate usa XML para describir una plantilla de aplicación. Para obtener más información, vea [nueva generación de proyectos: debajo del capó, parte dos](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 La etiqueta de > de \<ProjectType determina el tipo de proyecto de la aplicación. Por ejemplo, el archivo \CSharp\SmartDevice\WindowsCE\1033\WindowsCE-EmptyProject.zip contiene un archivo EmptyProject. vstemplate que tiene esta etiqueta:

```
<ProjectType>CSharp</ProjectType>
```

 La etiqueta de > de \<ProjectType, y no la subcarpeta de la carpeta ProjectTemplates, determina el nodo raíz de una aplicación en el árbol de **tipos de proyecto** . En el ejemplo, Windows CE aplicaciones aparecían en el nodo raíz **Visual C#**  y, incluso si fuera a la carpeta de WindowsCE, en la carpeta de VisualBasic aparece Windows CE aplicaciones todavía en la raíz **Visual C#**  nodo.

##### <a name="localizing-the-node-name"></a>Localizar el nombre del nodo
 Cuando Visual Studio atraviesa las carpetas ProjectTemplates, examina cualquier archivo. vstdir que encuentre. Un archivo. vstdir es un archivo XML que controla el aspecto del tipo de proyecto en el cuadro de diálogo **nuevo proyecto** . En el archivo. vstdir, use la etiqueta \<LocalizedName > para asignar un nombre al nodo **tipos de proyecto** .

 Por ejemplo, el archivo \CSharp\Database\TemplateIndex.vstdir contiene esta etiqueta:

```
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>
```

 Esto determina el archivo DLL satélite y el ID. de recurso de la cadena traducida que nombra el nodo raíz, en este caso, **base de datos**. El nombre localizado puede contener caracteres especiales que no están disponibles para los nombres de carpeta, como **.net**.

 Si no hay ninguna etiqueta de > de \<LocalizedName, el tipo de proyecto se denomina en la propia carpeta, **SmartPhone2003**.

##### <a name="finding-the-sort-order-for-a-project-type"></a>Buscar el criterio de ordenación de un tipo de proyecto
 Para determinar el criterio de ordenación del tipo de proyecto, los archivos. vstdir usan la etiqueta de > de \<SortOrder.

 Por ejemplo, el archivo \CSharp\Windows\Windows.vstdir contiene esta etiqueta:

```
<SortOrder>5</SortOrder>
```

 El archivo \CSharp\Database\TemplateIndex.vstdir tiene una etiqueta con un valor mayor:

```
<SortOrder>5000</SortOrder>
```

 Cuanto menor sea el número de la etiqueta de > de \<SortOrder, mayor será la posición en el árbol, por lo que el nodo de **Windows** aparecerá más arriba que el nodo de **base de datos** del árbol de **tipos de proyecto** .

 Si no se especifica ninguna etiqueta de > de \<SortOrder para un tipo de proyecto, aparece en orden alfabético tras cualquier tipo de proyecto que contenga \<SortOrder especificaciones de >.

 Tenga en cuenta que no hay ningún archivo. vstdir en las carpetas Mis documentos (**Mis plantillas**). Los nombres de tipo de proyecto de aplicación de usuario no se localizan y aparecen en orden alfabético.

#### <a name="a-quick-review"></a>Una revisión rápida
 Vamos a modificar el cuadro de diálogo **nuevo proyecto** y crear una nueva plantilla de proyecto de usuario.

1. Agregue una subcarpeta MyProjectNode a la carpeta \Archivos de Programa\microsoft Visual Studio 14.0 \ Common7\IDE\ProjectTemplates\CSharp

2. Cree un archivo de proyecto. vstdir en la carpeta MyProjectNode con cualquier editor de texto.

3. Agregue estas líneas al archivo. vstdir:

   ```
   <TemplateDir Version="1.0.0">
       <SortOrder>6</SortOrder>
   </TemplateDir>
   ```

4. Guarde y cierre el archivo. vstdir.

5. Cree un archivo de proyecto. vstemplate en la carpeta MyProjectNode con cualquier editor de texto.

6. Agregue estas líneas al archivo. vstemplate:

   ```
   <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
       <TemplateData>
           <ProjectType>CSharp</ProjectType>
       </TemplateData>
   </VSTemplate>
   ```

7. Guarde el archivo. vstemplate y cierre el editor.

8. Envíe el archivo. vstemplate a una nueva carpeta MyProjectNode\MyProject.zip comprimida.

9. En la ventana de comandos de Visual Studio, escriba:

    ```
    devenv /installvstemplates
    ```

   Abra Visual Studio.

10. Abra el cuadro de diálogo **nuevo proyecto** y expanda el nodo del proyecto **Visual C#**  .

    ![MyProjectNode](../../extensibility/internals/media/myprojectnode.png "MyProjectNode")

    **MyProjectNode** aparece como un nodo secundario de Visual C# justo debajo del nodo Windows.

## <a name="see-also"></a>Vea también
- [Nueva generación de proyectos: aspectos técnicos, segunda parte](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)