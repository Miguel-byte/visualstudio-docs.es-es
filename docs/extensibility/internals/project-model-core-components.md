---
title: Componentes principales del modelo de proyecto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e84438aa57492e28c4e8debc8c1c54e5f496eae
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725727"
---
# <a name="project-model-core-components"></a>Componentes principales del modelo de proyecto
Las tablas siguientes se expanden en el modelo de proyecto. Las tablas presentan breves descripciones de las interfaces y los servicios identificados en el modelo, así como las interfaces y servicios asociados a objetos específicos. Además, las tablas detallan otras interfaces que son opcionales en la creación y el mantenimiento del proyecto en función de los requisitos de su tipo de proyecto específico.

 Para obtener más información, consulte [compatibilidad con herramientas de exploración de símbolos](../../extensibility/internals/supporting-symbol-browsing-tools.md).

### <a name="package-object"></a>Objeto de paquete

|Interfaz|Comentarios|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|Inicializa un VSPackage en el IDE y pone sus servicios a disposición del IDE.|

### <a name="project-factory-object"></a>Objeto de generador de proyectos

|Interfaz|Comentarios|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Administra la creación de nuevos proyectos y la apertura de proyectos existentes.|

### <a name="project-objects"></a>Objetos de proyecto

|Interfaces|Comentarios|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Administra la adición y eliminación de elementos de proyecto, abre editores y mantiene la asignación entre cada moniker de documento y el `VSITEMID`. Hereda de `IVsProject` y `IVsProject2`.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Administra las propiedades de navegación y presentación y proporciona eventos.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Habilita la ejecución de comandos similar a la de `IOleCommandTarget` para los comandos como cortar y cambiar nombre que se aplican solo cuando el foco está en Explorador de soluciones.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Actúa como la interfaz de destino del comando principal para una jerarquía de proyecto. Es la interfaz estándar para consultar el estado de los comandos o el estado y los comandos de ejecución de los objetos. Está disponible cuando no tiene el foco en la ventana del proyecto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Coordina la persistencia del estado del proyecto. Normalmente, el estado del proyecto se almacena como un archivo de proyecto, pero se puede adaptar a sistemas de almacenamiento que no estén basados en archivos.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Permite al proyecto administrar todos los aspectos de la persistencia de sus elementos de proyecto, ya sea como archivos en disco u objetos de otros sistemas de almacenamiento. La interfaz de `IVsPersistHierarchyItem2` se utiliza para los elementos que no implementan la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Coordina las interacciones con el control de código fuente.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Permite que los proyectos administren la información de configuración.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Administra objetos de configuración de proyecto, como configuraciones de depuración y lanzamiento. Las operaciones de compilación, implementación y depuración se coordinan a través de objetos de configuración de proyecto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Implementado por jerarquías para controlar las opciones de eliminación (destructiva) o eliminación (no destructiva) de los elementos de la jerarquía. Llame a la interfaz de consulta en la interfaz de `IVsHierarchyDeleteHandler` desde la interfaz de `IVsHierarchy`.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|Proporciona la opción de implementación de tener el objeto que admite la interfaz de `IVsCfgProvider2` en una identidad COM diferente que el objeto de proyecto que implementa la interfaz de `IVsHierarchy`.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Interfaz opcional implementada para que otros desarrolladores puedan extender el proyecto. La interfaz de `IVsProjectStartupServices` permite a un VSPackage de terceros registrar un GUID que se conserva en el archivo del proyecto para que cada vez que se cargue el proyecto, cargue el GUID del servicio de terceros en el archivo del proyecto y llame a `QueryService` para ese GUID.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Implementado por jerarquías de origen en una ventana de `UIHierarchy` para coordinar operaciones del portapapeles, como cortar, copiar y pegar. Utilice la interfaz `AdviseClipboardHelperEvents` para registrar eventos del portapapeles.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Proporciona información sobre un elemento arrastrado en relación con su origen de datos durante una operación de arrastrar y colocar en una ventana de jerarquía de la interfaz de usuario. Se llama desde la interfaz `IVsHierarchy`.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Proporciona información sobre un elemento arrastrado en relación con su destino de colocación durante una operación de arrastrar y colocar en una ventana de jerarquía de la interfaz de usuario. Se llama desde la interfaz `IVsHierarchy`.|

### <a name="configuration-object"></a>Objeto de configuración

|Interfaces|Comentarios|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Proporciona información sobre una configuración.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Permite que los proyectos administren la información de configuración.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Permite que un proyecto se ejecute bajo el control del depurador.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Implementado por proyectos de implementación que realizan operaciones de implementación para otros proyectos.|

### <a name="configuration-builder-object"></a>Objeto de generador de configuración

|Interfaces|Comentarios|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Administra la operación de compilación de una configuración de proyecto.|

### <a name="additional-project-objects"></a>Objetos de proyecto adicionales

|Interfaces|Comentarios|
|----------------|--------------|
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Muestra las propiedades del elemento en la ventana **propiedades** .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Muestra los resultados de la implementación.|

 En la tabla siguiente se presentan breves descripciones de los servicios identificados en el modelo de proyecto.

### <a name="services"></a>Servicios

|web de Office|Comentarios|
|-------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Lo usan los VSPackages que implementan tipos de proyecto para registrar que su generador de proyectos existe con el IDE. El VSPackage debe llamar a `QueryService` para este servicio y registrar su generador de proyectos cuando se llama a `IVsPackage::SetSite` método. Si no se llama al método `SetSite`, no se crea una instancia del proyecto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Proporciona acceso a la noción interna integrada del IDE de la solución actual, como la posibilidad de enumerar proyectos, crear nuevos proyectos, realizar un aviso de cambios en el proyecto, etc.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Lo llaman los proyectos que desean participar en el control de código fuente.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Mantiene una tabla de documentos abiertos para determinar si uno o varios de los elementos de proyecto ya están abiertos.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Contiene las interfaces y los métodos a los que se llama para abrir realmente un elemento de proyecto mediante el editor estándar o un editor específico.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Es necesario que lo llamen todos los proyectos cuando agreguen, quiten o cambien el nombre de sus elementos.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Administra los cambios en un archivo o directorio y notifica a los clientes cuando se han cambiado los archivos seleccionados en el disco.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Es necesario que lo llamen todos los proyectos y editores antes de que se hayan modificado los elementos o se guarden.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Administra el orden de las operaciones de compilación e implementación para las configuraciones de proyecto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Proporciona acceso a los servicios de depuración de bajo nivel utilizados para la mayoría de los controles de depuración.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|Habilita el acceso a VSPackages para obtener información sobre las selecciones actuales y permite la comunicación con la ventana **propiedades** .|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Proporciona funcionalidad básica del IDE relacionada con la interfaz de usuario, como la capacidad de crear y enumerar ventanas de herramientas o de documentos, o notificar un error al usuario.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|Proporciona acceso a la barra de estado del IDE.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Se utiliza para implementar el modelo de automatización. En el modelo de proyecto, devolverá un objeto de propiedades que le permite crear una instancia de ese objeto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Se utiliza para implementar eventos del portapapeles en el objeto de proyecto en la jerarquía. `SVsUIHierWinClipboardHelper` permite administrar correctamente las operaciones de cortar, copiar y pegar.|

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Lista de comprobación: creación de nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [No está en la compilación: usar clases de proyecto de HierUtil7 para implementarC++un tipo de proyecto ()](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)
- [Compatibilidad con herramientas de exploración de símbolos](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Elementos de un modelo de proyecto](../../extensibility/internals/elements-of-a-project-model.md)