---
title: Configuración de soluciones | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solution configurations
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 243af2549862f1d29c44ba5bfc3060d87d5c6f85
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723830"
---
# <a name="solution-configuration"></a>Configuración de soluciones
Las configuraciones de soluciones almacenan propiedades de nivel de solución. Dirigen el comportamiento de la tecla **Inicio** (F5) y los comandos de **compilación** . De forma predeterminada, estos comandos compilan e inician la configuración de depuración. Ambos comandos se ejecutan en el contexto de una configuración de soluciones. Esto significa que el usuario puede esperar F5 para iniciar y compilar la configuración de la solución activa. El entorno está diseñado para optimizar las soluciones en lugar de los proyectos cuando se trata de compilar y ejecutar.

 La barra de herramientas de Visual Studio estándar contiene un botón Inicio y una lista desplegable Configuración de soluciones situada a la derecha del botón Inicio. Esta lista permite a los usuarios elegir la configuración que se va a iniciar cuando se presiona F5, crear sus propias configuraciones de soluciones o editar una configuración existente.

> [!NOTE]
> No hay interfaces de extensibilidad para crear o editar las configuraciones de soluciones. Debe utilizar `DTE.SolutionBuilder`. Sin embargo, hay API de extensibilidad para administrar la compilación de la solución. Para obtener más información, vea <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>.

 A continuación se muestra cómo puede implementar las configuraciones de soluciones compatibles con el tipo de proyecto:

- Proyecto

   Muestra los nombres de los proyectos que se encuentran en la solución actual.

- Configuración

   Para proporcionar la lista de configuraciones admitidas por el tipo de proyecto y mostradas en las páginas de propiedades, implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>.

   En la columna configuración se muestra el nombre de la configuración del proyecto que se va a compilar en esta configuración de solución y se enumeran todas las configuraciones de proyecto al hacer clic en el botón de flecha. El entorno llama al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A> para rellenar esta lista. Si el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> indica que el proyecto admite la edición de la configuración, las selecciones nuevas o de edición también se muestran en el encabezado configuración. Cada uno de estos cuadros de diálogo de inicio de selecciones que llaman a métodos de la interfaz de `IVsCfgProvider2` para editar las configuraciones del proyecto.

   Si un proyecto no admite configuraciones, la columna de configuración muestra ninguno y está deshabilitada.

- Plataforma

   Muestra la plataforma para la que se compilan las configuraciones de proyecto seleccionadas y enumera todas las plataformas disponibles para el proyecto al hacer clic en el botón de flecha. El entorno llama al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A> para rellenar esta lista. Si el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> indica que el proyecto admite la edición de plataforma, las selecciones nuevas o de edición también se muestran en el encabezado plataforma. Cada uno de estos cuadros de diálogo de inicio de selecciones que llaman a métodos `IVsCfgProvider2` para editar las plataformas disponibles del proyecto.

   Si un proyecto no admite plataformas, la columna plataforma de ese proyecto muestra ninguno y está deshabilitada.

- Compilar

   Especifica si el proyecto se compila o no mediante la configuración de la solución actual. Los proyectos no seleccionados no se generan cuando se invocan los comandos de compilación en el nivel de la solución a pesar de las dependencias del proyecto que contengan. Los proyectos que no se han seleccionado para compilarse todavía se incluyen en la depuración, ejecución, empaquetado e implementación de la solución.

- Implementar

   Especifica si el proyecto se implementará o no cuando se usen los comandos iniciar o implementar con la configuración de compilación de la solución seleccionada. La casilla de este campo estará disponible si el proyecto admite la implementación implementando la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> en su <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> objeto.

  Una vez que se agrega una nueva configuración de soluciones, el usuario puede seleccionarla en el cuadro de lista desplegable Configuración de soluciones de la barra de herramientas estándar para compilar o iniciar esa configuración.

## <a name="see-also"></a>Vea también
- [Administración de opciones de configuración](../../extensibility/internals/managing-configuration-options.md)
- [Configuración del proyecto para la compilación](../../extensibility/internals/project-configuration-for-building.md)
- [Objeto de configuración del proyecto](../../extensibility/internals/project-configuration-object.md)