---
title: Diseñador de actividades Diseñador de flujo de trabajo-FlowDecision
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.FlowDecision.UI
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2274333de9255ff818b4ee6952bfa1b2a99c59b3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650425"
---
# <a name="flowdecision-activity-designer"></a>Diseñador de actividades FlowDecision

El nodo <xref:System.Activities.Statements.FlowDecision> es un nodo condicional que proporciona una bifurcación para el flujo de control en una alternativa entre dos, en función de si se ha satisfecho una condición especificada. Si el flujo requiere más de dos bifurcaciones, utilice <xref:System.Activities.Statements.FlowSwitch%601> en su lugar.

## <a name="the-flowdecision-node"></a>Nodo FlowDecision

Utilice el nodo <xref:System.Activities.Statements.FlowDecision> cuando se puedan crear bifurcaciones en dos direcciones a partir del flujo. Un nodo <xref:System.Activities.Statements.FlowDecision> tiene una propiedad <xref:System.Activities.Statements.FlowDecision.Condition%2A> y una clase <xref:System.Activities.Statements.FlowNode> asociadas a cada uno de los dos posibles resultados: <xref:System.Activities.Statements.FlowDecision.True%2A> o <xref:System.Activities.Statements.FlowDecision.False%2A>. Se evalúa <xref:System.Activities.Statements.FlowDecision.Condition%2A> y el valor resultante determina la clase <xref:System.Activities.Statements.FlowNode> siguiente que se va a procesar dentro de <xref:System.Activities.Statements.Flowchart>.

### <a name="using-the-flowdecision-designer"></a>Utilizar el diseñador FlowDecision

El diseñador **FlowDecision** se puede encontrar en la categoría **Diagrama de flujo** del cuadro de **herramientas**, al que se tiene acceso al hacer clic en la pestaña cuadro de **herramientas** en el diseñador de flujo de trabajo. Como alternativa, seleccione **cuadro de herramientas** en el menú **Ver** o presione **Ctrl** +**Alt** +**X**.

El diseñador **FlowDecision** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie diseñador de flujo de trabajo dentro de un diseñador de actividades **Flowchart** . Esto crea una <xref:System.Activities.Statements.FlowDecision> la **decisión** con etiqueta dentro de la actividad <xref:System.Activities.Statements.Flowchart>. Se muestra el mouse sobre el diseñador y los manipuladores del cuadrado **verdadero** y **falso** de las dos ramas.

Después de arrastrar el diseñador de **FlowDecision** y otros diseñadores al **Diagrama de flujo**, los nodos se pueden vincular entre sí para especificar el orden de ejecución. Para crear un vínculo entre un nodo de origen (incluidas las bifurcaciones **true** y **false** de **FlowDecision**) y un nodo de destino, el mouse sobre el diseñador del nodo de origen y los identificadores cuadrados aparecen en cada lado del mismo. Haga clic en uno de los identificadores cuadrados y arrástrelo manteniendo presionado el botón del mouse hasta uno de los identificadores que aparecen de forma similar en torno al nodo de destino cuando desplaza el mouse sobre el mismo. Suelte el botón del mouse y se creará un vínculo entre ambos nodos que quedará representado como una flecha desde el diseñador de origen hasta el diseñador de destino.

La expresión que indica el <xref:System.Activities.Statements.FlowDecision.Condition%2A> se puede escribir en el cuadro **condición** de la ventana **propiedades** si se hace clic en el texto de la sugerencia "Escriba una expresión de VB".

### <a name="the-flowdecision-properties"></a>Las propiedades FlowDecision

En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.FlowDecision> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en la cuadrícula de propiedades o en la superficie del diseñador.

|Nombre de la propiedad|Requerido|Uso|
|-|--------------|-|
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|True|La condición que determina la ruta de acceso que va a tomar el control de flujo.|
|<xref:System.Activities.Statements.FlowDecision.True%2A>|False|La ruta de acceso que toma el control de flujo si se satisface <xref:System.Activities.Statements.FlowDecision.Condition%2A>.|
|<xref:System.Activities.Statements.FlowDecision.False%2A>|False|La ruta de acceso que toma el control de flujo si no se satisface <xref:System.Activities.Statements.FlowDecision.Condition%2A>.|

## <a name="see-also"></a>Vea también

- [Diagrama de flujo](../workflow-designer/flowchart-activity-designers.md)
- [Diagrama de flujo](../workflow-designer/flowchart-activity-designer.md)
- [FlowSwitch\<T>](../workflow-designer/flowswitch-t-activity-designer.md)