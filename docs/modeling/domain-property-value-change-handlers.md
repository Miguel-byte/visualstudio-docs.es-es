---
title: Controladores de los cambios de valor de propiedad de dominio
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, overriding event handlers
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 46bf3d8a188899e27e7a83d875cf970583858ba8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653776"
---
# <a name="domain-property-value-change-handlers"></a>Controladores de cambios de valor de propiedad de dominio

En un lenguaje específico de dominio de Visual Studio, cuando cambia el valor de una propiedad de dominio, los métodos `OnValueChanging()` y `OnValueChanged()` se invocan en el controlador de propiedades de dominio. Para responder al cambio, puede invalidar estos métodos.

## <a name="override-the-property-handler-methods"></a>Invalidar los métodos de control de propiedad

Cada propiedad de dominio de su lenguaje específico de dominio es administrada por una clase que está anidada dentro de su clase de dominio primaria. Su nombre sigue el formato *PropertyName*PropertyHandler. Puede inspeccionar esta clase de controlador de propiedades en el archivo **Dsl\Generated Code\DomainClasses.CS**. En la clase, se llama a `OnValueChanging()` inmediatamente antes de que cambie el valor, y se llama a `OnValueChanged()` inmediatamente después de que cambie el valor.

Por ejemplo, supongamos que tiene una clase de dominio denominada `Comment` que tiene una propiedad de dominio de cadena denominada `Text` y una propiedad de entero denominada `TextLengthCount`. Para que `TextLengthCount` siempre contenga la longitud de la cadena de `Text`, puede escribir el código siguiente en un archivo independiente en el proyecto DSL:

```csharp
// Domain Class "Comment":
public partial class Comment
{
  // Domain Property "Text":
  partial class TextPropertyHandler
  {
    protected override void OnValueChanging(CommentBase element, string oldValue, string newValue)
    {
      base.OnValueChanging(element, oldValue, newValue);

      // To update values outside the Store, write code here.

      // Let the transaction manager handle undo:
      Store store = element.Store;
      if (store.InUndoRedoOrRollback || store.InSerializationTransaction) return;

      // Update values in the Store:
      this.TextLengthCount = newValue.Length;
    }
  }
}
```

Observe los siguientes aspectos sobre los controladores de propiedad:

- Se llama a ambos métodos del controlador de propiedad cuando el usuario realiza cambios en una propiedad de dominio y cuando el código de programa asigna un valor diferente a la propiedad.

- Solo se llama a los métodos cuando el valor cambia realmente. No se invoca al controlador si el código de programa asigna un valor que es igual al valor actual.

- Las propiedades de dominio de almacenamiento calculadas y personalizadas no tienen los métodos OnValueChanged y OnValueChanging.

- No puede usar un controlador de cambios para modificar el nuevo valor. Si quiere hacerlo, para restringir el valor de un intervalo determinado, por ejemplo, defina una `ChangeRule`.

- No puede agregar un controlador de cambios a una propiedad que represente un rol de una relación. En su lugar, defina una `AddRule` y una `DeleteRule` en la clase de relación. Estas reglas se desencadenan cuando se crean o se cambian vínculos. Para obtener más información, vea [propagar los cambios dentro del modelo](../modeling/rules-propagate-changes-within-the-model.md).

### <a name="changes-in-and-out-of-the-store"></a>Cambios dentro y fuera del almacén

Se llama a los métodos de controlador de propiedad dentro de la transacción que inició el cambio. Por lo tanto, puede realizar más cambios en el almacén sin abrir una nueva transacción. Los cambios podrían provocar llamadas adicionales del controlador.

Cuando una transacción se está deshaciendo, rehaciendo o revirtiendo, no debe realizar cambios en el almacén, es decir, cambios en los elementos, relaciones, formas, conectores o diagramas del modelo, o en sus propiedades.

Además, normalmente no debería actualizar los valores cuando el modelo se está cargando desde el archivo.

Los cambios al modelo deben protegerse con una prueba como esta:

```csharp
if (!store.InUndoRedoOrRollback && !store. InSerializationTransaction)
{
   this.TextLength = ...; // in-store changes
}
```

En cambio, si el controlador de propiedad propaga los cambios fuera de la tienda, por ejemplo, a un archivo, una base de datos o variables que no son del almacén, siempre debe realizar estos cambios de manera que los valores externos se actualicen cuando el usuario invoque las acciones de deshacer o rehacer.

