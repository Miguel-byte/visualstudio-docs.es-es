---
title: Utilidad RegPkg | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f811eb37da730d63e199a0e378b8a9122143649e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724443"
---
# <a name="regpkg-utility"></a>Utilidad RegPkg
> [!NOTE]
> La mejor manera de registrar paquetes en Visual Studio es mediante el uso de archivos. pkgdef. Esto permite la implementación de la extensión sin tener que obtener acceso al registro del sistema, que es un requisito para la implementación de VSIX. Los archivos Pkgdef se crean mediante la [utilidad CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md). Para obtener más información sobre la implementación de paquetes de Visual Studio, vea [envío de extensiones de Visual Studio](../../extensibility/shipping-visual-studio-extensions.md).

 La utilidad RegPkg. exe registra un VSPackage con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y lo prepara para la implementación. Esta utilidad se usa en segundo plano durante el desarrollo del VSPackage. Se ejecuta como parte del proceso de compilación para que pueda compilar y ejecutar un VSPackage en el subárbol experimental.

 RegPkg puede generar scripts del registro del sistema en varios formatos. Puede incorporar estos scripts en proyectos de implementación como proyectos. msi o Windows Installer archivos de conjunto de herramientas XML.

 RegPkg. exe se encuentra normalmente en \<*ruta de instalación de Visual Studio SDK*> \VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg sigue esta sintaxis:

```
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath
```

 /root: root realiza el registro en el especificado

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] raíz.

 /regfile: FileName crea un archivo. reg en lugar de actualizar el registro.  No se puede usar con/vrgfile o/rgsfile o/wixfile.

 /rgsfile: FileName crea un archivo. RGS en lugar de actualizar el registro.  No se puede usar con/vrgfile o/regfile ni/wixfile.

 /vrgfile: FileName crea un archivo. VRG en lugar de actualizar el registro.  No se puede usar con/regfile o/rgsfile ni/wixfile.

 /RGM crea un archivo. RGM además del archivo RGS.  Debe combinarse con/rgsfile.

 /wixfile: FileName crea Windows Installer un archivo compatible con el conjunto de herramientas XML en lugar de actualizar el registro.  No se puede usar con/regfile o/rgsfile ni/vrgfile.

 /codebase fuerza el registro con el código base en lugar del ensamblado.

 /Assembly fuerza el registro con ensamblado en lugar de código base.

 /unregister anula el registro de este paquete.  No se puede usar

 con/regfile o/vrgfile o/rgsfile o/wixfile.

## <a name="see-also"></a>Vea también
- [VSPackages](../../extensibility/internals/vspackages.md)
- [Solución de problemas del registro de paquete RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)