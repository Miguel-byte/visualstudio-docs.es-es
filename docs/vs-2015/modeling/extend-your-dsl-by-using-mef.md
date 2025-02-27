---
title: Extender el DSL mediante MEF | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 3e7be79a-53ab-4d79-863a-bef8d27839bd
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d3257acde8d3c62aca64e3401ec18134601973e5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669647"
---
# <a name="extend-your-dsl-by-using-mef"></a>Ampliar DSL mediante MEF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede extender el lenguaje específico del dominio (DSL) mediante Managed Extensibility Framework (MEF). Usted u otros desarrolladores podrán escribir extensiones para DSL sin cambiar la definición de DSL y el código de programa. Tales extensiones incluyen comandos de menú, controladores de arrastrar y colocar, y validación. Los usuarios podrán instalar el DSL y, a continuación, instalar las extensiones para él de forma opcional.

 Además, al habilitar MEF en el DSL, puede ser más fácil escribir algunas de las características del DSL, incluso si están todas compiladas junto con el DSL.

 Para obtener más información sobre MEF, vea [Managed Extensibility Framework (MEF)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).

### <a name="to-enable-your-dsl-to-be-extended-by-mef"></a>Para habilitar la extensión de DSL mediante MEF

1. Cree una nueva carpeta denominada **MefExtension** dentro del proyecto **DslPackage** . Agregue los siguientes archivos:

    Nombre de archivo: `CommandExtensionVSCT.tt`

   > [!IMPORTANT]
   > Establezca el GUID en este archivo para que sea el mismo que el GUID CommandSetId definido en DslPackage\GeneratedCode\Constants.tt

   ```
   <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
   <#
   // CmdSet Guid must be defined before master template is included
   // This Guid must be kept synchronized with the CommandSetId Guid in Constants.tt
   Guid guidCmdSet = new Guid ("00000000-0000-0000-0000-000000000000");
   string menuidCommandsExtensionBaseId="0x4000";
   #>
   <#@ include file="DslPackage\CommandExtensionVSCT.tt" #>
   ```

    Nombre de archivo: `CommandExtensionRegistrar.tt`

   ```
   <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
   <#@ include file="DslPackage\CommandExtensionRegistrar.tt" #>
   ```

    Nombre de archivo: `ValidationExtensionEnablement.tt`

   ```
   <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
   <#@ include file="DslPackage\ValidationExtensionEnablement.tt" #>
   ```

    Nombre de archivo: `ValidationExtensionRegistrar.tt`

    Si agrega este archivo, debe habilitar la validación en DSL mediante al menos uno de los modificadores de **EditorValidation** en el explorador de DSL.

   ```
   <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
   <#@ include file="DslPackage\ValidationExtensionRegistrar.tt" #>
   ```

    Nombre de archivo: `PackageExtensionEnablement.tt`

   ```
   <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
   <#@ include file="DslPackage\PackageExtensionEnablement.tt" #>
   ```

2. Cree una nueva carpeta denominada **MefExtension** dentro del proyecto **DSL** . Agregue los siguientes archivos:

    Nombre de archivo: `DesignerExtensionMetaDataAttribute.tt`

   ```
   <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
   <#@ include file="Dsl\DesignerExtensionMetadataAttribute.tt" #>
   ```

    Nombre de archivo: `GestureExtensionEnablement.tt`

   ```
   <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
   <#@ include file="Dsl\GestureExtensionEnablement.tt" #>
   ```

    Nombre de archivo: `GestureExtensionController.tt`

   ```
   <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
   <#@ include file="Dsl\GestureExtensionController.tt" #>
   ```

3. Agregue la siguiente línea al archivo existente denominado **DslPackage\Commands.Vsct**:

   ```
   <Include href="MefExtension\CommandExtensionVSCT.vsct"/>
   ```

    Inserte la línea después de la Directiva de `<Include>` existente.

4. `Open DslDefinition.dsl.`

