---
title: 'Tutorial: agregar características a un editor personalizado | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5fa926b21171c3e09b5a0f4d74e9415da090bf2f
ms.sourcegitcommit: 97623fd6190c43fed0d2ee7af92b01c375282622
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73569077"
---
# <a name="walkthrough-add-features-to-a-custom-editor"></a>Tutorial: agregar características a un editor personalizado
Después de crear un editor personalizado, puede agregarle más características.

## <a name="to-create-an-editor-for-a-vspackage"></a>Para crear un editor para un VSPackage

1. Cree un editor personalizado mediante la plantilla de proyecto de paquete de Visual Studio.

     Para obtener más información, vea [Tutorial: crear un editor personalizado](../extensibility/walkthrough-creating-a-custom-editor.md).

2. Decida si desea que el editor admita una sola vista o varias vistas.

     Un editor que admite el comando **nueva ventana** , o tiene la vista de formulario y la vista de código, requiere objetos de datos de documento independientes y objetos de vista de documento. En un editor que admite una sola vista, el objeto de datos del documento y el objeto de vista de documento se pueden implementar en el mismo objeto.

     Para obtener un ejemplo de varias vistas, vea [compatibilidad con varias vistas de documentos](../extensibility/supporting-multiple-document-views.md).

3. Implemente un generador de editores mediante la configuración de la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>.

     Para obtener más información, consulte [generadores de editores](../extensibility/editor-factories.md).

4. Decida si desea que el editor use la activación en contexto o la incrustación simplificada para administrar la ventana de objeto de vista de documento.

     Una ventana del editor de incrustación simplificada hospeda una vista de documento estándar, mientras que una ventana del editor de activación en contexto hospeda un control ActiveX u otro objeto activo como su vista de documento. Para obtener más información, consulte [incrustación simplificada](../extensibility/simplified-embedding.md) y [activación en contexto](/visualstudio/misc/in-place-activation?view=vs-2015).

5. Implemente la interfaz <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> para controlar los comandos.

6. Proporcionar persistencia de documentos y respuesta a cambios de archivos externos:

    1. Para conservar el archivo, implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> y <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> en el objeto de datos de documento del editor.

    2. Para responder a los cambios en los archivos externos, implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> en el objeto de datos de documento del editor.

        > [!NOTE]
        > Llame a `QueryService` en <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> para obtener un puntero a `IVsFileChangeEx`.

7. Coordinar los eventos de edición de documentos con control de código fuente. Siga estos pasos:

    1. Obtiene un puntero a `IVsQueryEditQuerySave2` llamando a `QueryService` en <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>.

    2. Cuando se produzca el primer evento de edición, llame al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>.

         Este método solicita al usuario que desproteja el archivo si aún no está desprotegido. Asegúrese de administrar la condición "archivo no desprotegido" para evitar errores.

    3. Del mismo modo, antes de guardar el archivo, llame al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>.

         Este método solicita al usuario que guarde el archivo si no se ha guardado o si ha cambiado desde la última vez que se guardó.

8. Habilite la ventana **propiedades** para mostrar las propiedades del texto seleccionado en el editor. Siga estos pasos:

    1. Llame a <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> cada vez que cambie la selección de texto, pasando su implementación de <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>.

    2. Llame a `QueryService` en <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> servicio para obtener un puntero a <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.

9. Permite a los usuarios arrastrar y colocar elementos entre el editor y el **cuadro de herramientas**, o entre editores externos (como Microsoft Word) y el cuadro de **herramientas**. Siga estos pasos:

    1. Implemente `IDropTarget` en el editor para alertar al IDE de que el editor es un destino de colocación.

    2. Implemente la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> en la vista para que el editor pueda habilitar y deshabilitar elementos en el **cuadro de herramientas**.

    3. Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> y llame a `QueryService` en el servicio <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> para obtener un puntero a las interfaces <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>.

         Estos pasos permiten que el VSPackage agregue nuevos elementos al **cuadro de herramientas**.

10. Decida si desea cualquier otra característica opcional para el editor.

    - Si desea que el editor admita comandos de búsqueda y reemplazo, implemente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>.

    - Si desea utilizar una ventana de herramientas de esquema del documento en el editor, implemente `IVsDocOutlineProvider`.

    - Si desea usar una barra de estado en el editor, implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> y llame a `QueryService` para <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> para obtener un puntero a `IVsStatusBar`.

         Por ejemplo, un editor puede mostrar información de línea/columna, el modo de selección (secuencia/cuadro) y el modo de inserción (inserción/sobretachado).

    - Si desea que el editor admita el comando `Undo`, el método recomendado es usar el modelo de administrador de deshacer OLE. Como alternativa, puede hacer que el editor controle el comando de `Undo` directamente.

