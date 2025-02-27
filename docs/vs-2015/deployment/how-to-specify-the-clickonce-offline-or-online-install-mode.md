---
title: Procedimiento Especifique el sin conexión de ClickOnce o instalar el modo en línea | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, specifying install mode
- install mode
- online applications
- offline applications
- ClickOnce install mode
ms.assetid: 0aee5fc1-e966-4bda-9b8f-d9997aeaa779
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d4111ca5aee4a405a4a797dbfee14a3d4b50435f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68149755"
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>Procedimiento Especificar el modo de instalación en línea y sin conexión de ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El `Install Mode` para un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación determina si la aplicación estará disponible en línea o sin conexión. Cuando se elige **la aplicación solo está disponible en línea**, el usuario debe tener acceso a la [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ubicación (una página Web o un recurso compartido de archivos) para ejecutar la aplicación de publicación. Cuando se elige **la aplicación también está disponible sin conexión**, la aplicación agrega entradas a la **iniciar** menú y el **agregar o quitar programas** cuadro de diálogo; el usuario es puede ejecutar la aplicación cuando no están conectados.  
  
 El `Install Mode` se pueden establecer en el **publicar** página de la **Diseñador de proyectos**.  
  
 **Tenga en cuenta** el `Install Mode` también se puede establecer mediante el Asistente para publicación. Para obtener más información, consulte [Cómo publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-make-a-clickonce-application-available-online-only"></a>Para que una aplicación ClickOnce esté disponible solo en línea  
  
1. Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2. Haga clic en la pestaña **Publicar**.  
  
3. En el **instalar el modo y configuración** área, haga clic en el **la aplicación solo está disponible en línea** botón de opción.  
  
### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>Para que una aplicación ClickOnce esté disponible en línea o sin conexión  
  
1. Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2. Haga clic en la pestaña **Publicar**.  
  
3. En el **instalar el modo y configuración** área, haga clic en el **la aplicación también está disponible sin conexión** botón de opción.  
  
     Cuando se instala, la aplicación agrega entradas a la **iniciar** menú y a **agregar o quitar programas** en el Panel de Control.  
  
## <a name="see-also"></a>Vea también  
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Elegir una estrategia de implementación ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
