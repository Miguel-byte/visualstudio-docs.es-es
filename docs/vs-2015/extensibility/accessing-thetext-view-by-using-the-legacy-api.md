---
title: Acceso a Text vista mediante la API heredada | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text view
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8f9396e4523e38e7313efb5668c4680f551558ab
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184951"
---
# <a name="accessing-thetext-view-by-using-the-legacy-api"></a>Acceso a la vista de texto mediante la API heredada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Una vista de texto es una presentación del texto que se almacena en un búfer de texto. Puede tener acceso a la vista de texto mediante el uso de la API heredada tal como se muestra en la sección siguiente.  
  
## <a name="text-view-object"></a>Objeto de vista de texto  
 Cada vista está asociado con su propio búfer de texto y la vista es una ventana en los datos en el búfer. El siguiente diagrama muestra las interfaces del objeto de vista de texto, que viene representado por clave <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>.  
  
 ![Objeto de vista de texto de Visual Studio](../extensibility/media/vstextview.gif "objeto vstextview")  
Objeto de vista de texto  
  
 La vista es una forma de presentar el texto en el búfer. Incluye características como ajuste de línea y la esquematización, por lo que lo que ve en la vista no es una representación exacta del texto en el búfer.  
  
 Una vista permite que otros servicios o procesos para interceptar los comandos entrantes y actuar en ellos antes de la vista actúa sobre ellos. El servicio más comunes para hacer esto es un servicio de lenguaje. Un servicio de lenguaje que necesite, por ejemplo, interceptar el comando para la tecla ENTRAR para proporcionar sugerencias personalizadas de comportamiento o la herramienta de sangría.  
  
## <a name="adding-functionality-to-the-text-view"></a>Agregar funcionalidad a la vista de texto  
 Puede personalizar el comportamiento de la vista de texto al controlar las pulsaciones de teclas específicas. Para interceptar las pulsaciones de teclas, implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> en el objeto y proporcione un destino de comando (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) a los comandos de monitor y la intersección.  
  
 La vista de texto utiliza arquitectura secuencial para filtros de comandos. Nuevos filtros de comandos (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objetos) se agregan a la secuencia mediante una llamada a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> método.  
  
 Notificación de eventos para la vista de texto se proporciona mediante el uso de la `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents` interfaz. Implemente esta interfaz en el objeto de cliente para recibir una notificación de cambios en la vista de texto. Exponer esta interfaz para la vista de texto mediante el uso de la <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> interfaz en la vista de texto para recibir notificación de cambios de la vista.  
  
## <a name="see-also"></a>Vea también  
 [Cambie la configuración de vista mediante la API heredada](../extensibility/changing-view-settings-by-using-the-legacy-api.md)   
 [Uso del administrador de texto para supervisar la configuración global](../extensibility/using-the-text-manager-to-monitor-global-settings.md)
