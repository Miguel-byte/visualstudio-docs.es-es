---
title: Windows en el registro de herramientas | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering
ms.assetid: c4bb8add-7148-49e4-a377-01d059fd5524
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8cedb95ccd98c3d5bd5e05086cfd1b53b0f97cd9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68186383"
---
# <a name="tool-windows-in-the-registry"></a>Ventanas de herramientas del Registro
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los VSPackages que proporcionan las ventanas de herramientas se debe registrar con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] como proveedores de la ventana de herramientas. Ventanas de herramientas creadas con la plantilla de paquete de Visual Studio hace esto de forma predeterminada. Proveedores de ventana de herramientas tienen las claves del registro del sistema que especifican los atributos de visibilidad, como tamaño predeterminado de la ventana de herramienta y la ubicación, el GUID de la ventana que actúa como el panel de ventana de herramientas y el estilo de acoplamiento.  
  
 Durante el desarrollo, los proveedores de ventana de herramientas administrada registran ventanas de herramientas mediante la adición de atributos al código fuente y, a continuación, ejecute la utilidad RegPkg.exe en el ensamblado resultante. Para obtener más información, consulte [registrando una ventana de herramientas](../extensibility/registering-a-tool-window.md).  
  
## <a name="registering-unmanaged-tool-window-providers"></a>Registrar proveedores de ventana de herramienta no administrado  
 Proveedores de ventana de herramientas no administrado deben registrar con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] en la sección de ToolWindows del registro del sistema. El siguiente fragmento del archivo .reg muestra cómo se puede registrar una ventana de herramientas dinámica:  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]  
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"  
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"  
"Float"="250, 250, 410, 430"  
"DontForceCreate"=dword:00000001  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]  
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000  
```  
  
 En la primera clave en el ejemplo anterior, el número de versión es la versión de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], como 7.1 u 8.0, la subclave {f0e1e9a1-9860-484d-ad5d-367d79aabf55} es el GUID del panel de la ventana de herramienta (DynamicWindowPane) y el valor de predeterminada {} 01069cdd-95ce-4620-ac21-ddff6c57f012} es el GUID del VSPackage que proporciona la ventana de herramientas. Para obtener una explicación de las subclaves Float y DontForceCreate, consulte [configuración de pantalla de ventana de herramienta](../extensibility/tool-window-display-configuration.md).  
  
 La segunda clave opcional, ToolWindows\Visibility, especifica el GUID de los comandos que requieren la ventana de herramientas debe hacer visible. En este caso, no hay ningún comando especificado. Para obtener más información, consulte [configuración de pantalla de ventana de herramienta](../extensibility/tool-window-display-configuration.md).  
  
## <a name="see-also"></a>Vea también  
 [Elementos fundamentales de VSPackage](../misc/vspackage-essentials.md)
