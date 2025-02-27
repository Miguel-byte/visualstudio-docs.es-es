---
title: 'Vista Detalles de recursos: datos de contención | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.resourcedetails
helpviewer_keywords:
- Resource Details view
ms.assetid: a4ecfe1c-abbc-4fb3-9ab2-34de50486901
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6328ea53c90b5a5a7ba50fde5a00e29fadacaaa7
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68924514"
---
# <a name="resource-details-view---contention-data"></a>Vista Detalles de recursos: datos de contención
La vista Detalles de recursos presenta un gráfico de escala de tiempo de los eventos de bloqueo originados por las contenciones sobre un recurso seleccionado. Un evento de bloqueo se produce cuando un subproceso se ve obligado a suspender la ejecución porque otro subproceso ha bloqueado el acceso al recurso.

 Esta vista representa la escala de tiempo de ejecución de cada subproceso como una barra horizontal y representa cada evento de bloqueo como una barra vertical en la escala de tiempo del subproceso. Si es necesario, puede aumentar una sección de la escala de tiempo para ver eventos individuales. Para ver la ruta de acceso de ejecución (pila de llamadas) de las funciones que dieron lugar al evento, haga clic en la barra del evento. Las funciones aparecen en la ventana **Pila de llamadas**. Si está disponible el código fuente de una función, puede hacer clic en el nombre de la función para editar el archivo de origen en la interfaz para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="procedures"></a>Procedimientos

#### <a name="to-magnify-a-timeline-segment"></a>Para ampliar un segmento de la escala de tiempo

- Arrastre el puntero del mouse sobre un área de la escala de tiempo.

     Al soltar el botón del mouse, la vista amplía el segmento de tiempo seleccionado. Puede repetir el proceso para ampliar todavía más el segmento. El cuadro de desplazamiento de la barra de desplazamiento temporal representa el tamaño relativo del segmento de tiempo que aparece en la vista.

#### <a name="to-zoom-out-on-a-timeline"></a>Para alejar una escala de tiempo

- Realice uno de estos pasos:

  - Haga clic en **Alejar** para volver al nivel de zoom anterior.

  - Haga clic en **Restablecer zoom** para mostrar toda la escala de tiempo en la vista.

#### <a name="to-view-the-call-stack-of-an-event"></a>Para ver la pila de llamadas de un evento

- En el gráfico de escala de tiempo, haga clic en la barra de eventos.

#### <a name="to-view-or-edit-the-source-code-of-a-function-in-the-call-stack"></a>Para ver o editar el código fuente de una función en la pila de llamadas

- En la ventana **Pila de llamadas**, haga clic en el nombre de la función.

  El código fuente de la función debe formar parte del proyecto actual.

#### <a name="to-view-the-call-tree-of-contention-events-for-the-resource"></a>Para ver el árbol de llamadas de eventos de contención del recurso

- En el gráfico de escala de tiempo, haga clic en **Total**.

     Aparece la vista Contenciones del recurso. Para más información, consulte [Vista Contenciones del recurso](../profiling/resource-contentions-view-contention-data.md).

#### <a name="to-view-all-the-contention-events-of-a-thread"></a>Para ver todos los eventos de contención de un subproceso

- En el gráfico de escala de tiempo, haga clic en el nombre o identificador del subproceso.

     Aparece la vista Detalles del subproceso para el subproceso seleccionado. Para obtener más información, consulte [Vista Detalles del subproceso](../profiling/thread-details-view-contention-data.md).
