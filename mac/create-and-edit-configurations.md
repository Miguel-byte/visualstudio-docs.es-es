---
title: Creación y edición de configuraciones de compilación
description: En este artículo se describe la creación de configuraciones de compilación en Visual Studio para Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: CC1B72D6-12FF-4CCC-A9D4-00F2DC14589F
ms.custom: video
ms.openlocfilehash: 26f6e25bfe1284fc31bcd484b905bf5d75c2ba15
ms.sourcegitcommit: 53bc4c11b82882ab658e34c65ae374060f823531
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2019
ms.locfileid: "71128425"
---
# <a name="creating-and-editing-build-configurations"></a>Creación y edición de configuraciones de compilación

Las configuraciones de compilación proporcionan un control preciso sobre una compilación, lo que permite crear configuraciones adecuadas para diferentes situaciones de prueba y distribución. Puede crear configuraciones de compilación para proyectos individuales o para toda una solución.

Además, puede crear configuraciones nuevas y editar las existentes para proyectos y soluciones mediante el cuadro de diálogo Opciones del proyecto.

>[!NOTE]
>Este tema se aplica a Visual Studio para Mac. Para obtener información sobre Visual Studio en Windows, consulte [Procedimiento para crear y editar configuraciones](/visualstudio/ide/how-to-create-and-edit-configurations).

## <a name="creating-a-project-build-configuration"></a>Creación de la configuración de compilación de un proyecto

Para crear la configuración de compilación de un proyecto, siga estos pasos:

1. Haga clic con el botón derecho en el nodo del proyecto y seleccione **Opciones**. También puede hacer doble clic en el nodo del proyecto para abrir el cuadro de diálogo Opciones del proyecto.

2. En el cuadro de diálogo Opciones del proyecto, seleccione **Compilar > Configuraciones**:

    ![Administrador de configuraciones de Opciones del proyecto](media/create-and-edit-configurations-image2.png)

3. Seleccione **Agregar** para crear una configuración. También puede copiar cualquiera de las configuraciones existentes.

Una vez creada la configuración, puede usar la sección **Compilar** de Opciones del proyecto para adaptar las propiedades en función de la configuración:

![Configuración de opciones de compilación](media/create-and-edit-configurations-image3.png)

## <a name="creating-a-solution-build-configuration"></a>Creación de una configuración de compilación de una solución

Para crear la configuración de compilación de una solución, siga estos pasos:

1. Haga clic con el botón derecho en el nodo de la solución y seleccione **Opciones**. También puede hacer doble clic en el nodo de la solución para abrir el cuadro de diálogo Opciones de la solución.

2. En el cuadro de diálogo Opciones de la solución, seleccione **Compilar > Configuraciones**:

    ![Administrador de configuraciones de Opciones de la solución](media/create-and-edit-configurations-image1.png)

3. Seleccione **Agregar** para crear una configuración. También puede copiar cualquiera de las configuraciones existentes.

Una vez creada la configuración, puede usar la sección **Compilar** del cuadro de diálogo Opciones del proyecto para cada uno de los proyectos a fin de adaptar las propiedades en función de la configuración:

![Configuración de opciones de compilación](media/create-and-edit-configurations-image3.png)

## <a name="renaming-a-build-configuration"></a>Cambio del nombre de una configuración de compilación

Para cambiar el nombre de una configuración, selecciónela en la lista Configuración. Para ello, vaya a **Compilación > Configuraciones** en Opciones del proyecto u Opciones de la solución:

![lista Configuración](media/create-and-edit-configurations-image4.png)

Seleccione el botón **Cambiar nombre**.

![cuadro de diálogo Cambiar nombre](media/create-and-edit-configurations-image5.png)

Después, haga clic en **Aceptar** para confirmar.

## <a name="related-video"></a>Vídeo relacionado

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Launch-Multiple-Projects/player]

## <a name="see-also"></a>Vea también

- [Creación y edición de configuraciones de compilación (Visual Studio en Windows)](/visualstudio/ide/how-to-create-and-edit-configurations)