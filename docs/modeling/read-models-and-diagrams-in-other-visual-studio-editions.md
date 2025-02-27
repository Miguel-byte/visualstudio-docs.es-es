---
title: Leer modelos y diagramas en otras ediciones de Visual Studio
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- models, versions of Visual Studio
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29c190115836972f86590233e331f172422efbd6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747435"
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Leer modelos y diagramas en otras ediciones de Visual Studio

Al abrir un modelo en una versión de Visual Studio que no es compatible con la creación de modelos, el modelo se abre en modo de solo lectura. En este modo puede cambiar el diseño de los diagramas pero no se puede cambiar el modelo.

Para ver qué versiones de Visual Studio admiten la creación de modelos, vea [compatibilidad de versiones con las herramientas de arquitectura y modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="obtaining-access-to-a-model-and-diagrams"></a>Acceder a un modelo y a diagramas

Para leer un diagrama de dependencia, primero debe usar Visual Studio para abrir el proyecto de modelado y, a continuación, abrir el diagrama en él.

Por esta razón, si desea leer un diagrama de dependencia, también debe tener acceso al proyecto de modelado en el que se creó. Para ello, puede obtener acceso al proyecto desde el control de código fuente o obtener una copia de los archivos del proyecto.

> [!NOTE]
> Esto no se aplica a los mapas de código ni a los diagramas de clases .NET generados a partir del código. Esos diagramas pueden verse sin necesidad de un proyecto de modelado.

Para leer un diagrama de dependencia, el conjunto mínimo de archivos que necesita es el siguiente:

- Los dos archivos de diagrama del diagrama que desea leer, por ejemplo, **diagram. classdiagram y diagram. classdiagram. layout**.

    > [!NOTE]
    > En el caso de los diagramas de dependencia, también debe tener el archivo denominado _Diagram_ **. layerdiagram. suppresss**.

- Archivo del proyecto de modelado (**modelproj**)

- El archivo de modelo raíz (**ModelDefinition\MyModel.UML**)

- Los archivos de paquete de cualquier paquete al que se hace referencia en el diagrama (**ModelDefinition\MyPackage.UML**)

## <a name="changes-that-you-can-make-in-read-only-mode"></a>Cambios que puede realizar en modo de solo lectura

Si abre un modelo y sus diagramas en una versión de Visual Studio que no es compatible con la creación de modelos, no podrá cambiar el modelo. Es decir, no podrá cambiar los elementos y relaciones que se muestran en los diagramas o en el explorador de modelos. Sin embargo, puede realizar algunos cambios en el diseño de los diagramas:

- Reorganizar las formas y conectores del diagrama.

- Expandir y contraer formas.

Puede guardar estos cambios. Si desea que los cambios sean visibles para otros usuarios, debe enviar al menos los archivos **. layout** actualizados.

## <a name="see-also"></a>Vea también

- [Diagramas de dependencia: referencia](../modeling/layer-diagrams-reference.md)
- [Crear modelos para la aplicación](../modeling/create-models-for-your-app.md)