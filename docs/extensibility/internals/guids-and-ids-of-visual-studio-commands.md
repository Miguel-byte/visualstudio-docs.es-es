---
title: GUID e identificadores de comandos de Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f7670eacc875bf7c5437d9bb92cc1932753093bd
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186641"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>GUID e identificadores de comandos de Visual Studio
Los valores de identificador y GUID de los comandos incluidos en el entorno de desarrollo integrado (IDE) de Visual Studio se definen en los archivos. Vsct que se instalan como parte del SDK de Visual Studio. Para obtener más información, vea [comandos, menús y grupos definidos por el IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

 Para obtener más información sobre cómo trabajar con objetos IDE definidos en archivos *. Vsct* , vea [extender menús y comandos](../../extensibility/extending-menus-and-commands.md).

## <a name="find-a-command-definition"></a>Buscar una definición de comando
 Dado que Visual Studio define más de 1000 comandos, no es práctico enumerarlos aquí. En su lugar, siga estos pasos para buscar la definición de un comando.

### <a name="to-locate-a-command-definition"></a>Para buscar una definición de comando

1. En Visual Studio, abra los siguientes archivos en la *< ruta de instalación del SDK de Visual studio\>carpeta \VisualStudioIntegration\Common\Inc\\* : *SharedCmdDef. Vsct*, *ShellCmdDef. Vsct*, *VsDbgCmdUsed. Vsct*, *Venusmenu. Vsct*.

    La mayoría de los comandos de Visual Studio se definen en *SharedCmdDef. Vsct* y *ShellCmdDef. Vsct*. *VsDbgCmdUsed. Vsct* define comandos que pertenecen al depurador y *Venusmenu. Vsct* define comandos específicos del desarrollo web.

2. Si el comando es un elemento de menú, tenga en cuenta el texto exacto del elemento de menú. Si el comando es un botón de una barra de herramientas, tenga en cuenta el texto de información sobre herramientas que aparece cuando se pausa en él.

3. Presione **Ctrl**+**F** para abrir el cuadro de diálogo **Buscar** .

4. En el cuadro **Buscar** , escriba el texto que anotó en el paso 2.

5. Compruebe que **todos los documentos abiertos** se muestran en el cuadro **Buscar en** .

6. Haga clic en el botón **Buscar siguiente** hasta que se seleccione el texto en la sección `<Strings>` de un [elemento de botón](../../extensibility/button-element.md).

    El elemento `<Button>` en el que aparece el comando es la definición del comando.

   Cuando haya encontrado la definición de comando, puede colocar una copia del comando en otro menú o barra de herramientas creando un [elemento CommandPlacement](../../extensibility/commandplacement-element.md) que tenga los mismos valores `guid` y `id` que el comando. Para obtener más información, vea [crear grupos reutilizables de botones](../../extensibility/creating-reusable-groups-of-buttons.md).

### <a name="special-cases"></a>Casos especiales
 En los casos siguientes, el texto de menú o el texto de información sobre herramientas puede no coincidir exactamente con lo que hay en la definición de comando.

- Elementos de menú que incluyen un carácter subrayado, como el comando **Imprimir** del menú **archivo** , en el que aparece subrayado *P* .

     Los caracteres precedidos por el carácter de y comercial (&) en los nombres de los elementos de menú se muestran como subrayados. Sin embargo, los archivos *. Vsct* se escriben en XML, que utiliza el carácter de y comercial (&) para indicar caracteres especiales y requiere que se escriba una y comercial como *&amp;amp;* . Por lo tanto, en un archivo *. Vsct* , el comando **Print** aparece como *&amp;amp; Imprimir*.

- Comandos que tienen texto dinámico, como **guardar** \<nombre de archivo actual\>y elementos de menú generados dinámicamente, como los elementos de la lista de **archivos recientes** .

     No hay ninguna manera confiable de buscar en texto dinámico. En su lugar, busque un grupo que hospede el comando deseado consultando los [GUID e identificadores de los menús](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) o GUID de Visual Studio, [así como los identificadores de las barras de herramientas de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md), y busque en el identificador de ese grupo. Si la definición de comando no tiene el grupo como su [elemento primario](../../extensibility/parent-element.md), busque *SharedCmdPlace. Vsct* y *ShellCmdPlace. Vsct* (o *VsDbgCmdPlace. Vsct* para los comandos del depurador) para un elemento `<CommandPlacement>` que establece el elemento primario del Command. *SharedCmdPlace. Vsct*, *ShellCmdPlace. Vsct*y *VsDbgCmdPlace. vsct* se encuentran en la *\<ruta de instalación del SDK de Visual Studio\>carpeta \VisualStudioIntegration\Common\Inc\\* .

## <a name="see-also"></a>Vea también

- [Archivos de tabla de comandos de Visual Studio (. Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Referencia del esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md)
