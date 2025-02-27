---
title: Personalizar títulos para controles enlazados a datos
ms.date: 11/03/2017
ms.topic: conceptual
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 932d50d44fbfaa810225ef90c2f5361bc26d9b72
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648566"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Personalizar el modo en que Visual Studio crea los títulos de controles enlazados a datos

Cuando se arrastran elementos desde la [ventana orígenes de datos](add-new-data-sources.md#data-sources-window) hasta un diseñador, se produce una consideración especial: los nombres de columna de las etiquetas de título se vuelven a formatear en una cadena más legible cuando dos o más palabras se encuentran concatenadas.

::: moniker range="vs-2017"

Puede personalizar la forma en que se crean estas etiquetas estableciendo los valores **SmartCaptionExpression**, **SmartCaptionReplacement**y **SmartCaptionSuffix** en **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0 \Data** clave del registro de los diseñadores.

::: moniker-end

::: moniker range=">=vs-2019"

Puede personalizar la forma en que se crean estas etiquetas estableciendo los valores **SmartCaptionExpression**, **SmartCaptionReplacement**y **SmartCaptionSuffix** en **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\16.0 \Data** clave del registro de los diseñadores.

::: moniker-end

> [!NOTE]
> Esta clave del registro no existe hasta que se crea.

Los subtítulos inteligentes se controlan mediante la expresión regular especificada en el valor de **SmartCaptionExpression** . Al agregar la clave del registro de los **diseñadores de datos** se invalida la expresión regular predeterminada que controla las etiquetas de título. Para obtener más información sobre las expresiones regulares, vea [usar expresiones regulares en Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

En la tabla siguiente se describen los valores del registro que controlan las etiquetas de título.

|Elemento del registro|Descripción|
|-------------------|-----------------|
|**SmartCaptionExpression**|Expresión regular que se usa para hacer coincidir los patrones.|
|**SmartCaptionReplacement**|Formato en el que se van a mostrar los grupos coincidentes en **SmartCaptionExpression**.|
|**SmartCaptionSuffix**|Cadena opcional que se va a anexar al final del título.|

En la tabla siguiente se muestra la configuración predeterminada interna de estos valores del registro.

|Elemento del registro|Valor predeterminado|Explicación|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**|**(\\\p{Ll})(\\\p{Lu})&#124;_+**|Coincide con un carácter en minúscula seguido de un carácter en mayúsculas o un carácter de subrayado.|
|**SmartCaptionReplacement**|**$1 $2**|**$1** representa los caracteres coincidentes en los primeros paréntesis de la expresión y el **$2** representa los caracteres coincidentes en el segundo paréntesis. El reemplazo es la primera coincidencia, un espacio y, a continuación, la segunda coincidencia.|
|**SmartCaptionSuffix**|**:**|Representa un carácter anexado a la cadena devuelta. Por ejemplo, si el título es `Company Name`, el sufijo lo hace `Company Name:`|

> [!CAUTION]
> Tenga mucho cuidado al realizar cualquier acción en el editor del registro. Realice una copia de seguridad del registro antes de editarlo. Si utiliza incorrectamente el editor del registro, puede ocasionar problemas graves que pueden requerir la reinstalación del sistema operativo. Microsoft no garantiza que se puedan resolver los problemas que se produzcan con el editor del registro de forma incorrecta. Utilice el editor del registro bajo su responsabilidad.
>
> Para obtener información sobre la copia de seguridad, la edición y la restauración del registro, consulte [información del registro de Windows para usuarios avanzados](https://support.microsoft.com/help/256986/windows-registry-information-for-advanced-users).

## <a name="modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>Modificar el comportamiento de los subtítulos inteligentes de la ventana orígenes de datos

1. Abra una ventana de comandos haciendo clic en **Inicio** y, a continuación, en **Ejecutar**.

2. Escriba `regedit` en el cuadro de diálogo **Ejecutar** y haga clic en **Aceptar**.

3. Expanda el nodo **HKEY_CURRENT_USER**  > **Software**  > **Microsoft**  > **VisualStudio** .

::: moniker range="vs-2017"

4. Haga clic con el botón secundario en el nodo **15,0** y cree una nueva **clave** denominada `Data Designers`.

::: moniker-end

::: moniker range=">=vs-2019"

4. Haga clic con el botón secundario en el nodo **16,0** y cree una nueva **clave** denominada `Data Designers`.

::: moniker-end

5. Haga clic con el botón secundario en el nodo **diseñadores de datos** y cree tres nuevos valores de cadena:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. Haga clic con el botón secundario en el valor **SmartCaptionExpression** y seleccione **modificar**.

7. Escriba la expresión regular que desea que use la ventana **orígenes de datos** .

8. Haga clic con el botón secundario en el valor **SmartCaptionReplacement** y seleccione **modificar**.

9. Escriba la cadena de reemplazo con el formato que desea para mostrar los patrones coincidentes en la expresión regular.

10. Haga clic con el botón secundario en el valor **SmartCaptionSuffix** y seleccione **modificar**.

11. Escriba los caracteres que desee que aparezcan al final del título.

    La próxima vez que arrastre elementos desde la ventana **orígenes de datos** , las etiquetas de título se crearán con los nuevos valores del registro proporcionados.

## <a name="turn-off-the-smart-captioning-feature"></a>Desactivar la característica de subtítulos inteligentes

1. Abra una ventana de comandos haciendo clic en **Inicio** y, a continuación, en **Ejecutar**.

2. Escriba `regedit` en el cuadro de diálogo **Ejecutar** y haga clic en **Aceptar**.

3. Expanda el nodo **HKEY_CURRENT_USER**  > **Software**  > **Microsoft**  > **VisualStudio** .

::: moniker range="vs-2017"

4. Haga clic con el botón secundario en el nodo **15,0** y cree una nueva **clave** denominada `Data Designers`.

::: moniker-end

::: moniker range=">=vs-2019"

4. Haga clic con el botón secundario en el nodo **16,0** y cree una nueva **clave** denominada `Data Designers`.

::: moniker-end

5. Haga clic con el botón secundario en el nodo **diseñadores de datos** y cree tres nuevos valores de cadena:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. Haga clic con el botón secundario en el elemento **SmartCaptionExpression** y seleccione **modificar**.

7. Escriba `(.*)` para el valor. Coincide con toda la cadena.

8. Haga clic con el botón secundario en el elemento **SmartCaptionReplacement** y seleccione **modificar**.

9. Escriba `$1` para el valor. Esto reemplaza la cadena con el valor coincidente, que es toda la cadena para que permanezca sin cambios.

    La próxima vez que arrastre elementos desde la ventana **orígenes de datos** , las etiquetas de título se crearán con títulos sin modificar.

## <a name="see-also"></a>Vea también

- [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)