5. En DSL Explorer (explorador de DSL), seleccione **Editor\Validation**.

6. En el ventana Propiedades, asegúrese de que al menos una de las propiedades denominadas **use...** es `true`.

7. En la barra de herramientas Explorador de soluciones, haga clic en **transformar todas las plantillas**.

    Los archivos subsidiarios aparecen debajo de cada uno de los archivos agregados.

8. Compile y ejecute la solución para comprobar que sigue funcionando.

   El DSL es ahora compatible con MEF. Los comandos de menú, los controladores de gestos y las restricciones de validación se pueden escribir como extensiones de MEF. Puede escribir estas extensiones en la solución DSL junto con otro código personalizado. Además, usted u otros desarrolladores pueden escribir extensiones de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] independientes que amplían el DSL.

## <a name="creating-an-extension-for-a-mef-enabled-dsl"></a>Crear una extensión para un DSL habilitado para MEF
 Si tiene acceso a un DSL habilitado para MEF creado por usted mismo o por otro usuario, puede escribir extensiones para él. Las extensiones se pueden usar para agregar comandos de menú, controladores de gestos o restricciones de validación. Para crear estas extensiones, se usa una solución de extensión de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (VSIX). La solución tiene dos partes: un proyecto de biblioteca de clases que compila el ensamblado de código y un proyecto VSIX que empaqueta el ensamblado.

#### <a name="to-create-a-dsl-extension-vsix"></a>Para crear un VSIX de extensión DSL

1. Cree un nuevo proyecto de biblioteca de clases. Para ello, en el cuadro de diálogo **nuevo proyecto** , seleccione **Visual Basic** o **Visual C#**  y, a continuación, seleccione **biblioteca de clases**.

2. En el nuevo proyecto de biblioteca de clases, agregue una referencia al ensamblado de DSL.

   - Normalmente, este ensamblado tiene un nombre que termina con ". DSL. dll ".

   - Si tiene acceso al proyecto DSL, puede encontrar el archivo de ensamblado en el directorio **dsl \\bin \\ \***

   - Si tiene acceso al archivo VSIX de DSL, puede encontrar el ensamblado cambiando la extensión de nombre de archivo del archivo VSIX a ". zip". Descomprima el archivo. zip.

3. Agregue referencias a los siguientes ensamblados .NET:

   - Microsoft. VisualStudio. Modeling. SDK. 11.0. dll

   - Microsoft. VisualStudio. Modeling. SDK. Diagrams. 11.0. dll

   - Microsoft. VisualStudio. Modeling. SDK. Shell. 11.0. dll

   - System.ComponentModel.Composition.dll

   - System.Windows.Forms.dll

4. Cree un proyecto VSIX en la misma solución. Para ello, en el cuadro de diálogo **nuevo proyecto** , expanda **Visual Basic** o **Visual C#** , haga clic en **extensibilidad**y, a continuación, seleccione **proyecto de VSIX**.

5. En Explorador de soluciones, haga clic con el botón secundario en el Proyecto VSIX y luego haga clic en **establecer como proyecto de inicio**.

6. En el nuevo proyecto, Abra **source. Extension. vsixmanifest**.

7. Haga clic en **agregar contenido**. En el cuadro de diálogo, establezca **tipo de contenido** en **componente MEF**y **proyecto de origen** en el proyecto de biblioteca de clases.

8. Agregue una referencia VSIX al DSL.

   1. En **source. Extension. vsixmanifest**, haga clic en **Agregar referencia** .

   2. En el cuadro de diálogo, haga clic en **Agregar carga** y, a continuación, busque el archivo VSIX del DSL. El archivo VSIX se crea en la solución DSL, en **DslPackage \\bin \\ \*** .

       Esto permite a los usuarios instalar el DSL y la extensión al mismo tiempo. Si el usuario ya ha instalado el DSL, solo se instalará la extensión.

9. Revise y actualice los demás campos de **source. Extension. vsixmanifest**. Haga clic en **seleccionar ediciones** y compruebe que están establecidas las ediciones de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] correctas.

