---
title: Personalizar la transformación de texto T4
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3222a7bdf8e843a915d0ed0fb72f58ff4a89dca0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654003"
---
# <a name="customize-t4-text-transformation"></a>Personalizar la transformación de texto T4

Las plantillas de texto son una característica de Visual Studio que le permite generar código de programa u otros archivos de texto a través de un proceso de transformación. Con [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)], puede extender el proceso de transformación de plantillas predeterminado personalizando el procesador de directivas de plantillas de texto o el host de plantilla de texto.

## <a name="in-this-section"></a>En esta sección

 [El proceso de transformación de plantillas de texto](../modeling/the-text-template-transformation-process.md) Describe cómo funciona la transformación de texto y explica el rol del host de plantilla y los procesadores de directivas.

 [Crear procesadores de directivas de plantillas de texto T4 personalizadas](../modeling/creating-custom-t4-text-template-directive-processors.md) El procesador de directivas trata las directivas de la plantilla, como `<#@template#>.` se ejecuta durante la compilación de la plantilla y puede cargar ensamblados y otros recursos. También puede insertar código que cargará los recursos en tiempo de ejecución. Al definir su propio procesador de directivas, puede reducir la complejidad de las plantillas.

 [Invocar la transformación de texto en una extensión de vs](../modeling/invoking-text-transformation-in-a-vs-extension.md) Si está escribiendo una extensión de Visual Studio, como un comando de menú o un controlador de eventos, la extensión puede utilizar el servicio de plantillas de texto para transformar cualquier plantilla de texto. Puede pasar datos de parámetros a la plantilla mediante el objeto de sesión y obtener los valores de dentro de la plantilla mediante la Directiva de `<#@parameter#>`.

 [Procesamiento de plantillas de texto mediante un host personalizado](../modeling/processing-text-templates-by-using-a-custom-host.md) Cuando se ejecuta el código de la plantilla de texto, el host proporciona acceso a los archivos externos y al estado de la aplicación. Por ejemplo, el host que ejecuta transformaciones de texto en Visual Studio puede proporcionar acceso a **Explorador de soluciones**. También se muestran errores en la ventana de mensajes de error. Si desea ejecutar transformaciones de texto en un contexto diferente, puede definir su propio host que proporciona acceso a los servicios disponibles en ese contexto.

 Si está escribiendo una extensión de Visual Studio, considere la posibilidad de usar el servicio de transformación de texto existente en lugar de escribir su propio host. Para obtener más información, consulte [invocar la transformación de texto en una extensión de vs](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="reference"></a>Referencia

- [Escribir una plantilla de texto T4](../modeling/writing-a-t4-text-template.md) proporciona la sintaxis de las directivas de plantilla de texto y los bloques de control.