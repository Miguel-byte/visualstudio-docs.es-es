---
title: Vincular un caso de uso a documentos y diagramas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.usecasediagram.artifact.properties.artifactlink
- vs.teamarch.usecasediagram.artifact
helpviewer_keywords:
- use case diagrams
ms.assetid: 4c9ed205-9197-4ed5-b39d-ddfa24a0a421
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c713759a8ea75eed3048469327f962668efa4f70
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657641"
---
# <a name="link-a-use-case-to-documents-and-diagrams"></a>Vincular un caso de uso a documentos y diagramas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede vincular un caso de uso de un diagrama de casos de uso a otro diagrama o documento. Por ejemplo, puede vincular el caso de uso a los siguientes documentos y diagramas:

- Un diagrama de secuencias que muestra cómo se realizan los objetivos del caso de uso mediante las interacciones entre los usuarios y el sistema o sus componentes principales.

- Un diagrama de actividades que muestra las acciones detalladas de los usuarios y el sistema o sus componentes principales mientras llevan a cabo el caso de uso.

- Una página o párrafo de OneNote que describe el caso de uso con detalle.

- Un documento de Word o una presentación de PowerPoint que describe el caso de uso con detalle. Puede conservar estos documentos en la solución o en una ubicación accesible para el equipo, por ejemplo, un sitio de SharePoint.

  Para vincular un caso de uso a un documento, cree un artefacto en el diagrama de casos de uso y conecte el caso de uso con el artefacto. En las propiedades del artefacto, establezca la ruta de acceso de archivo del otro diagrama o documento. Al hacer doble clic en el artefacto, se abrirá el otro diagrama o documento.

  Puede conectar tantos artefactos como desee a cada caso de uso. También puede vincular los artefactos a otros tipos de elementos en un diagrama de casos de uso.

### <a name="to-open-a-document-associated-with-an-artifact"></a>Para abrir un documento asociado a un artefacto

- En el diagrama de casos de uso, haga doble clic en la forma del artefacto.

     Se abrirá el documento asociado.

### <a name="to-link-a-use-case-to-a-diagram-or-file-in-the-same-solution"></a>Para vincular un caso de uso a un diagrama o a un archivo en la misma solución

1. Dibuje un diagrama, por ejemplo un diagrama de secuencia o de actividades, para mostrar un escenario del caso de uso.

2. Vuelva al diagrama de casos de uso.

3. Arrastre el diagrama o el archivo desde el Explorador de soluciones a una zona vacía del diagrama de casos de uso.

4. Conecte desde el artefacto al caso de uso mediante una **dependencia**.

### <a name="to-link-to-a-solution-file-such-as-a-word-document-or-powerpoint-presentation"></a>Para vincular a un archivo de solución, por ejemplo a un documento de Word o a una presentación de PowerPoint

1. Agregue el documento a la solución.

    1. Mueva el documento de Word a la misma carpeta de Windows que la solución.

    2. En Explorador de soluciones, haga clic con el botón secundario en la solución, seleccione **Agregar**y, a continuación, haga clic en **elemento existente**.

    3. Navegue hasta el documento de Word y haga clic en **Agregar**.

         El documento de Word aparece en una carpeta de la solución en el Explorador de soluciones.

2. Arrastre el documento de Word desde el Explorador de soluciones a una parte en blanco del diagrama de casos de uso.

     Aparece un nuevo artefacto.

3. Conecte desde el artefacto al caso de uso mediante una **dependencia**.

### <a name="to-link-to-a-shared-document-onenote-element-or-web-page"></a>Para vincular un documento compartido, elemento de OneNote o página web

1. Obtenga la dirección URL del elemento compartido. Esto puede ser, por ejemplo, una ruta de acceso de archivo de red que empieza por ' \\ \\ ', o una página web o una dirección URL de SharePoint que empieza por ' http://', o un vínculo a una sección, página o párrafo de OneNote que empieza por ' OneNote: '.

2. En el cuadro de herramientas, haga clic en **artefacto** y, a continuación, haga clic en el diagrama de casos de uso.

3. Con el nuevo artefacto seleccionado, escriba o pegue la dirección URL en la propiedad de **hipervínculo** .

    > [!NOTE]
    > Si desea proporcionar una ruta de acceso de archivo, es mejor elegir un archivo en un área de trabajo común (empezando por ' \\ \\ ') o un archivo dentro de la solución de Visual Studio. Esto garantizará que la ruta de acceso del archivo seguirá siendo válida en el sistema de otro miembro del equipo o si se mueve la solución. Para agregar un documento, como un documento de Word, a la solución, haga clic con el botón secundario en la solución en Explorador de soluciones, seleccione **Agregar** y, a continuación, haga clic en **elemento existente**.

## <a name="see-also"></a>Vea también
 [Diagramas de casos de uso de UML: referencia](../modeling/uml-use-case-diagrams-reference.md) [diagramas de casos de uso de UML: instrucciones](../modeling/uml-use-case-diagrams-guidelines.md) [Editar modelos y diagramas UML](../modeling/edit-uml-models-and-diagrams.md) [crear modelos para la aplicación](../modeling/create-models-for-your-app.md)
