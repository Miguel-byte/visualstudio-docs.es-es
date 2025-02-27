---
title: Diseñador de actividades CancellationScope | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fa41d63fa4f67037a8e98e72abc3e338ad894f70
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659175"
---
# <a name="cancellationscope-activity-designer"></a>Diseñador de actividades CancellationScope
El diseñador de actividades **CancellationScope** se utiliza para crear y configurar una actividad <xref:System.Activities.Statements.CancellationScope>.

## <a name="the-cancellationscope-activity"></a>Actividad CancellationScope
 La actividad <xref:System.Activities.Statements.CancellationScope> le permite especificar una actividad para la lógica de ejecución y cancelación de esa actividad.

### <a name="using-the-cancellationscope-activity-designer"></a>Utilizar el diseñador de actividades CancellationScope
 El diseñador de actividades **CancellationScope** se puede encontrar en la categoría **transacción** del **cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **cuadro de herramientas** del [!INCLUDE[wfd2](../includes/wfd2-md.md)] (de forma alternativa, seleccione **barra de herramientas** en la **vista.** o Ctrl + Alt + X).

 El diseñador de actividades **CancellationScope** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie [!INCLUDE[wfd2](../includes/wfd2-md.md)], donde se coloquen normalmente las actividades, como en una <xref:System.Activities.Statements.Sequence>. De esta forma se crea una actividad <xref:System.Activities.Statements.CancellationScope> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de CancellationScope. El valor <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado del diseñador de actividades **CancellationScope** o en el cuadro **displayName** de la cuadrícula de propiedades.

### <a name="the-cancellationscope-properties"></a>Propiedades CancellationScope
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.CancellationScope> y se describe cómo se utilizan en el diseñador. La propiedad <xref:System.Activities.Activity.DisplayName%2A> se puede editar en cuadrícula de propiedades, pero las otras propiedades se debe editar en la superficie de [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Nombre de la propiedad|Requerido|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|El nombre descriptivo opcional de la actividad de la clase <xref:System.Activities.Statements.CancellationScope>. El valor predeterminado es CancellationScope. Pese a que el valor <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda usar uno.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|Especifica la actividad para la que se proporciona la lógica de cancelación. Para agregar la actividad <xref:System.Activities.Statements.CancellationScope.Body%2A>, coloque una actividad del cuadro de **herramientas** en el cuadro **Body** del diseñador de actividades **CancellationScope** con el texto de la sugerencia "Coloque la actividad aquí".|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|Especifica la actividad que se ejecuta en caso de cancelación. Para agregar la actividad <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>, coloque una actividad del cuadro de **herramientas** en el cuadro **CancellationHandler** del diseñador de actividad **CancellationScope** con el texto de la sugerencia "Coloque la actividad aquí".|

## <a name="see-also"></a>Vea también
 [Transacción](../workflow-designer/transaction-activity-designers.md) [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) [compensar](../workflow-designer/compensate-activity-designer.md) [confirmar](../workflow-designer/confirm-activity-designer.md) [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)