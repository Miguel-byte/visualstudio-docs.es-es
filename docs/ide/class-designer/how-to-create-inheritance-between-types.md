---
title: Procedimiento Crear la herencia entre tipos en el Diseñador de clases
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.inheritanceline
helpviewer_keywords:
- inheritance, relationship defining
- relationships, defining inheritance
ms.assetid: 3786a21c-8022-4bf5-9d13-740fd354e93c
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8a7d7f3facf1408f87ef23dfa8ed8462195c172
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647729"
---
# <a name="how-to-create-inheritance-between-types-in-class-designer"></a>Procedimiento Crear la herencia entre tipos en el Diseñador de clases

Para crear una relación de herencia entre dos tipos de un diagrama de clases mediante el **Diseñador de clases**, conecte el tipo base con su tipo o tipos derivados. Puede haber una relación de herencia entre dos clases, entre una clase y una interfaz o entre dos interfaces.

## <a name="to-create-an-inheritance-between-types"></a>Para crear una herencia entre tipos

1. Desde el proyecto, en el **Explorador de soluciones**, abra un archivo de diagrama de clases (.cd).

     Si no tiene un diagrama de clases, créelo. Vea [Cómo: Agregar diagramas de clases a proyectos](how-to-add-class-diagrams-to-projects.md).

2. En el **Cuadro de herramientas**, en **Diseñador de clases**, haga clic en **Herencia**.

3. En el diagrama de clases, dibuje una línea de herencia entre los tipos que desee, desde:

    - Una clase derivada a la clase base

    - Una clase de implementación a la interfaz implementada

    - Una interfaz de extensión a la interfaz extendida

4. Opcionalmente, cuando tenga un tipo derivado de un tipo genérico, haga clic en la línea de herencia. En la ventana **Propiedades**, establezca la propiedad **Argumentos de tipo** para que coincida con el tipo que quiera para el tipo genérico.

    > [!NOTE]
    > Si una clase abstracta principal contiene como mínimo un miembro abstracto, todos los miembros abstractos se implementan como clases de herencia no abstractas.
    >
    >  Aunque puede visualizar los tipos genéricos existentes, no puede crear tipos genéricos nuevos. Tampoco puede cambiar los parámetros de tipo de los tipos genéricos existentes.

## <a name="see-also"></a>Vea también

- [Herencia](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)
- [Fundamentos de la herencia](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
- [Cómo: Ver la herencia entre tipos](how-to-view-inheritance-between-types.md)
- [Clases de Visual C++ en el Diseñador de clases](visual-cpp-classes.md)