---
title: Uso de la máquina de Estados heredada Diseñador de flujo de trabajo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- StateFinalizationActivity activity
- StateActivity activity
- SetStateActivity activity
- EventDrivenActivity activity
- state machine workflow designer
- state machine workflows, designer
- state machine workflows, activities
- StateInitializationActivity activity
ms.assetid: 2cd21123-35c2-4eaf-82f6-86fce7a8f04d
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8c2b1ce1f1b2c6a16b5576880904feadf37a3e7b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72606771"
---
# <a name="using-the-legacy-state-machine-workflow-designer"></a>Usar el diseñador de flujo de trabajo de máquina de estados heredado
Al crear un nuevo proyecto de flujo de trabajo de equipo de estado en [!INCLUDE[vs2010](../includes/vs2010-md.md)] que tiene como destino el [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o el [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)], puede usar la **aplicación de consola de flujos de trabajo de equipo** de estado o la biblioteca de flujos de trabajo de equipo de **Estado** heredada. plantilla de proyecto. Si elige una de estas plantillas de proyecto de máquina de estados, el diseñador de máquina de estados se presenta como la interfaz de usuario del diseñador de flujo de trabajo heredada. Para obtener información acerca de las plantillas de proyecto de equipo de estado heredado, consulte [Cómo: crear aplicaciones de consola de flujos de trabajo de equipo de estado (heredado)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) y [Cómo: crear una biblioteca de flujos de trabajo de equipo de estado (heredado)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md).

 Un flujo de trabajo de equipo de estado está compuesto por un conjunto de estados. Se designa un estado como estado inicial. Cada estado puede recibir un conjunto de eventos determinado. En función de un evento, se puede realizar una transición a otro estado. El flujo de trabajo de equipo de estado puede tener un estado final. Cuando se realiza una transición al estado final, el flujo de trabajo termina.

## <a name="state-machine-designer-views"></a>Vistas del diseñador de equipo de estado
 El diseñador de equipo de estado es un diseñador de forma libre, lo que significa que las actividades se pueden mover libremente por la superficie de diseño. El diseñador de máquina de Estados tiene dos vistas: vista de *Estado* y vista *controlada por eventos* .

 La vista de estado muestra las actividades de estado y las actividades orientadas a eventos que pueden estar dentro de una actividad de estado. En esta vista, las transiciones de un estado a otro se representan mediante líneas que van de la actividad orientada a eventos en un estado a otro estado. También puede crear las transiciones dibujando la línea usted mismo. Para dibujar la transición, seleccione la actividad orientada a eventos y, a continuación, seleccione uno de los controladores de la actividad y arrástrelo. Esta acción dibuja una línea. A continuación, la línea se adjunta al estado de destino, lo que indica una transición entre estados.

 Para tener acceso a la vista orientada a eventos, haga doble clic en una actividad orientada a eventos. El diseñador que aparece es muy parecido al diseñador de flujo de trabajo secuencial. En la parte superior del diseñador, una barra de exploración muestra la jerarquía de las actividades hasta la actividad orientada a eventos que se aparece. Puede volver a la vista de estado haciendo clic en cualquier elemento de la jerarquía que se muestra. Si ha dibujado una transición de un estado a otro en la vista de estado, y si está en la vista orientada a eventos de esa actividad, se agrega una actividad de estado fija a la actividad orientada a eventos. Si cambia las propiedades de la actividad de estado fija, el cambio queda reflejado en la vista de estado.

## <a name="state-machine-workflow-activities"></a>Actividades de flujo de trabajo de equipo de estado
 En la tabla siguiente se describen las actividades principales que se utilizan en un diseñador de flujo de trabajo de máquina de estados.

|Nombre del cuadro de herramientas|Actividad|Descripción|
|------------------|--------------|-----------------|
|**Estado**|[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|Representa un estado en una máquina de Estados; puede contener actividades **StateActivity** adicionales. Para obtener más información, vea [uso de la actividad StateActivity](http://go.microsoft.com/fwlink?LinkID=65083).|
|**SetState**|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|Especifica una transición a un nuevo estado. Para obtener más información, vea [uso de la actividad SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082).|
|**StateInitialization**|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|Se ejecuta cuando se entra en un estado; puede contener otras actividades. Para obtener más información, vea [usar la actividad StateInitialization](http://go.microsoft.com/fwlink?LinkID=65006).|
|**StateFinalization**|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|Ejecuta actividades contenidas al mantener una actividad [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) . Para obtener más información, vea [uso de la actividad StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008).|
|**EventDriven**|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|Se utiliza para los estados que dependen de un evento externo para empezar a ejecutarse. La actividad **EventDrivenActivity** debe tener una actividad que implemente la interfaz [IEventActivity](http://go.microsoft.com/fwlink?LinkID=65032) como la primera actividad secundaria. Para obtener más información, vea [usar la actividad EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068).|

 El componente principal de un flujo de trabajo de equipo de estado es la actividad [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) . Al capturarse eventos en diversos puntos en un flujo de trabajo de equipo de estado, se entra en estados diferentes para administrar las tareas asociadas a los eventos. Durante la duración del flujo de trabajo, éste puede entrar en y salir de varios estados diferentes. Estos Estados se conectan entre sí mediante la actividad [SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041) .

 Al arrastrar un nuevo **StateActivity** en la superficie de diseño de flujo de trabajo, puede Agregar las actividades [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029), [StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044), [StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)o **StateActivity** adicionales como actividades secundarias.

> [!CAUTION]
> Cuando use el diseñador de flujo de trabajo de equipo de estado para crear flujos de trabajo, debe supervisar la estructura del flujo de trabajo que está diseñando con la ventana vista **esquema del documento** . La vista de la estructura del flujo de trabajo de equipo de estado en la ventana vista **esquema del documento** refleja el diseño lógico de las actividades en el archivo de marcado de flujo de trabajo. El diseño físico de las actividades de flujo de trabajo tal como aparecen en la superficie de diseño podría no reflejar el diseño lógico de las actividades del archivo de marcado del flujo de trabajo.
>
> Para abrir la **ventana esquema del documento** , en el menú **Ver** , seleccione **otras ventanas**y, a continuación, seleccione **esquema del documento**.

## <a name="see-also"></a>Vea también
 [Cómo: crear aplicaciones de consola de flujos de trabajo de equipo de estado (heredado)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) cómo: crear un flujo de trabajo de [máquina de Estados](http://go.microsoft.com/fwlink?LinkID=65016) de [biblioteca de flujos de trabajo de máquina de Estados (heredado)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md) [usar la actividad StateActivity](http://go.microsoft.com/fwlink?LinkID=65083) [mediante el Actividad StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65006) [mediante la actividad StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008) [usar la actividad SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082) [mediante la actividad EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068)