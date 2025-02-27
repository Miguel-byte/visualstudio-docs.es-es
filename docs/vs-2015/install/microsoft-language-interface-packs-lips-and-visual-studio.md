---
title: Paquetes de interfaz de idioma (LIP) de Microsoft | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
helpviewer_keywords:
- text [Visual Studio], multiple languages
- Multilingual User Interface [Visual Studio]
- language switching [Visual Studio]
- MUI [Visual Studio]
- multiple language support [Visual Studio SDK]
- Windows Multilingual User Interface
- UI text language [Visual Studio]
- languages, multiple language support
ms.assetid: dc86304b-65b7-47e6-9314-1dfd02ecfa65
caps.latest.revision: 28
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 503f97d1530f8d22184f42a2452046782a997c18
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432996"
---
# <a name="microsoft-language-interface-packs-lips-and-visual-studio"></a>Paquetes de interfaz de idioma (LIP) de Microsoft y Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Con un paquete de interfaz de idiomas (LIP) de Windows, puede instalar una versión de idioma de Windows y, a continuación, instalar varios paquetes de idioma de la interfaz de usuario. Estos paquetes de idioma proporcionan una interfaz de usuario localizada para el sistema operativo. Por ejemplo, puede instalar un paquete de Idioma de interfaz de usuario en japonés sobre una versión en inglés de Windows y, a continuación, cambiar el idioma de la interfaz de usuario de Windows entre japonés e inglés. Mediante los paquetes LIP, puede tener varias versiones de idioma de Windows en un equipo.

 En los equipos con paquetes LIP y varias versiones de idioma de Visual Studio, cuando se modifica la configuración de idioma de la interfaz de usuario en Windows, dicho cambio afecta a Windows y a Visual Studio si están instalados los correspondientes paquetes de idioma.

## <a name="limitations-of-multi-language-installations"></a>Limitaciones de las instalaciones de varios idiomas
 Cuando se instalan diferentes versiones de idioma de Visual Studio en el mismo equipo, solo se pueden intercambiar los idiomas de las mismas ediciones. Por ejemplo, si tiene instalada una versión Express Edition en inglés, una versión Express Edition en alemán y una versión Professional Edition, solo podrá cambiar los idiomas de las versiones Express Edition, no de la versión Professional Edition.

 Visual Studio usa un paquete de idioma unificado. Para instalar más de una versión de idioma de estos productos, debe instalar primero un producto de idioma completo y después instalar uno o más paquetes de idioma.

> [!NOTE]
> Visual Studio no es compatible con la instalación de varias versiones de idioma del producto de idioma completo en el mismo equipo. Después de instalar un producto de idioma completo, deberá agregar las versiones de idioma mediante los paquetes de idioma. Todavía puede instalar varios productos de idioma completos de las ediciones Express en el mismo equipo.

### <a name="support-for-code-pages"></a>Compatibilidad con páginas de códigos
 Algunas Visual Studio Tools no muestran el texto correctamente si el texto contiene caracteres que no se encuentran en la página de códigos actual. En su lugar, aparecen signos de interrogación o texto dañado. Las siguientes herramientas o áreas se ven afectadas:

- Sitios implementados mediante FTP.

- Nombres de equipo no ASCII en algunos controles.

- Herramientas de línea de comandos que se ejecutan fuera de Visual Studio.

- Asistente para migración de Visual Basic

- ActiveX Control Test Container.

- Visor de objetos OLE y COM.

- Herramienta de depuración Web ISAPI.

- Proyectos de aplicación MFC que tienen contenido HTML de la Ayuda.

- La interfaz de usuario de Visual SourceSafe/SCCI vuelve al inglés si hay una página de códigos incompatible.

- Visual SourceSafe no admite nombres de archivo Unicode.

- Los caracteres definidos por el usuario final (zona de uso privado) no se pueden utilizar como tokens ni identificadores.

- Los caracteres de Latín extendido-B no se pueden mostrar en algunas ventanas de herramientas de Visual Studio cuando la página de códigos de Windows está establecida en un idioma de Asia Oriental.

- Las ejecuciones de texto que constan de caracteres de scripts de varios lenguajes pueden mostrar el glifo predeterminado para algunos caracteres.

- Al copiar y pegar cadenas de script complejas en controles comunes, es posible que los caracteres pierdan su forma. Por consiguiente, utilice un teclado del idioma correspondiente para escribir texto.

##### <a name="to-correctly-display-characters-that-are-not-included-in-the-current-code-page"></a>Para mostrar correctamente los caracteres que no están incluidos en la página de códigos actual

1. Haga clic en **Iniciar** y en **Panel de control** y, a continuación, abra **Configuración regional y de idioma** (o **Región** en [!INCLUDE[win8](../includes/win8-md.md)]).

    > [!NOTE]
    > Para poder llevar a cabo estos pasos, debe ser administrador del equipo.

2. Haga clic en la pestaña **Opciones avanzadas**.

3. En la lista **Seleccione un idioma que coincida con la versión del idioma de los programas no Unicode que quiera utilizar**, seleccione su idioma habitual.

4. Haga clic en **Aceptar**.

## <a name="changing-the-language-used-for-the-ui-text-in-visual-studio"></a>Cambiar el idioma utilizado para el texto de la interfaz de usuario de Visual Studio
 Al instalar varias versiones de idioma de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] en el mismo equipo, la interfaz de usuario de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] cambia de forma predeterminada a **Igual que en Microsoft Windows**. Este valor indica que [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] mostrará el texto de la interfaz de usuario en el idioma de la interfaz de usuario del sistema operativo.

> [!NOTE]
> Si en Visual Studio se define la configuración **Igual que en Microsoft Windows** y no está instalado el correspondiente paquete de idioma de Visual Studio, utilizará el idioma que se haya configurado en la primera instalación.

#### <a name="to-set-the-language-that-is-used-for-the-ui-text-in-visual-studio"></a>Para establecer el idioma que se usa para el texto de la interfaz de usuario de Visual Studio

1. En el menú **Herramientas** , haga clic en **Opciones**.

2. En el cuadro de diálogo **Opciones**, expanda la carpeta **Entorno** y, a continuación, haga clic en **Configuración internacional**.

3. En la lista **Idioma**, elija el idioma en el que el texto de la interfaz de usuario debe aparecer en el entorno de desarrollo.

    Para que el texto de la interfaz de usuario en el IDE se muestre en el mismo idioma que el sistema operativo, seleccione **Igual que en Microsoft Windows**.

   También puede usar el comando devenv para establecer el idioma que se usa para la interfaz de usuario. Para obtener más información, vea [/LCID (devenv.exe)](../ide/reference/lcid-devenv-exe.md).

## <a name="see-also"></a>Vea también
 [Configuración internacional, Entorno, Opciones (Cuadro de diálogo)](../ide/reference/international-settings-environment-options-dialog-box.md)