11. Cree información del registro, incluidos los GUID del VSPackage, los menús, el editor y otras características.

     A continuación se muestra un ejemplo genérico de código que se incluiría en el script del archivo *. RGS* para mostrar cómo registrar correctamente un editor.

    ```csharp
    NoRemove Editors
    {
          ForceRemove {...guidEditor...} = s 'RTF Editor'
          {
             val Package = s '{...guidVsPackage...}'
             ForceRemove Extensions
             {
                val rtf = d 50
             }
          }
    }
    NoRemove Menus
    {
          val {...guidVsPackage...} = s ',203,11'
    }
    ```

12. Implementar la compatibilidad con la ayuda contextual.

     Este paso le permite proporcionar ayuda F1 y compatibilidad con ventanas de ayuda dinámica para los elementos del editor. Para obtener más información, vea [Cómo: proporcionar contexto para editores](/visualstudio/extensibility/how-to-provide-context-for-editors?view=vs-2015).

13. Exponga un modelo de objetos de automatización desde el editor implementando la interfaz `IDispatch`.

     Para obtener más información, consulta [Contributing to the Automation Model](../extensibility/internals/contributing-to-the-automation-model.md).

## <a name="robust-programming"></a>Programación sólida

- La instancia del editor se crea cuando el IDE llama al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>. Si el editor admite varias vistas, `CreateEditorInstance` crea los datos del documento y los objetos de la vista del documento. Si el objeto de datos del documento ya está abierto, se pasa un valor `punkDocDataExisting` no NULL a `IVsEditorFactory::CreateEditorInstance`. La implementación del generador de editores debe determinar si un objeto de datos de documento existente es compatible mediante la consulta de las interfaces adecuadas en él. Para obtener más información, vea [admitir varias vistas de documentos](../extensibility/supporting-multiple-document-views.md).

- Si utiliza el enfoque de incrustación simplificado, implemente la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>.

- Si decide usar la activación en contexto, implemente las interfaces siguientes:

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>

   <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>

  > [!NOTE]
  > La interfaz de `IOleInPlaceComponent` se utiliza para evitar la combinación de menús de OLE 2.

   La implementación de `IOleCommandTarget` controla comandos como **cortar**, **copiar**y **pegar**. Al implementar `IOleCommandTarget`, decida si el editor requiere su propio archivo *. Vsct* para definir su propia estructura de menú de comandos o si puede implementar comandos estándar definidos por [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Normalmente, los editores usan y extienden los menús del IDE y definen sus propias barras de herramientas. Sin embargo, a menudo es necesario que un editor defina sus propios comandos específicos además de usar el conjunto de comandos estándar del IDE. El editor debe declarar los comandos estándar que usa y, a continuación, definir los comandos nuevos, los menús contextuales, los menús de nivel superior y las barras de herramientas en un archivo *. Vsct* . Si crea un editor de activación en contexto, implemente <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> y defina los menús y las barras de herramientas del editor en un archivo *. Vsct* en lugar de usar la combinación de menús de OLE 2.

- Para evitar la amontonación del comando de menú en la interfaz de usuario, debe usar los comandos existentes en el IDE antes de inventar nuevos comandos. Los comandos compartidos se definen en *SharedCmdDef. Vsct* y *ShellCmdDef. Vsct*. Estos archivos se instalan de forma predeterminada en el subdirectorio VisualStudioIntegration\Common\Inc de la instalación de [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)].

- `ISelectionContainer` puede expresar selecciones únicas y múltiples. Cada objeto seleccionado se implementa como un objeto `IDispatch`.

- El IDE implementa `IOleUndoManager` como un servicio accesible desde un <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> o como un objeto del que se pueden crear instancias a través de <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>. El editor implementa la interfaz `IOleUndoUnit` para cada acción de `Undo`.

- Hay dos lugares en los que un editor personalizado puede exponer objetos de automatización:

  - `Document.Object`

  - `Window.Object`

## <a name="see-also"></a>Vea también

- [Contribuir al modelo de automatización](../extensibility/internals/contributing-to-the-automation-model.md)