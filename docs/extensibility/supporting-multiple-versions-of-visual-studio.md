---
title: Compatibilidad con varias versiones de Visual Studio | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f7212445cd507a0d7d185bbd73fa2292e5b783f4
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2019
ms.locfileid: "66745988"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Compatibilidad con varias versiones de Visual Studio
El término *side-by-side* significa que puede instalar y mantener varias versiones de un producto en el mismo equipo. Para los paquetes VSPackage, que significa que un usuario puede tener varias versiones de Visual Studio instaladas en el mismo equipo. Sin embargo, no puede tener versiones en paralelo de los VSPackages cargados en una única versión de Visual Studio.

 Antes de realizar el VSPackage puede cargarse en las versiones en paralelo de Visual Studio, tenga en cuenta lo siguiente:

- Debe determinar qué estrategia de implementación en paralelo que desea seguir.

   Para obtener más información, consulte [VSPackages con control de versiones y elegir entre compartir](../extensibility/choosing-between-shared-and-versioned-vspackages.md).

- Los formatos de archivo de solución y proyecto deben ajustarse a su estrategia de implementación.

   Para obtener más información, consulte [actualizar proyectos personalizados](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects) y [registrar extensiones de nombre de archivo para las implementaciones de Side-By-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).

- El instalador debe controlar la estrategia de implementación para que los componentes con control de versiones, además de componentes compartidos por todas las versiones, están correctamente instalados y registrados.

   Para obtener más información, consulte [Installing VSPackages con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) y también [componente administración](../extensibility/internals/component-management.md).

  > [!NOTE]
  > Instalar una versión de Visual Studio, también instala una versión de .NET Framework correspondiente. Por ejemplo, la instalación de Visual Studio 2010 y Visual Studio 2012 en el mismo equipo también instala las versiones 4.0 y 4.5 de .NET Framework, respectivamente.

## <a name="in-this-section"></a>En esta sección
- [Elegir entre compartir y con control de versiones VSPackages](../extensibility/choosing-between-shared-and-versioned-vspackages.md) explica cómo resolver problemas en paralelo en el VSPackage.

- [Registrar las extensiones de nombre de archivo para las implementaciones de Side-By-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) describe cómo el VSPackage puede registrar las asociaciones de archivo en un escenario en paralelo.

## <a name="related-sections"></a>Secciones relacionadas
- [Instalación de VSPackages con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)
