---
title: Empezar a programar personalizaciones de nivel de documento para Word
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word solutions in Visual Studio
- Word projects [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2b2872ca6496444cbb3878dc39800a8661400a76
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62971802"
---
# <a name="get-started-programming-document-level-customizations-for-word"></a>Empezar a programar personalizaciones de nivel de documento para Word
  Si acaba de empezar a crear personalizaciones de nivel de documento para Microsoft Office Word mediante Visual Studio, aquí es lo que necesita saber.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

## <a name="understand-how-document-level-customizations-for-word-work"></a>Comprender cómo personalizaciones de documentos para el trabajo de Word
 Cada personalización de Word que cree se basa en un único documento. Para empezar a usar la personalización, el usuario final abre el documento o se crea a partir de una plantilla de Word. Los eventos en el documento, por ejemplo, mueva el cursor a áreas específicas o hacer clic en botones y elementos de menú, pueden llamar a métodos de control de eventos en el ensamblado. Cuando se cierra el documento, las características proporcionadas por la personalización ya no están disponibles en Word.

 Para obtener más información, consulte [arquitectura de las personalizaciones de nivel de documento](../vsto/architecture-of-document-level-customizations.md).

## <a name="create-document-level-projects-for-word"></a>Crear proyectos de nivel de documento para Word
 Para crear una personalización de nivel de documento para Word, use la plantilla de proyecto de documento de Word o plantilla de Word en el **nuevo proyecto** cuadro de diálogo. Estas plantillas incluyen las referencias de ensamblado necesarias y los archivos del proyecto.

 Para obtener más información acerca de cómo crear un proyecto de nivel de documento para Word, consulte [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Para obtener más información acerca de las plantillas de proyecto, vea [Introducción a las plantillas de proyecto de Office](../vsto/office-project-templates-overview.md).

## <a name="program-word-documents-by-using-host-items-host-controls"></a>Documentos de Word del programa mediante el uso de elementos y controles host
 *Elementos host* y *controles host* son clases que proporcionan el modelo de programación para las personalizaciones de nivel de documento.

 Los elementos host proporcionan un punto de entrada para el código, y puede también actúan como contenedores para los controles host y controles de formularios Windows Forms. En proyectos de nivel de documento para Word, se representa el elemento host mediante la `ThisDocument` clase.

 Los controles host se basan en objetos nativos de Word, como los controles de contenido, marcadores y los nodos XML. Los controles host proporcionan una funcionalidad similar a los objetos nativos de Word, pero también tienen nuevos eventos, compatibilidad con el diseñador y capacidad de enlace de datos. Aparecen como objetos de primera clase en el código del proyecto y en IntelliSense, lo que resulta más fácil hacer referencia a objetos específicos directamente en el código sin tener que navegar por el modelo de objetos de Word.

 Para obtener más información, vea los temas siguientes:

- [Programar personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md)

- [Automatizar Word usando objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)

- [Elementos host y la información general sobre controles de host](../vsto/host-items-and-host-controls-overview.md)

## <a name="customize-the-user-interface-of-word"></a>Personalizar la interfaz de usuario de Word
 La mayoría de las soluciones de Microsoft Office modifican la interfaz de usuario (UI) de la aplicación de Office para ofrecer alguna forma para que los usuarios interactuar con la solución. Hay muchas maneras en que puede modificar la interfaz de usuario de Word mediante una personalización de nivel de documento. Por ejemplo, puede agregar controles a la cinta de opciones, y puede mostrar un panel de acciones. Para obtener más información, consulte [personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md).

 También puede abrir el documento que está asociado directamente al proyecto en Visual Studio. Cuando el documento está abierto en Visual Studio, puede modificar el documento mediante el uso de la interfaz de usuario de Word. También puede usar el documento como una superficie de diseño, lo que permite arrastrar los controles. Para obtener más información, consulte [proyectos de Office en el entorno de Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="bind-controls-to-data"></a>Enlazar controles a datos
 Los controles de contenido y la <xref:Microsoft.Office.Tools.Word.Bookmark> control están en la lista de controles que puede arrastrar desde el **orígenes de datos** ventana. Agregar controles de contenido y marcadores de esta manera automáticamente, enlaza al origen de datos que configuró mediante el uso de la ventana. Sin escribir ningún código, puede mostrar datos de bases de datos, servicios y objetos de negocios. Para obtener más información, consulte [enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md).

## <a name="next-steps"></a>Pasos siguientes
 Para obtener información sobre cómo crear una personalización de nivel de documento para Word, consulte [Tutorial: Crear la primera personalización de nivel de documento para Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md). Este tutorial presentan las herramientas de desarrollo de Office en Visual Studio y el modelo de programación para las personalizaciones de nivel de documento de Word.

 Para obtener una lista de temas que le guiarán a través de algunas de las tareas comunes en proyectos de Word, consulte [tareas comunes de programación de Office](../vsto/common-tasks-in-office-programming.md).

## <a name="see-also"></a>Vea también
- [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Programar personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md)
- [Soluciones de Word](../vsto/word-solutions.md)
- [Tutorial: Crear la primera personalización de nivel de documento para Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)
- [Tutoriales para Word](../vsto/walkthroughs-using-word.md)
- [Información general sobre el modelo de objetos de Word](../vsto/word-object-model-overview.md)
- [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)
