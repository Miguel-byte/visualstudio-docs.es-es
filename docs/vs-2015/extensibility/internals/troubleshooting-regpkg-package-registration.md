---
title: Solución de problemas de registro de paquete RegPkg | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: troubleshooting
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 241975e475252a18d5e5a91c6e8c4fb40c067a95
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441187"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Solución de problemas del registro de paquete RegPkg
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!NOTE]
> Es la mejor manera de registrar paquetes en Visual Studio mediante el uso de los archivos .pkgdef. Esto permite la implementación de extensión sin necesidad de tener acceso al registro del sistema. Archivos pkgdef se crean mediante el [utilidad CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).  
  
 Para registrar un paquete mediante el uso de RegPkg en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], debe usar la versión de RegPkg que sea adecuado para el paquete.  
  
## <a name="regpkg-versions-related-to-package-versions"></a>Versiones de RegPkg relacionado con las versiones de paquete  
 Hay dos versiones de RegPkg. Se incluye una versión en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Use esta versión para registrar los paquetes que se han creado mediante uno de los siguientes ensamblados:  
  
1. Microsoft.VisualStudioShell.9.0.dll  
  
2. Microsoft.VisualStudioShell.10.0.dll  
  
3. Microsoft.VisualStudioShell.11.0.dll  
  
   No puede registrar paquetes que se han creado mediante el ensamblado Microsoft.VisualStudio.Shell.dll anterior.  
  
   La versión anterior de RegPkg puede registrar paquetes que se han creado mediante el ensamblado Microsoft.VisualStudio.Shell.dll. Sin embargo, que no registre los paquetes creados mediante el uso de las versiones posteriores de ese ensamblado.  
  
## <a name="see-also"></a>Vea también  
 [Publicación de un producto](../../misc/releasing-a-visual-studio-integration-product.md)
