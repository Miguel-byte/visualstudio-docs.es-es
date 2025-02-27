---
title: Procedimiento Compilación de varias configuraciones simultáneamente
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7f4abd95c2a37366b4f6dfabe141e6418d23301d
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2019
ms.locfileid: "68416759"
---
# <a name="how-to-build-multiple-configurations-simultaneously"></a>Procedimiento Compilación de varias configuraciones simultáneamente

Puede compilar la mayoría de los tipos de proyectos con varias o incluso todas sus configuraciones de compilación al mismo tiempo usando el cuadro de diálogo **Compilación por lotes**. Sin embargo, no puede compilar los siguientes tipos de proyectos en varias configuraciones de compilación al mismo tiempo:

1. Aplicaciones de [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] compiladas para Windows mediante JavaScript.

2. Todos los proyectos de Visual Basic.

   Para más información sobre las configuraciones de compilación, vea [Descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md).

## <a name="to-build-a-project-in-multiple-build-configurations"></a>Para compilar un proyecto en varias configuraciones de compilación

1. En la barra de menús, elija **Compilar** > **Compilación por lotes**.

2. En la columna **Compilar**, seleccione las casillas de las configuraciones en las que quiere compilar un proyecto.

    > [!TIP]
    > Para editar o crear una configuración de compilación para una solución, en la barra de menús elija **Compilar** > **Administrador de configuración** para abrir el cuadro de diálogo **Administrador de configuración**. Después de editar una configuración de compilación para una solución, en el cuadro de diálogo **Compilación por lotes**, elija el botón **Recompilar** para actualizar todas las configuraciones para los proyectos de la solución.

3. Elija los botones **Compilar** o **Recompilar** para compilar el proyecto con las configuraciones que especificó.

## <a name="see-also"></a>Vea también

- [Cómo: Crear y editar configuraciones](../ide/how-to-create-and-edit-configurations.md)
- [Descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md)
- [Compilar varios proyectos en paralelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)