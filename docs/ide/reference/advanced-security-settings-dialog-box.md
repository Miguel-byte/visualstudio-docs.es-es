---
title: Cuadro de diálogo Configuración de seguridad avanzada
ms.date: 06/27/2018
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- vs.err.debug_in_zone_no_hostproc
helpviewer_keywords:
- Advanced Security Settings dialog box
ms.assetid: 2e7aefe9-6d20-4f3e-b257-aee1ebcc6f5d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e1fcc3d09e43fc5358cbe507c5045c16cc9f8cf9
ms.sourcegitcommit: 85d66dc9fea3fa49018263064876b15aeb6f9584
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68461861"
---
# <a name="advanced-security-settings-dialog-box"></a>Cuadro de diálogo Configuración de seguridad avanzada

Este cuadro de diálogo permite especificar la configuración de seguridad relacionada con la depuración en zona.

![Cuadro de diálogo Configuración de seguridad avanzada en Visual Studio](../media/advanced-security-settings.png)

Para acceder a este cuadro de diálogo, seleccione un nodo de proyecto en el **Explorador de soluciones** y después, en el menú **Proyecto**, haga clic en **Propiedades**. Cuando se muestre el **Diseñador de proyectos**, haga clic en la pestaña **Seguridad**. En la página **Seguridad**, seleccione **Habilitar configuración de seguridad de ClickOnce**, haga clic en **Aplicación de confianza parcial** y, después, haga clic en **Avanzado**.

## <a name="uielement-list"></a>Lista de UIElement

**Conceder a la aplicación acceso al sitio de origen**

Si selecciona esta casilla, la aplicación puede tener acceso al sitio web o recurso compartido de servidor en el que está publicada. Esta opción se encuentra activada de forma predeterminada.

**Depurar esta aplicación como si se hubiera descargado de la siguiente dirección URL:**

Si necesita que la aplicación tenga acceso al sitio web o recurso compartido de servidor correspondiente a la **Dirección URL de instalación** especificada en la página **Publicar**, introduzca esa dirección URL aquí. Esta opción solo está disponible cuando está seleccionada la opción **Conceder a la aplicación acceso al sitio de origen**.

## <a name="see-also"></a>Vea también

- [Página Seguridad, Diseñador de proyectos](../../ide/reference/security-page-project-designer.md)