### <a name="cancel-a-change"></a>Cancelar un cambio

Si quiere evitar un cambio, puede revertir la transacción actual. Por ejemplo, quizás quiera asegurarse de que una propiedad está dentro de un intervalo específico.

```csharp
if (newValue > 10)
{
   store.TransactionManager.CurrentTransaction.Rollback();
   System.Windows.Forms.MessageBox.Show("Value must be less than 10");
}
```

### <a name="alternative-technique-calculated-properties"></a>Técnica alternativa: propiedades calculadas

El ejemplo anterior muestra cómo se puede usar OnValueChanged() para propagar los valores de una propiedad de dominio a otra. Cada propiedad tiene su propio valor almacenado.

En su lugar, podría considerar la posibilidad de definir la propiedad derivada como una propiedad calculada. En ese caso, la propiedad no tiene su propio almacenamiento y su función de definición se evalúa siempre que se necesita su valor. Para obtener más información, consulte [propiedades de almacenamiento calculado y personalizado](../modeling/calculated-and-custom-storage-properties.md).

En lugar del ejemplo anterior, podría establecer el campo **Kind** de `TextLengthCount` que se va a **calcular** en la definición de DSL. Debe proporcionar su propio método **Get** para esta propiedad de dominio. El método **Get** devolverá la longitud actual de la cadena de `Text`.

Sin embargo, un posible inconveniente de las propiedades calculadas es que la expresión se evalúa cada vez que se usa el valor, lo que podría suponer un problema de rendimiento. Además, las propiedades calculadas no tienen ningún método OnValueChanging() y OnValueChanged().

### <a name="alternative-technique-change-rules"></a>Técnica alternativa: cambiar reglas

Si define un cambio, se ejecuta al final de una transacción en la que cambia el valor de una propiedad.  Para obtener más información, vea [propagar los cambios dentro del modelo](../modeling/rules-propagate-changes-within-the-model.md).

Si se realizan varios cambios en una transacción, la regla de cambio se ejecuta cuando se completan todos. Por el contrario, el valor de... los métodos se ejecutan cuando algunos de los cambios no se han realizado. Según lo que quiera lograr, una regla de cambio podría ser más apropiada.

También puede usar un cambio para ajustar el nuevo valor de la propiedad y mantenerlo dentro de un intervalo específico.

> [!WARNING]
> Si una regla realiza cambios en el contenido del almacén, se podrían desencadenar otras reglas y controladores de propiedad. Si una regla cambia la propiedad que la desencadenó, se llamará de nuevo. Debe asegurarse de que las definiciones de regla no producen un desencadenamiento infinito.

```csharp
using Microsoft.VisualStudio.Modeling;
...
// Change rule on the domain class Comment:
[RuleOn(typeof(Comment), FireTime = TimeToFire.TopLevelCommit)]
class MyCommentTrimRule : ChangeRule
{
  public override void
    ElementPropertyChanged(ElementPropertyChangedEventArgs e)
  {
    base.ElementPropertyChanged(e);
    Comment comment = e.ModelElement as Comment;

    if (comment.Text.StartsWith(" ") || comment.Text.EndsWith(" "))
      comment.Text = comment.Text.Trim();
    // If changed, rule will trigger again.
  }
}

// Register the rule:
public partial class MyDomainModel
{
 protected override Type[] GetCustomDomainModelTypes()
 { return new Type[] { typeof(MyCommentTrimRule) };
 }
}
```

## <a name="example"></a>Ejemplo

### <a name="description"></a>Descripción

En el ejemplo siguiente se invalida el controlador de propiedad de una propiedad de dominio y notifica al usuario cuando una propiedad de la clase de dominio `ExampleElement` ha cambiado.

### <a name="code"></a>Código

```csharp
using DslModeling = global::Microsoft.VisualStudio.Modeling;
using DslDesign = global::Microsoft.VisualStudio.Modeling.Design;

namespace msft.FieldChangeSample
{
  public partial class ExampleElement
  {
    internal sealed partial class NamePropertyHandler
    {
      protected override void OnValueChanged(ExampleElement element,
         string oldValue, string newValue)
      {
        if (!this.Store.InUndoRedoOrRollback)
        {
           // make in-store changes here...
        }
        // This part is called even in undo:
        System.Windows.Forms.MessageBox.Show("Value Has Changed");
        base.OnValueChanged(element, oldValue, newValue);
      }
    }
  }
}
```