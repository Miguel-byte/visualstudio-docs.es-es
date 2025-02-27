---
title: Diseñador de actividad Parallel | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a46a340ccdeacacb8f04b962313db18975447a67
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672635"
---
# <a name="parallel-activity-designer"></a>Diseñador de actividades Parallel
La actividad de la clase <xref:System.Activities.Statements.Parallel> ejecuta una colección de actividades secundarias simultáneamente.

## <a name="the-parallel-activity"></a>La actividad de la clase Parallel
 La actividad de la clase <xref:System.Activities.Statements.Parallel> almacena sus actividades secundarias en una colección de la propiedad <xref:System.Activities.Statements.Parallel.Branches%2A>. Use la actividad de la clase <xref:System.Activities.Statements.Parallel> en vez de la actividad de la clase <xref:System.Activities.Statements.Sequence> si alguna de las actividades secundarias se puede quedar inactiva.

 La actividad <xref:System.Activities.Statements.Parallel> tiene una propiedad <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> que contiene a una expresión [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] especificada por el usuario. La actividad <xref:System.Activities.Statements.Parallel> evalúa esta propiedad una vez se complete cada bifurcación. Si se evalúa como **true**, la actividad <xref:System.Activities.Statements.Parallel> se completa sin ejecutar las otras bifurcaciones. Si el <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> no se evalúa como **true**, la actividad de <xref:System.Activities.Statements.Parallel> se completa cuando se han completado todas sus actividades secundarias.

### <a name="using-the-parallel-activity-designer"></a>Usar el diseñador de actividad Parallel
 El diseñador de actividad **Parallel** se puede encontrar en la categoría **flujo de control** del **cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña cuadro de **herramientas** en el lado izquierdo del [!INCLUDE[wfd2](../includes/wfd2-md.md)] (de forma alternativa, seleccione **barra de herramientas** en la  **Menú Ver** o Ctrl + Alt + X).

 El diseñador de actividad **Parallel** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie de [!INCLUDE[wfd2](../includes/wfd2-md.md)] siempre que se coloquen normalmente los diseñadores de actividad, por ejemplo, dentro de un diseñador de actividad **Sequence** . Después de colocarlo en el [!INCLUDE[wfd2](../includes/wfd2-md.md)], crea una actividad <xref:System.Activities.Statements.Parallel>, que de forma predeterminada contiene un <xref:System.Activities.Activity.DisplayName%2A> de **Parallel** .

 Para agregar una actividad a la colección de <xref:System.Activities.Statements.Parallel.Branches%2A> de la actividad Parallel, arrastre algún otro diseñador de actividad desde el **cuadro de herramientas** y colóquelo en el triángulo dentro del diseñador de actividad **Parallel** . Los triángulos rodean las actividades contenidas en las bifurcaciones. Las actividades adicionales se pueden agregar repitiendo este procedimiento. Las actividades se pueden reordenar arrastrándolas y colocándolos en el diseñador de actividad **Parallel** .

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>Propiedades de la actividad Parallel en el Diseñador de flujo de trabajo
 En la tabla siguiente se muestran las propiedades de la actividad Parallel y se describe cómo se usan en el diseñador.

|Nombre de la propiedad|Requerido|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre para mostrar descriptivo del diseñador de actividades en el encabezado. El valor predeterminado es **Parallel**. El valor se puede editar opcionalmente en la cuadrícula de **propiedades** o directamente en el encabezado del diseñador de actividad.|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|True|Contiene la colección de actividades secundarias que se van a ejecutar.|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|Se evalúa cuando se completa una bifurcación. Si se evalúa como **true**, se cancelan las bifurcaciones pendientes programadas. Si esta propiedad no se establece o se evalúa como **false**, la actividad se completa cuando se han completado todas sus actividades secundarias. El valor predeterminado es **null**.|

## <a name="see-also"></a>Vea también
 [Flujo de control](../workflow-designer/control-flow-activity-designers.md) de \<T de [Sequence](../workflow-designer/sequence-activity-designer.md) [ParallelForEach >](../workflow-designer/parallelforeach-t-activity-designer.md)