---
title: 'Diagramas de casos de uso de UML: referencia | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.usecasediagram.toolbox
- vs.teamarch.usecasediagram.diagram
- vs.teamarch.UMLModelExplorer.usecasediagram
helpviewer_keywords:
- diagrams - modeling, use case
- UML, use case diagrams
- diagrams - modeling, UML use case
- use case diagrams
- UML diagrams, use case
ms.assetid: aa15772b-eb67-4366-b145-b559112817df
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cbea61c2a26b1dc81487365ef8fc3f320ac95943
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657305"
---
# <a name="uml-use-case-diagrams-reference"></a>Diagramas de casos de uso de UML: Referencia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En Visual Studio, un *Diagrama de casos de uso* resume quién usa la aplicación o el sistema y lo que puede hacer con él. Para crear un diagrama de casos de uso de UML, en el menú **arquitectura** , haga clic en **nuevo diagrama de UML o de capas**.

 Un diagrama de casos de uso actúa como foco en la descripción de los requisitos del usuario. En él se describen las relaciones entre los requisitos, los usuarios y los componentes principales. Los requisitos no se describen en detalle, ya que esto puede hacerse en otros diagramas o en documentos que pueden vincularse a cada caso de uso. Para obtener información sobre el modo en que los diagramas de casos de uso pueden ayudarle a entender, analizar y comunicar las necesidades de los usuarios, vea [requisitos de usuario de modelo](../modeling/model-user-requirements.md).

 Para ver qué versiones de Visual Studio admiten esta característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> En este tema se describen los elementos que están disponibles en los diagramas de casos de uso. Para obtener más información sobre cómo dibujar diagramas de casos de uso, vea [diagramas de casos de uso de UML: instrucciones](../modeling/uml-use-case-diagrams-guidelines.md). Para obtener más información sobre cómo crear y dibujar diagramas de modelado, vea [Editar modelos y diagramas UML](../modeling/edit-uml-models-and-diagrams.md).

## <a name="reading-use-case-diagrams"></a>Lectura de diagramas de casos de uso
 En las tablas de las secciones siguientes se describen los elementos disponibles en un diagrama de casos de uso y sus propiedades principales. Para obtener una lista completa de las propiedades, vea [propiedades de los elementos de los diagramas de casos de uso de UML](../modeling/properties-of-elements-on-uml-use-case-diagrams.md).

### <a name="actors-use-cases-and-subsystems"></a>Actores, casos de uso y subsistemas
 ![Elementos de un diagrama de casos de uso](../modeling/media/uml-ucovactor.png "UML_UCOvActor")

|**Forma**|**Element**|**Descripción y propiedades principales**|
|---------------|-----------------|-----------------------------------------|
|1|**Agente**|Representa un usuario, organización o sistema externo que interactúa con la aplicación o el sistema. Un actor es una clase de tipo.<br /><br /> -   **ruta de acceso** de la imagen: la ruta de acceso del archivo de una imagen que se debe usar en lugar del icono de actor predeterminado. El icono debe ser un archivo de recursos incluido en el proyecto de Visual Studio.|
|2|**Caso de uso**|Representa las acciones realizadas por uno o varios actores para conseguir un objetivo determinado. Un caso de uso es una clase de tipo.<br /><br /> -   **asuntos** : el subsistema en el que aparece el caso de uso.|
|3|**Asociación**|Indica que un actor forma parte de un caso de uso.|
|4|**Subsistema o componente**|El sistema o la aplicación en los que se está trabajando (o parte de él). Puede ser cualquier cosa, desde una red de gran tamaño hasta una única clase de una aplicación.<br /><br /> Los casos de uso admitidos por un sistema o componente aparecen dentro de su rectángulo. Para aclarar el ámbito del sistema, puede resultar útil mostrar algunos casos de uso fuera del rectángulo.<br /><br /> El tipo de un subsistema de un diagrama de casos de uso es básicamente el mismo que el de un componente de un diagrama de componentes.<br /><br /> **se crea una instancia de -    indirectamente** ; si es false, el sistema en ejecución tiene uno o más objetos que se corresponden directamente con este subsistema. Si es true, el subsistema es una construcción del diseño que solo aparece en el sistema en ejecución a través de la creación de instancias de los elementos que lo conforman.|

