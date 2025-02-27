---
title: Diseñador de actividades CompensableActivity | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e2bc28c4586912d7c253c9629c2af0eefd30e47e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656990"
---
# <a name="compensableactivity-activity-designer"></a>Diseñador de actividad CompensableActivity Activity
El diseñador de actividades **CompensableActivity** se utiliza para crear y configurar una actividad <xref:System.Activities.Statements.CompensableActivity>.

## <a name="the-compensableactivity-activity"></a>La actividad CompensableActivity
 La clase <xref:System.Activities.Statements.CompensableActivity> define una unidad de trabajo que se puede confirmar o compensar después de que se haya completado correctamente.

### <a name="using-the-compensableactivity-activity-designer"></a>Usar el diseñador de actividad CompensableActivity
 El diseñador de actividades **CompensableActivity** se puede encontrar en la categoría **transacción** del **cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **cuadro de herramientas** en el lado izquierdo del [!INCLUDE[wfd2](../includes/wfd2-md.md)] (también puede seleccionar barra de **herramientas** en el menú **Ver** o Ctrl + Alt + X).

 El diseñador de actividades **CompensableActivity** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie [!INCLUDE[wfd2](../includes/wfd2-md.md)], donde se coloquen normalmente las actividades, como en una <xref:System.Activities.Statements.Sequence>. De esta forma, se crea una actividad de la clase <xref:System.Activities.Statements.CompensableActivity> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de CompensableActivity. El valor <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado del diseñador de actividades **CompensableActivity** o en el cuadro **displayName** de la cuadrícula de propiedades.

### <a name="the-compensableactivity-properties"></a>Las propiedades de CompensableActivity
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.CompensableActivity> y se describe cómo se utilizan en el diseñador. Las propiedades <xref:System.Activities.Activity.DisplayName%2A> y <xref:System.Activities.Activity%601.Result%2A> se pueden editar en la cuadrícula de propiedades, pero el resto de propiedades se deben editar en la superficie de [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Nombre de la propiedad|Requerido|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|El nombre descriptivo opcional de la actividad de la clase <xref:System.Activities.Statements.CompensableActivity>. El valor predeterminado es CompensableActivity.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Especifica el valor devuelto de la clase <xref:System.Activities.Statements.CompensableActivity>. Esta propiedad se debe editar en la cuadrícula de propiedades.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|True|Especifica la actividad para la que se proporciona la lógica de compensación, cancelación y confirmación. Para agregar la actividad <xref:System.Activities.Statements.CompensableActivity.Body%2A>, coloque una actividad del cuadro de **herramientas** en el cuadro **Body** del diseñador de actividades **CompensableActivity** con el texto de la sugerencia "Coloque la actividad aquí".|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|Especifica la actividad que se ejecuta en caso de cancelación. Para agregar la actividad, coloque su diseñador desde el cuadro de **herramientas** en el cuadro **CancellationHandler** del diseñador de actividad **CompensableActivity** con el texto de la sugerencia "Coloque la actividad aquí".|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|Especifica la actividad que se va a ejecutar al realizar la compensación para la actividad de la propiedad <xref:System.Activities.Statements.CompensableActivity.Body%2A>. Este controlador se puede invocar explícitamente mediante la actividad <xref:System.Activities.Statements.Compensate>.<br /><br /> Para agregar la actividad, coloque su diseñador de actividad del cuadro de **herramientas** en el cuadro **CompensationHandler** del diseñador de actividad **CompensableActivity** con el texto de la sugerencia "Coloque la actividad aquí".|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|Especifica la actividad que se va a ejecutar al confirmar la actividad de la propiedad <xref:System.Activities.Statements.CompensableActivity.Body%2A>. Este controlador se puede invocar explícitamente mediante la actividad <xref:System.Activities.Statements.Confirm>.<br /><br /> Para agregar la actividad, coloque su diseñador de actividad del cuadro de **herramientas** en el cuadro **ConfirmationHandler** del diseñador de actividad **CompensableActivity** con el texto de la sugerencia "Coloque la actividad aquí".|

## <a name="see-also"></a>Vea también
 [Transacción](../workflow-designer/transaction-activity-designers.md) [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md) [compensar](../workflow-designer/compensate-activity-designer.md) [confirmar](../workflow-designer/confirm-activity-designer.md) [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)