10. Agregue código al proyecto de biblioteca de clases. Use los ejemplos de la sección siguiente como guía.

     Puede agregar cualquier número de clases de comandos, de gestos y de validación.

11. Para probar la extensión, presione **F5**. En la instancia experimental de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], cree o abra un archivo de ejemplo de DSL.

## <a name="writing-mef-extensions-for-dsls"></a>Escribir extensiones MEF para DSL
 Puede escribir extensiones en el proyecto de código de ensamblado de una solución de extensión DSL independiente. También puede usar MEF en el proyecto DslPackage, como una manera cómoda de escribir comandos, gestos y código de validación como parte del DSL.

### <a name="menu-commands"></a>Comandos de menú
 Para escribir un comando de menú, defina una clase que implemente <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension> y Prefije la clase con el atributo que se define en el DSL, denominado *sudsl* `CommandExtension`. Puede escribir más de una clase de comandos de menú.

 se llama a `QueryStatus()` siempre que el usuario haga clic con el botón secundario en el diagrama. Debe inspeccionar la selección actual y establecer `command.Enabled` para indicar si el comando es aplicable.

```
using System.ComponentModel.Composition;
using System.Linq;
using Company.MyDsl; // My DSL
using Company.MyDsl.ExtensionEnablement; // My DSL
using Microsoft.VisualStudio.Modeling; // Transactions
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement; // IVsSelectionContext
using Microsoft.VisualStudio.Modeling.ExtensionEnablement; // ICommandExtension

namespace MyMefExtension
{
  // Defined in Dsl\MefExtension\DesignerExtensionMetaDataAttribute.cs:
  [MyDslCommandExtension]
  public class MyCommandClass : ICommandExtension
  {
    /// <summary>
    /// Provides access to current document and selection.
    /// </summary>
    [Import]
    IVsSelectionContext SelectionContext { get; set; }

    /// <summary>
    /// Called when the user selects this command.
    /// </summary>
    /// <param name="command"></param>
    public void Execute(IMenuCommand command)
    {
      // Transaction is required if you want to update elements.
      using (Transaction t = SelectionContext.CurrentStore
              .TransactionManager.BeginTransaction("fix names"))
      {
        foreach (ExampleShape shape in SelectionContext.CurrentSelection)
        {
          ExampleElement element = shape.ModelElement as ExampleElement;
          element.Name = element.Name + " !";
        }
        t.Commit();
      }
    }

    /// <summary>
    /// Called when the user right-clicks the diagram.
    /// Determines whether the command should appear.
    /// This method should set command.Enabled and command.Visible.
    /// </summary>
    /// <param name="command"></param>
    public void QueryStatus(IMenuCommand command)
    {
      command.Enabled =
        command.Visible = (SelectionContext.CurrentSelection.OfType<ExampleShape>().Count() > 0);
    }

    /// <summary>
    /// Called when the user right-clicks the diagram.
    /// Determines the text of the command in the menu.
    /// </summary>
    public string Text
    {
      get { return "My menu command"; }
    }
  }
}

```

### <a name="gesture-handlers"></a>Controladores de gestos
 Un controlador de gestos puede tratar con los objetos arrastrados hasta el diagrama desde cualquier lugar, dentro o fuera de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. En el ejemplo siguiente se permite al usuario arrastrar archivos desde el explorador de Windows hasta el diagrama. Crea elementos que contienen los nombres de archivo.

 Puede escribir Controladores para tratar los arrastres de otros modelos DSL y modelos UML. Para obtener más información, vea [Cómo: agregar un controlador de arrastrar y colocar](../modeling/how-to-add-a-drag-and-drop-handler.md).

