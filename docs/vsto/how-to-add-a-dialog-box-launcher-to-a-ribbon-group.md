---
title: Procedimiento Agregar un selector de cuadro de diálogo a un grupo de la cinta
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- dialog box launcher [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], dialog box launcher
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b930348845e04dca089cf153a11cc2a9fd29c880
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255906"
---
# <a name="how-to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Procedimiento Agregar un selector de cuadro de diálogo a un grupo de la cinta
  Puede Agregar un selector de cuadro de diálogo a cualquier grupo en una cinta de opciones. Un selector de cuadro de diálogo es un icono pequeño que aparece en un grupo. Los usuarios hacen clic en este icono para abrir cuadros de diálogo o paneles de tareas relacionados que proporcionan más opciones relacionadas con el grupo.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Para agregar un selector de cuadro de diálogo a un grupo de la cinta de opciones

1. Seleccione el archivo de código de la cinta de opciones (archivo *. VB* o *. cs* ) en **Explorador de soluciones**.

2. En el menú **Ver** , haga clic en **Diseñador**.

3. En el diseñador de la cinta de opciones, haga clic con el botón secundario en cualquier grupo y, a continuación, haga clic en **Agregar DialogBoxLauncher**.

     Agregue código al <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick> evento del grupo para abrir un cuadro de diálogo personalizado o integrado.

## <a name="see-also"></a>Vea también
- [Información general sobre la cinta](../vsto/ribbon-overview.md)
- [Obtener acceso a la cinta de opciones en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md)
- [Ejemplos y tutoriales de desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Diseñador de la cinta](../vsto/ribbon-designer.md)
- [Información general del modelo de objetos de la cinta](../vsto/ribbon-object-model-overview.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Cómo: Exportar una cinta de opciones del diseñador de la cinta de opciones a XML de la cinta](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Cómo: Cambiar la posición de una pestaña en la cinta de opciones](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Cómo: Personalizar una pestaña integrada](../vsto/how-to-customize-a-built-in-tab.md)
- [Cómo: Agregar controles a la vista backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Personalización de una cinta para Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Cómo: Introducción a la personalización de la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Cómo: Mostrar errores de interfaz de usuario de complementos](../vsto/how-to-show-add-in-user-interface-errors.md)
- [Tutorial: Crear una pestaña personalizada mediante el diseñador de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Tutorial: Actualizar los controles de una cinta de opciones en tiempo de ejecución](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Tutorial: Crear una pestaña personalizada usando XML de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
