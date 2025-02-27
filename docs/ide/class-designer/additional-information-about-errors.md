---
title: Errores del Diseñador de clases
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.classdesigner.CPlusPlusViewInDiagramNoTypeFound
- vs.classdesigner.CPlusPlusNoTypeFound
- vs.classdesigner.CannotShowBaseType
- vs.classdesigner.MatchOrphanTypesAtLoad
- vs.classdesigner.CannotShowType
- vs.classdesigner.AssociationTypeNotFoundError
- vs.classdesigner.ViewInDiagramNoTypesFound
- vs.classdesigner.CannotImplementInterface
- vs.classdesigner.CannotShowImplementedInterface
- vs.classdesigner.ViewInDiagramUnparsableTypeFound
- vs.classdesigner.AssociationTypeNotFound
- vs.classdesigner.CPlusPlusTypeCannotBeAdded
helpviewer_keywords:
- errors, class diagrams
- errors, Class Designer
- error messages, Class Designer
- error messages, class diagrams
- Class Designer [Visual Studio], errors
- class diagrams, errors
ms.assetid: 79d70e70-704c-4255-ab68-c10d6949470e
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de1c6c5ec6c5639cc8a9e036bcc674c407c1ac8f
ms.sourcegitcommit: 4f82de3fb0cfae226aef1abb40c47e63d2036a5c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72919053"
---
# <a name="class-designer-errors"></a>Errores del Diseñador de clases

El **Diseñador de clases** no hace un seguimiento de la ubicación de los archivos de origen, por lo que modificar la estructura del proyecto o mover los archivos de origen del proyecto puede hacer que el **Diseñador de clases** pierda de vista el tipo. Por ejemplo, es habitual modificar el tipo de origen de una definición de tipo, de clases base y de tipos de asociación. Puede que obtenga un error, como **El Diseñador de clases no puede mostrar este tipo**. Para resolver el error, arrastre otra vez el código fuente modificado o reubicado al diagrama de clases para mostrarlo.

## <a name="resources"></a>Recursos

Encontrará ayuda relacionada con otros errores y advertencias en los siguientes recursos:

- [Trabajar con código de Visual C++](working-with-visual-cpp-code.md) incluye información de solución de problemas sobre la visualización de C++ en un diagrama de clases.
- [Foro del Diseñador de clases de Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsclassdesigner) proporciona un foro para formular preguntas sobre el **Diseñador de clases**.

## <a name="see-also"></a>Vea también

- [Diseñar y ver clases y tipos](designing-and-viewing-classes-and-types.md)
