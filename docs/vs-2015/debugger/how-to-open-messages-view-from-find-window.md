---
title: Procedimiento Abrir la vista mensajes desde Buscar ventana | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Messages View in Spy++, opening
- opening Messages View in Spy++
ms.assetid: 601a193e-432a-417b-9406-6fec9e401264
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ee29135e659eff7e4965b6b1fb0d24de2c2e90cc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157886"
---
# <a name="how-to-open-messages-view-from-find-window"></a>Procedimiento Apertura de la vista Mensajes desde la ventana Buscar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le resultará cómodo utilizar el **Buscar ventana** cuadro de diálogo para seleccionar una ventana de destino y, a continuación, abra una vista de mensajes de esa ventana.  
  
### <a name="to-open-a-messages-view-window-using-the-find-window-dialog-box"></a>Para abrir una ventana de vista de mensajes mediante el cuadro de diálogo Buscar ventana  
  
1. Organizar las ventanas para que estén visibles Spy ++ y la ventana de destino.  
  
2. Desde el **Spy** menú, elija **Buscar ventana**.  
  
     El [cuadro de diálogo Buscar ventana](../debugger/find-window-dialog-box.md) se abre.  
  
3. Desde el **Windows** pestaña, arrastre el **herramienta de búsqueda** a través de la ventana de destino. A medida que arrastra la herramienta, el **Buscar ventana** cuadro de diálogo muestra los detalles de la ventana seleccionada.  
  
     -O bien-  
  
     Si tiene el identificador de la ventana que desea examinar (por ejemplo, si se copian desde el depurador), puede escribirla en el **controlar** cuadro de texto.  
  
4. En **mostrar**, seleccione **mensajes**.  
  
5. Haga clic en **Aceptar**.  
  
     Un espacio en blanco [vista mensajes](../debugger/messages-view.md) abre la ventana y un **mensajes** menú se agrega a la barra de herramientas de Spy ++.  
  
6. Desde el **mensajes** menú, elija **opciones de registro**.  
  
     El [cuadro de diálogo Opciones de mensaje](../debugger/message-options-dialog-box.md) se abre.  
  
7. Seleccione las opciones para los mensajes que desea mostrar.  
  
8. Presione **Aceptar** para empezar a mensajes de registro.  
  
     Dependiendo de las opciones seleccionadas, los mensajes comenzará a transmitir en la ventana activa de la vista de mensajes.  
  
9. Cuando tenga suficientes mensajes, elija **detener el registro** desde el **mensajes** menú.
