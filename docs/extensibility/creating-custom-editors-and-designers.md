---
title: Crear editores y diseñadores personalizados | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7a6cb0d70566eaabb2ba37cb209041e03684c958
ms.sourcegitcommit: 97623fd6190c43fed0d2ee7af92b01c375282622
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73568891"
---
# <a name="create-custom-editors-and-designers"></a>Crear editores y diseñadores personalizados

El entorno de desarrollo integrado (IDE) de Visual Studio puede hospedar distintos tipos de editor:

- Editor principal de Visual Studio

- Editores personalizados

- Editores externos

- Diseñadores

La siguiente información le ayuda a elegir el tipo de editor que necesita.

## <a name="types-of-editor"></a>Tipos de editor

Para obtener información sobre el editor principal de Visual Studio, vea [extender el editor y los servicios de lenguaje](../extensibility/extending-the-editor-and-language-services.md).

### <a name="custom-editors"></a>Editores personalizados
 Un editor personalizado es aquel que está diseñado para funcionar en circunstancias especializadas. Por ejemplo, puede crear un editor cuya función sea leer y escribir datos en un repositorio específico, como un servidor de Microsoft Exchange. Elija un editor personalizado si desea un editor que funcione solo con el tipo de proyecto o si desea un editor que tenga solo algunos comandos concretos. Tenga en cuenta, sin embargo, que los usuarios no podrán usar un editor personalizado para editar proyectos de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] estándar.

 Un editor personalizado puede usar un generador de editores y agregar información sobre el editor al registro. Sin embargo, el tipo de proyecto asociado al editor personalizado puede crear instancias del editor personalizado de otras maneras.

 Un editor personalizado puede usar la activación en contexto o la incrustación simplificada para implementar una vista.

### <a name="external-editors"></a>Editores externos
 Los editores externos son editores que no están integrados en Visual Studio, como Microsoft Word, Bloc de notas o Microsoft FrontPage. Puede llamar a este tipo de editor si, por ejemplo, va a pasar texto a él desde el VSPackage. Los editores externos se registran y se pueden usar fuera de Visual Studio. Cuando se llama a un editor externo y se puede incrustar en una ventana host, aparece en una ventana del IDE. En caso contrario, el IDE crea una ventana independiente para él.

 El método <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> establece la prioridad del documento mediante la enumeración <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>. Si se especifica el valor `DP_External`, un editor externo puede abrir el archivo.

## <a name="editor-design-decisions"></a>Decisiones de diseño del editor
 Las siguientes preguntas de diseño le ayudarán a elegir el tipo de editor que mejor se adapte a su aplicación:

- ¿La aplicación guardará sus datos en archivos o no? Si va a guardar sus datos en archivos, ¿estarán en un formato personalizado o estándar?

   Si usa un formato de archivo estándar, otros tipos de proyectos además del proyecto podrán abrir y leer datos en ellos. Sin embargo, si usa un formato de archivo personalizado, solo el tipo de proyecto podrá abrir y leer datos en ellos.

   Si el proyecto utiliza archivos, debe personalizar el editor estándar. Si el proyecto no usa archivos, sino que usa elementos en una base de datos u otro repositorio, debe crear un editor personalizado.

- ¿El editor necesita hospedar controles ActiveX?

   Si el editor hospeda controles ActiveX, implemente un editor de activación en contexto, como se describe en [activación en contexto](/visualstudio/misc/in-place-activation?view=vs-2015). Si no hospeda controles ActiveX, use un editor de inserción simplificado o personalice el editor predeterminado de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

- ¿El editor admite varias vistas? Debe admitir varias vistas si desea que las vistas del editor sean visibles al mismo tiempo que el editor predeterminado.

   Si el editor necesita admitir varias vistas, los datos de documento y los objetos de vista de documento para el editor deben ser objetos independientes. Para obtener más información, vea [compatibilidad con varias vistas de documentos](../extensibility/supporting-multiple-document-views.md).

   Si el editor admite varias vistas, ¿tiene previsto usar la implementación de búfer de texto del editor de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Core (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto) para el objeto de datos del documento? Es decir, ¿desea admitir la vista del editor en paralelo con el editor de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Core? La capacidad de hacerlo es la base del diseñador de formularios.

- Si necesita hospedar un editor externo, ¿se puede incrustar el editor dentro de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]?

   Si se puede incrustar, debe crear una ventana host para el editor externo y, a continuación, llamar al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> y establecer el valor de la enumeración <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> en `DP_External`. Si no se puede incrustar el editor, el IDE creará automáticamente una ventana independiente para él.

## <a name="in-this-section"></a>En esta sección

[Tutorial: crear un editor personalizado](../extensibility/walkthrough-creating-a-custom-editor.md)\
Explica cómo crear un editor personalizado.

[Tutorial: agregar características a un editor personalizado](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)\
Explica cómo agregar características a un editor personalizado.

[Inicialización del diseñador y configuración de metadatos](../extensibility/designer-initialization-and-metadata-configuration.md)\
Explica cómo inicializar un diseñador.

[Proporcione soporte para deshacer para diseñadores](../extensibility/supplying-undo-support-to-designers.md)\
Explica cómo proporcionar compatibilidad con la deshacer para los diseñadores.

[Colores de la sintaxis en editores personalizados](../extensibility/syntax-coloring-in-custom-editors.md)\
Explica la diferencia entre el color de la sintaxis en el editor principal y en los editores personalizados.

[Datos de documento y vista de documento en editores personalizados](../extensibility/document-data-and-document-view-in-custom-editors.md)\
Explica cómo implementar datos de documento y vistas de documento en editores personalizados.

## <a name="related-sections"></a>Secciones relacionadas

[Interfaces heredadas en el editor](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015)\
Explica cómo obtener acceso al editor principal por medio de la API heredada.

[Desarrollo de un servicio de lenguaje heredado](../extensibility/internals/developing-a-legacy-language-service.md)\
Explica cómo implementar un servicio de lenguaje.

[Extender otras partes de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)\
Explica cómo crear elementos de interfaz de usuario que coincidan con el resto de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>