```

using System.ComponentModel.Composition;
using System.Linq;
using Company.MyDsl;
using Company.MyDsl.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling; // Transactions
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;

namespace MefExtension
{
  [MyDslGestureExtension]
  class MyGestureExtension : IGestureExtension
  {
    public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)
    {
      System.Windows.Forms.MessageBox.Show("double click!");
    }

    /// <summary>
    /// Called when the user drags anything over the diagram.
    /// Return true if the dragged object can be dropped on the current target.
    /// </summary>
    /// <param name="targetMergeElement">The shape or diagram that the mouse is currently over</param>
    /// <param name="diagramDragEventArgs">Data about the dragged element.</param>
    /// <returns></returns>
    public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)
    {
      // This handler only allows items to be dropped onto the diagram:
      return targetMergeElement is MefDsl2Diagram &&
      // And only accepts files dragged from Windows Explorer:
        diagramDragEventArgs.Data.GetFormats().Contains("FileNameW");
    }

    /// <summary>
    /// Called when the user drops an item onto the diagram.
    /// </summary>
    /// <param name="targetDropElement"></param>
    /// <param name="diagramDragEventArgs"></param>
    public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
    {
      MefDsl2Diagram diagram = targetDropElement as MefDsl2Diagram;
      if (diagram == null) return;

      // This handler only accepts files dragged from Windows Explorer:
      string[] draggedFileNames = diagramDragEventArgs.Data.GetData("FileNameW") as string[];
      if (draggedFileNames == null || draggedFileNames.Length == 0) return;

      using (Transaction t = diagram.Store.TransactionManager.BeginTransaction("file names"))
      {
        // Create an element to represent each file:
        foreach (string fileName in draggedFileNames)
        {
          ExampleElement element = new ExampleElement(diagram.ModelElement.Partition);
          element.Name = fileName;

          // This method of adding the new element allows the position
          // of the shape to be specified:
          ElementGroup group = new ElementGroup(element);
          diagram.ElementOperations.MergeElementGroupPrototype(
            diagram, group.CreatePrototype(), PointD.ToPointF(diagramDragEventArgs.MousePosition));
        }
        t.Commit();
      }
    }
  }
}

```

### <a name="validation-constraints"></a>Restricciones de validación
 Los métodos de validación están marcados por el atributo `ValidationExtension` que genera el DSL, y también por <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute>. El método puede aparecer en cualquier clase que no esté marcada por un atributo.

 Para obtener más información, vea [validación en un lenguaje específico de dominio](../modeling/validation-in-a-domain-specific-language.md).

```
using Company.MyDsl;
using Company.MyDsl.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.Validation;

namespace MefExtension
{
  class MyValidationExtension // Can be any class.
  {
    // SAMPLE VALIDATION METHOD.
    // All validation methods have the following attributes.

    // Specific to the extended DSL:
    [MyDslValidationExtension]

    // Determines when validation is applied:
    [ValidationMethod(
       ValidationCategories.Save
     | ValidationCategories.Open
     | ValidationCategories.Menu)]

    /// <summary>
    /// When validation is executed, this method is invoked
    /// for every element in the model that is an instance
    /// of the second parameter type.
    /// </summary>
    /// <param name="context">For reporting errors</param>
    /// <param name="elementToValidate"></param>
    private void ValidateClassNames
      (ValidationContext context,
       // Type determines to what elements this will be applied:
       ExampleElement elementToValidate)
    {
      // Write code here to test values and links.
      if (elementToValidate.Name.IndexOf(' ') >= 0)
      {
        // Log any unacceptable values:
        context.LogError(
          // Description:
          "Name must not contain spaces"
          // Error code unique to this type of error:
          , "MyDsl001"
          // Element to highlight when user double-clicks error:
          , elementToValidate);
} } } }

```

## <a name="see-also"></a>Vea también
 [Envío de extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md) [Managed Extensibility Framework (MEF)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde) [Cómo: agregar una validación de controlador de arrastrar y colocar](../modeling/how-to-add-a-drag-and-drop-handler.md) [en un lenguaje específico de dominio](../modeling/validation-in-a-domain-specific-language.md)
