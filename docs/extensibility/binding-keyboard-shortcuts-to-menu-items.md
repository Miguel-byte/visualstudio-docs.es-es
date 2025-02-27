---
title: Enlazar métodos abreviados de teclado a elementos de menú | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 98c0b6f5b26e7f423f2a89f680395ceaba7286bc
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2019
ms.locfileid: "72982269"
---
# <a name="bind-keyboard-shortcuts-to-menu-items"></a>Enlazar métodos abreviados de teclado a elementos de menú
Para enlazar un método abreviado de teclado a un comando de menú personalizado, solo tiene que agregar una entrada al archivo *. Vsct* para el paquete. En este tema se explica cómo asignar un método abreviado de teclado a un botón personalizado, un elemento de menú o un comando de barra de herramientas, y cómo aplicar la asignación de teclado en el editor predeterminado o limitarlo a un editor personalizado.

 Para asignar métodos abreviados de teclado a elementos de menú existentes de Visual Studio, consulte [identificar y personalizar métodos abreviados de teclado](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

## <a name="choose-a-key-combination"></a>Elegir una combinación de teclas
 Muchos métodos abreviados de teclado ya se usan en Visual Studio. No debe asignar el mismo acceso directo a más de un comando, ya que los enlaces duplicados son difíciles de detectar y también pueden producir resultados imprevisibles. Por lo tanto, se recomienda comprobar la disponibilidad de un acceso directo antes de asignarlo.

### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>Para comprobar la disponibilidad de un método abreviado de teclado

1. En la ventana **herramientas** > **Opciones** > **entorno** , seleccione **teclado**.

2. Asegúrese de que **usar nuevo acceso directo en** está establecido en **global**.

3. En el cuadro **presionar teclas de método abreviado** , escriba el método abreviado de teclado que desee usar.

    Si el acceso directo ya se usa en Visual Studio, el cuadro el **método abreviado utilizado actualmente por** Box mostrará el comando al que llama actualmente el acceso directo.

4. Pruebe diferentes combinaciones de claves hasta que encuentre una que no esté asignada.

   > [!NOTE]
   > Los métodos abreviados de teclado que usan **Alt** pueden abrir un menú y no ejecutar directamente un comando. Por lo tanto, el **método abreviado utilizado actualmente por** Box puede estar en blanco cuando se escribe un acceso directo que incluye **Alt**. Para comprobar que el acceso directo no abre un menú, cierre el cuadro de diálogo **Opciones** y, a continuación, presione las teclas.

   En el procedimiento siguiente se da por supuesto que tiene un VSPackage existente con un comando de menú. Si necesita ayuda para hacerlo, eche un vistazo a [creación de una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).

### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>Para asignar un método abreviado de teclado a un comando

1. Abra el archivo *. Vsct* para el paquete.

2. Cree una sección de `<KeyBindings>` vacía después del `<Commands>` si aún no está presente.

   > [!WARNING]
   > Para obtener más información sobre los enlaces de teclado, vea [KeyBinding](../extensibility/keybinding-element.md).

    En la sección `<KeyBindings>`, cree una entrada `<KeyBinding>`.

    Establezca los atributos `guid` y `id` en los del comando que desea invocar.

    Establezca el atributo `mod1` en **control**, **Alt**o **Shift**.

    La sección KeyBindings debe tener un aspecto similar al siguiente:

   ```xml
   <KeyBindings>
       <KeyBinding guid="<name of command set>" id="<name of command id>"
           editor="guidVSStd97" key1="1" mod1="CONTROL"/>
   </KeyBindings>

   ```

   Si el método abreviado de teclado requiere más de dos claves, establezca los atributos `mod2` y `key2`.

   En la mayoría de los casos, no se debe usar **Shift** sin un segundo modificador, ya que si se presiona, la mayoría de las claves alfanuméricas se escriben con una letra mayúscula o un símbolo.

   Los códigos de tecla virtual permiten tener acceso a las teclas especiales que no tienen un carácter asociado, por ejemplo, las teclas de función y la tecla **retroceso** . Para obtener más información, consulte [códigos de tecla virtual](/windows/desktop/inputdev/virtual-key-codes).

   Para que el comando esté disponible en el editor de Visual Studio, establezca el atributo `editor` en `guidVSStd97`.

   Para que el comando esté disponible solo en un editor personalizado, establezca el atributo `editor` en el nombre del editor personalizado generado por la plantilla de paquete de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] al crear el VSPackage que incluye el editor personalizado. Para buscar el valor del nombre, busque en la sección `<Symbols>` para un nodo `<GuidSymbol>` cuyo atributo `name` termine en "`editorfactory`". Este es el nombre del editor personalizado.

## <a name="example"></a>Ejemplo
 En este ejemplo se enlaza el método abreviado de teclado **Ctrl**+**Alt**+**C** a un comando denominado `cmdidMyCommand` en un paquete denominado `MyPackage`.

```
<CommandTable>
. . .
<Commands>
. . .
</Commands>
<KeyBindings>
  <KeyBinding guid="guidMyPackageCmdSet" id="cmdidMyCommand"
      key1="C" mod1="CONTROL" mod2="ALT" editor="guidVSStd97" />
</KeyBindings>
. . .
</CommandTable>
```

## <a name="example"></a>Ejemplo
 En este ejemplo se enlaza el método abreviado de teclado **Ctrl**+**B** a un comando denominado `cmdidBold` en un proyecto denominado `TestEditor`. El comando solo está disponible en el editor personalizado y no en otros editores.

```xml
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />
```

## <a name="see-also"></a>Vea también
- [Extensión de menús y comandos](../extensibility/extending-menus-and-commands.md)