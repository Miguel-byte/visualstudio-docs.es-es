---
title: Leer un modelo UML en el código del programa | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, reading models
ms.assetid: 0f63105e-6079-498a-94f1-318c0f5f9621
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bbc55204987f4b6ea0d45c4228f6c194f1ebaf64
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671308"
---
# <a name="read-a-uml-model-in-program-code"></a>Leer un modelo UML en el código del programa
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede cargar un modelo UML y sus diagramas usando la API de UML.

## <a name="Reading"></a>Leer un modelo en el código del programa
 Para tener acceso al contenido de un modelo sin mostrarlo en una ventana de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], utilice `ModelingProject.LoadReadOnly()`.

 Por ejemplo:

```
using Microsoft.VisualStudio.Uml.Classes;
               // for IElement
using Microsoft.VisualStudio.ArchitectureTools.Extensibility;
               // for ModelingProject
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
               // for IModelStore
...
string projectPath = @"C:\MyProjectFolder\MyProject.modelproj";
using (IModelingProjectReader projectReader =
           ModelingProject.LoadReadOnly(projectPath))
{
   IModelStore store = projectReader.Store;
   foreach (IClass umlClass in store.AllInstances<IClass>())
   {
       ...
   }
}
```

 Si desea leer las formas de un diagrama, debe leer el proyecto y, a continuación, el diagrama.

 Por ejemplo:

```
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
                             // for IDiagram
...
foreach (string diagramFile in projectReader. DiagramFileNames)
{
  IDiagram diagram = projectReader.LoadDiagram(diagramFile);
  foreach (IShape<IElement> shape
         in diagram.GetChildShapes<IElement>())
  { ... }
}
```

## <a name="alternative-methods"></a>Métodos alternativos
 En el caso de muchas aplicaciones, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Modelbus le permite hacer referencia a modelos y elementos dentro de ellos, con mayor robustez y flexibilidad que con los métodos descritos en este tema. Proporciona un método estándar para realizar vínculos entre elementos arbitrarios, en los mismos modelos o en otros diferentes. Para obtener más información, vea [integrar modelos UML con otros modelos y herramientas](../modeling/integrate-uml-models-with-other-models-and-tools.md).

 También puede abrir modelos y diagramas en la interfaz de usuario mediante la API de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Para obtener más información, vea [abrir un modelo UML mediante la API de Visual Studio](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md).

## <a name="Standalone"></a>Aplicaciones independientes
 El ejemplo de la sección anterior funcionará en las extensiones de Visual Studio. Es posible leer un modelo en una aplicación independiente, pero debe agregar algunas referencias al proyecto de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

> [!NOTE]
> Es probable que los detalles sobre cómo leer un modelo en una aplicación independiente cambien en versiones futuras del producto. Algunas características que son accesibles en la versión actual podrían no estar disponibles en versiones futuras.

#### <a name="to-add-references-to-read-a-model-in-a-stand-alone-application"></a>Para agregar referencias para leer un modelo en una aplicación independiente.

1. En Explorador de soluciones, haga clic con el botón secundario en el proyecto en el que va a compilar la aplicación y, a continuación, haga clic en **propiedades**. En el editor de propiedades, en la pestaña **aplicación** , establezca **plataforma de destino** en la versión requerida del .NET Framework.

2. Agregue las referencias de [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] que necesita para tener acceso a los modelos UML, normalmente:

   - Microsoft.VisualStudio.Uml.Interfaces.dll

   - Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll

3. Además de las referencias enumeradas en las secciones anteriores, agregue las siguientes referencias de proyecto desde **\Archivos de Programa\microsoft Visual Studio [versión] \Common7\IDE\PrivateAssemblies**:

   - Microsoft.VisualStudio.Uml.dll

   - Microsoft.VisualStudio.TeamArchitect.ModelStore.Dsl.dll

     Si desea leer diagramas en la aplicación, también podría necesitar estas referencias:

   - Microsoft.VisualStudio.TeamArchitect.ActivityDesigner.Dsl.dll

   - Microsoft.VisualStudio.TeamArchitect.ComponentDesigner.Dsl.dll

   - Microsoft.VisualStudio.TeamArchitect.LogicalClassDesigner.Dsl.dll

   - Microsoft.VisualStudio.TeamArchitect.SequenceDesigner.Dsl.dll

   - Microsoft.VisualStudio.TeamArchitect.UseCase.Dsl.dll

## <a name="see-also"></a>Vea también
 [Programar con la API de UML](../modeling/programming-with-the-uml-api.md) [ampliar modelos y diagramas UML](../modeling/extend-uml-models-and-diagrams.md)
