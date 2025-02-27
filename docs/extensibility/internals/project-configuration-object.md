---
title: Objeto de configuración del proyecto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e3321b70b51d194c67f1deee8ed33e240762b16b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725841"
---
# <a name="project-configuration-object"></a>Objeto de configuración del proyecto
El objeto de configuración de proyecto administra la presentación de la información de configuración en la interfaz de usuario.

 ![Configuración de proyecto de Visual Studio](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg") Páginas de propiedades de configuración del proyecto

 El proveedor de configuración del proyecto administra las configuraciones del proyecto. El entorno y otros paquetes, para obtener acceso y recuperar información sobre las configuraciones de un proyecto, llame a las interfaces asociadas al objeto del proveedor de configuración del proyecto.

> [!NOTE]
> No se pueden crear ni editar archivos de configuración de soluciones mediante programación. Debe utilizar `DTE.SolutionBuilder`. Consulte [configuración de soluciones](../../extensibility/internals/solution-configuration.md) para obtener más información.

 Para publicar un nombre para mostrar que se va a usar en la interfaz de usuario de configuración, el proyecto debe implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>. El entorno llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, que devuelve una lista de punteros de `IVsCfg` que puede usar para obtener los nombres para mostrar de la información de configuración y plataforma que se mostrarán en la interfaz de usuario del entorno. La configuración activa y la plataforma vienen determinadas por la configuración del proyecto almacenada en la configuración de soluciones activa. El método <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> se puede usar para recuperar la configuración del proyecto activo.

 Opcionalmente, el objeto <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> se puede implementar en el objeto <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> con el objeto <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> para que pueda recuperar un objeto `IVsProjectCfg2` basado en el nombre de la configuración del proyecto canónico.

 Otra manera de proporcionar el entorno y otros proyectos con acceso a las configuraciones de proyecto es para que los proyectos proporcionen una implementación del método `IVsCfgProvider2::GetCfgs` para devolver uno o más objetos de configuración. Los proyectos también pueden implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>, que hereda de `IVsProjectCfg` y, por tanto, de `IVsCfg`, para proporcionar información específica de la configuración. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> admite plataformas y funcionalidad para agregar, eliminar y cambiar el nombre de las configuraciones de proyecto.

> [!NOTE]
> Dado que Visual Studio ya no está limitado a dos tipos de configuración, el código que procesa las configuraciones no se debe escribir con suposiciones sobre el número de configuraciones ni debe escribirse con la suposición de que un proyecto que solo tiene uno. la configuración es necesariamente debug o Retail. Esto hace que el uso de <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> obsoleto.

 La llamada a `QueryInterface` en el objeto devuelto desde `IVsGetCfgProvider::GetCfgProvider` recupera `IVsCfgProvider2`. Si no se encuentra `IVsGetCfgProvider` llamando a `QueryInterface` en el objeto de proyecto de `IVsProject3`, puede tener acceso al objeto de proveedor de configuración llamando a `QueryInterface` en el objeto de explorador raíz de la jerarquía para el objeto devuelto por `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)` o a través de un puntero a la configuración. proveedor devuelto para `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`.

 `IVsProjectCfg2` proporciona principalmente acceso a objetos de administración de compilación, depuración e implementación, y permite a los proyectos la libertad de agrupar las salidas. Los métodos de `IVsProjectCfg` y `IVsProjectCfg2` se pueden usar para implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> para administrar el proceso de compilación y <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> punteros para los grupos de salida de una configuración.

 El proyecto debe devolver el mismo número de grupos para cada configuración que admita aunque el número de salidas contenidas dentro de un grupo puede variar de una configuración a una configuración. Los grupos también deben tener la misma información de identificador (nombre canónico, nombre para mostrar e información de grupo) de la configuración a la configuración de un proyecto. Para obtener más información, vea [configuración del proyecto para la salida](../../extensibility/internals/project-configuration-for-output.md).

 Para habilitar la depuración, las configuraciones deben implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>. `IVsDebuggableProjectCfg` es una interfaz opcional implementada por los proyectos para permitir que el depurador inicie una configuración y se implementa en el objeto de configuración con `IVsCfg` y `IVsProjectCfg`. El entorno lo llama cuando el usuario elige iniciar el depurador presionando F5.

 `ISpecifyPropertyPages` y `IDispatch` se usan junto con las páginas de propiedades para recuperar y Mostrar información dependiente de la configuración al usuario. Para obtener más información, vea [páginas de propiedades](../../extensibility/internals/property-pages.md).

## <a name="see-also"></a>Vea también
- [Administración de opciones de configuración](../../extensibility/internals/managing-configuration-options.md)
- [Configuración del proyecto para la compilación](../../extensibility/internals/project-configuration-for-building.md)
- [Configuración del proyecto para la salida](../../extensibility/internals/project-configuration-for-output.md)
- [Páginas de propiedades](../../extensibility/internals/property-pages.md)
- [Configuración de soluciones](../../extensibility/internals/solution-configuration.md)