### <a name="structuring-use-cases"></a>Estructuración de casos de uso
 ![Casos de uso con include, Extend y generalización](../modeling/media/uml-ucovstructure.png "UML_UCOvStructure")

|Forma|**Element**|Descripción|
|-----------|-----------------|-----------------|
|5|**Inclui**|Un caso de uso de inclusión llama o invoca al caso de uso incluido. La inclusión se usa para mostrar cómo se divide un caso de uso en pasos más pequeños. El caso de uso incluido se encuentra en el extremo con la punta de flecha.<br /><br /> Tenga en cuenta que el diagrama no muestra el orden de los pasos. Puede usar un diagrama de actividades, un diagrama de secuencia u otro documento para describir estos detalles.|
|6|**Allá**|Un caso de uso de extensión agrega objetivos y pasos al caso de uso extendido. Las extensiones solamente funcionan en ciertas condiciones. El caso de uso extendido se encuentra en el extremo con la punta de flecha.<br /><br /> Tenga en cuenta que en el diagrama no se muestran las circunstancias exactas en las que se aplica la extensión; puede registrar esas circunstancias en un comentario o en otro documento.|
|7|**Herencia**|Relaciona un elemento especializado y un elemento generalizado. El elemento generalizado se encuentra en el extremo con la punta de flecha.<br /><br /> Un caso de uso especializado hereda los objetivos y actores de su generalización y puede agregar objetivos más específicos y los pasos para llevarlos a cabo.<br /><br /> Un actor especializado hereda los casos de uso, los atributos y las asociaciones de su generalización y puede agregar más elementos.|
|8|**Pendiente**|Indica que el diseño del origen depende del diseño del destino.|
|9|**Comentario**|Se usa para agregar notas generales al diagrama.|
|10|**Artefacto**|Un artefacto proporciona un vínculo a otro diagrama o documento y se crea arrastrando un archivo desde el Explorador de soluciones. Se puede vincular mediante una relación de dependencia a otro elemento del diagrama. Un artefacto se usa normalmente para vincular un caso de uso a un diagrama de secuencia, una página de OneNote, un documento de Word o una presentación de PowerPoint que describe el caso de uso en detalle. El documento puede ser un elemento de la solución de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] o un documento en una ubicación compartida, como un sitio de SharePoint.<br /><br /> -   **hipervínculo**. dirección URL o ruta de acceso del diagrama o documento.<br /><br /> Haga doble clic en un artefacto para abrir la página web o el archivo al que está vinculado.|
|11 (no se muestra)|**Paquetes**|Los casos de uso, actores y subsistemas pueden incluirse dentro de paquetes. Las formas paquete no aparecen en el diagrama, pero puede establecer la propiedad **LinkedPackage** del diagrama. Los elementos que cree posteriormente en el diagrama se colocarán dentro del paquete. Para obtener más información, vea [definir paquetes y espacios de nombres](../modeling/define-packages-and-namespaces.md).|

## <a name="see-also"></a>Vea también
 [Diagramas de casos de uso de UML: instrucciones](../modeling/uml-use-case-diagrams-guidelines.md) [Editar modelos y diagramas](../modeling/edit-uml-models-and-diagrams.md) UML [diagramas de secuencia UML:](../modeling/uml-sequence-diagrams-reference.md) referencia [diagramas de clases de UML: referencia](../modeling/uml-class-diagrams-reference.md) [diagramas de componentes](../modeling/uml-component-diagrams-reference.md) de UML: referencia [diagramas de componentes de UML: referencia](../modeling/uml-component-diagrams-reference.md)
