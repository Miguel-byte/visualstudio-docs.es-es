---
title: Opciones, editor de texto, JavaScript, formato | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.New_Lines
ms.assetid: 28a0aef1-9353-4d94-95a5-54b42e15c0dc
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dcfa4a2fb15ed8f4abfff24aa8e78c2b08eb8412
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662247"
---
# <a name="options-text-editor-javascript-formatting"></a>Opciones, editor de texto, JavaScript, formato
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Use la página **Formato** del cuadro de diálogo **Opciones** para establecer las opciones para proporcionar formato al código en el Editor de código. Para acceder a esta página, vaya a la barra de menús y elija **Herramientas**, **Opciones** y expanda **Editor de texto**, **JavaScript** y **Formato**.

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

## <a name="automatic-formatting"></a>Formato automático
 Estas opciones determinan cuándo se da formato en la vista **Origen**.

## <a name="uielement-list"></a>Lista de UIElement

|Opción|DESCRIPCIÓN|
|------------|-----------------|
|**Dar formato a una línea completada al presionar &Entrar**|Cuando se selecciona esta opción, el editor de código aplica formato a la línea automáticamente cuando presiona la tecla Entrar.|
|**Dar formato a una instrucción completada con ;**|Cuando se selecciona esta opción, el editor de código aplica formato a la línea automáticamente cuando presiona la tecla de punto y coma.|
|**Dar formato a un bloque completado con }**|Cuando se selecciona esta opción, el editor de código aplica formato a la línea automáticamente cuando presiona la tecla de llave de cierre.|
|**Dar formato al pegar**|Cuando se selecciona esta opción, el Editor de código cambia el formato del código cuando lo pega en el editor. El editor usa las reglas de formato definidas actualmente. Si no se selecciona esta opción, el editor usa el formato original del código pegado.|

## <a name="new-lines"></a>Nuevas líneas
 Estas opciones determinan si el editor de código coloca una llave de apertura para funciones y bloques de control en una nueva línea.

## <a name="uielement-list"></a>Lista de UIElement

|Opción|DESCRIPCIÓN|
|------------|-----------------|
|**Colocar llave de apertura en línea nueva para funciones**|Cuando se selecciona esta opción, el editor de código desplaza la llave de apertura asociada a una función a una nueva línea.|
|**Colocar llave de apertura para bloques de control en nueva línea**|Cuando se selecciona esta opción, el editor de código desplaza la llave de apertura asociada a un bloque de control (por ejemplo, los bloques de control `if` y `while`) a una nueva línea.|

## <a name="spacing"></a>Espaciado
 Estas opciones determinan cómo se insertan los espacios en la vista **Origen**.

## <a name="uielement-list"></a>Lista de UIElement

|Opción|DESCRIPCIÓN|
|------------|-----------------|
|**Insertar espacio después del delimitador de coma**|Cuando se selecciona esta opción, el editor de código agrega un espacio después de delimitadores de coma.|
|**Insertar espacio tras punto y coma en instrucción “for”**|Cuando se selecciona esta opción, el editor de código agrega un espacio después de cada punto y coma en la primera línea de un bucle `for`.|
|**Insertar espacio delante y detrás de operadores binarios**|Cuando se selecciona esta opción, el editor de código agrega un espacio antes y después de los operadores binarios (por ejemplo, +, -, &&, &#124;&#124;).|
|**Insertar espacio después de palabras clave en instrucciones de flujo de control**|Cuando se selecciona esta opción, el editor de código agrega un espacio después de palabras clave de JavaScript en las instrucciones de flujo de control.|
|**Insertar espacio tras la palabra clave function para las funciones anónimas**|Cuando se selecciona esta opción, el editor de código agrega un espacio después de la palabra clave `function` para funciones anónimas.|
|**Insertar espacio después de abrir y antes de cerrar paréntesis con contenido**|Cuando se selecciona esta opción, el editor de código agrega un espacio después de los paréntesis de apertura y antes de los paréntesis de cierre si dentro de los paréntesis hay caracteres con contenido.|

## <a name="see-also"></a>Otras referencias
 [General, Entorno, Opciones (Cuadro de diálogo)](../../ide/reference/general-environment-options-dialog-box.md)
