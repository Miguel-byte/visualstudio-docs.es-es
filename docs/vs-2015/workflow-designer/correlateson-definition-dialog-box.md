---
title: Cuadro de diálogo Definición de CorrelatesOn | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e2a9a6f7ec6b8bf246ebfc03c166780b229e1aee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656939"
---
# <a name="correlateson-definition-dialog-box"></a>Definición CorrelatesOn (cuadro de diálogo)
El cuadro de diálogo **CorrelatesOn** se utiliza en [!INCLUDE[wfd1](../includes/wfd1-md.md)] para editar la propiedad <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> de una actividad <xref:System.ServiceModel.Activities.Receive>. [!INCLUDE[crdefault](../includes/crdefault-md.md)] el tema [Receive](../workflow-designer/receive-activity-designer.md) .

 La correlación entre las actividades <xref:System.ServiceModel.Activities.Receive> especifica cómo se conectan entre sí diferentes operaciones de servicio en un flujo de trabajo.

 En la tabla siguiente se describen los elementos de la interfaz de usuario (UI) del cuadro de diálogo **CorrelatesOn** .

|Elemento de la interfaz de usuario|Descripción|
|----------------|-----------------|
|**CorrelatesWith**|La clase <xref:System.ServiceModel.Activities.CorrelationHandle> que se utiliza para enrutar el mensaje hacia la instancia de flujo de trabajo adecuada.|
|**Consultas XPath**|Un par clave-valor que contiene las consultas que se utilizan para extraer los datos de la correlación de los mensajes entrantes. Esto corresponde a la propiedad <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>. Un objeto <xref:System.ServiceModel.MessageQuerySet> contiene las consultas XPath.|

## <a name="to-launch-the-correlateson-dialog-box"></a>Para iniciar el cuadro de diálogo CorrelatesOn
 El diseñador de actividades **Receive** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie [!INCLUDE[wfd2](../includes/wfd2-md.md)], donde se coloquen normalmente las actividades. Esto crea una actividad <xref:System.ServiceModel.Activities.Receive> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de Receive. Seleccione el diseñador de actividades **Receive** y haga clic en el botón de puntos suspensivos junto al texto (colección) de la propiedad **CorrelatesOn** en la cuadrícula de propiedades para que aparezca el cuadro de diálogo **definición de CorrelatesOn** .

## <a name="see-also"></a>Vea también
 <xref:System.ServiceModel.Activities.Receive> cuadro de [diálogo Agregar CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) [inicializar](../workflow-designer/initialize-correlation-dialog-box.md) el cuadro de diálogo de correlación