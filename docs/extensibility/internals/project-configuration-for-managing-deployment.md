---
title: Configuración de proyecto para administrar la implementación | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ffa661d8bf33219a3a2956cef3e456c9b5f1146
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726012"
---
# <a name="project-configuration-for-managing-deployment"></a>Configuración del proyecto para administrar la implementación
La implementación es el acto de mover físicamente los elementos de salida de un proceso de compilación a la ubicación esperada para la depuración y la instalación. Por ejemplo, una aplicación web podría estar compilada en un equipo local y, a continuación, colocarse en el servidor.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] admite dos maneras en que los proyectos pueden estar implicados en la implementación:

- Como asunto del proceso de implementación.

- Como administrador del proceso de implementación.

  Antes de implementar las soluciones, primero debe agregar un proyecto de implementación para configurar las opciones de implementación. Si el proyecto de implementación aún no existe, se le pregunta si desea crear uno al seleccionar **implementar solución** en el menú **compilar** o hacer clic con el botón secundario en la solución. Al hacer clic en **sí** , se abre el cuadro de diálogo **Agregar nuevo proyecto** con el proyecto del **Asistente para implementar remoto** seleccionado.

  El Asistente para la implementación remota le pide el tipo de aplicación (Windows o Web), los grupos de resultados del proyecto que se van a incluir, los archivos adicionales que desee incluir y el equipo remoto en el que desea realizar la implementación. La última página del asistente muestra un resumen de las opciones seleccionadas.

  Los proyectos que están sujetos a un proceso de implementación producen elementos de salida que se deben pasar a un entorno alternativo. Estos elementos de salida se describen como parámetros para la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>, cuyo propósito principal es permitir que los proyectos agrupen salidas. Para obtener más información sobre la implementación de `IVsProjectCfg2`, vea [configuración del proyecto para la salida](../../extensibility/internals/project-configuration-for-output.md).

  Los proyectos de implementación, que administran el proceso de implementación, habilitan el comando implementar y responden cuando se selecciona este comando. Los proyectos de implementación implementan la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> para realizar la implementación y realizar llamadas a la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> para informar de los eventos de estado de implementación.

  Las configuraciones pueden especificar las dependencias que afectan a las operaciones de compilación o implementación. Las dependencias de compilación o implementación son proyectos que deben compilarse o implementarse antes o después de que se compilen o implementen las propias configuraciones. Las dependencias de compilación entre proyectos se describen con la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> e implementan las dependencias con la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency>. Para obtener más información, vea [configuración del proyecto para la compilación](../../extensibility/internals/project-configuration-for-building.md).

## <a name="see-also"></a>Vea también
- [Administración de opciones de configuración](../../extensibility/internals/managing-configuration-options.md)
- [Configuración del proyecto para la compilación](../../extensibility/internals/project-configuration-for-building.md)
- [Configuración del proyecto para la salida](../../extensibility/internals/project-configuration-for-output.md)