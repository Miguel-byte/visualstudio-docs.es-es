---
title: Cambiar el tipo de valor devuelto del método DataContext (Object Relational Designer)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 304cd62e83ae2e256e40cdbb8f046b637cbd8d58
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648381"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Procedimiento para cambiar el tipo de valor devuelto de un método DataContext (Object Relational Designer)
El tipo de valor devuelto de un método <xref:System.Data.Linq.DataContext> (creado basándose en un procedimiento almacenado o una función) difiere en función de dónde se coloque el procedimiento almacenado o la función en Object Relational **Designer**. Si se coloca un elemento directamente en una clase de entidad existente, se crea un método de <xref:System.Data.Linq.DataContext> que tiene el tipo de valor devuelto de la clase de entidad (si el esquema de los datos devueltos por el procedimiento almacenado o la función coincide con la forma de la clase de entidad). Si coloca un elemento en un área vacía de Object Relational **Designer**, se creará un método <xref:System.Data.Linq.DataContext> que devuelve un tipo generado automáticamente. Se puede cambiar el tipo de valor devuelto de un método de <xref:System.Data.Linq.DataContext> después de agregarlo al panel de métodos. Para examinar o cambiar el tipo de valor devuelto de un método <xref:System.Data.Linq.DataContext>, selecciónelo y haga clic en la propiedad **Tipo devuelto** en la ventana **Propiedades**.

> [!NOTE]
> Mediante la ventana **Propiedades**, no se pueden revertir los métodos de <xref:System.Data.Linq.DataContext> cuyo tipo de valor devuelto está establecido en una clase de entidad para que devuelvan el tipo generado automáticamente. Para revertir un método de <xref:System.Data.Linq.DataContext>, de modo que devuelva un tipo generado automáticamente, debe arrastrar de nuevo el objeto de base de datos original hasta **Object Relational Designer**.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Para cambiar el tipo de valor devuelto de un método de DataContext del tipo generado automáticamente a una clase de entidad

1. Seleccione el método de <xref:System.Data.Linq.DataContext> en el panel de métodos.

2. Seleccione **Tipo devuelto** en la ventana **Propiedades** y después seleccione una clase de entidad disponible en la lista **Tipo devuelto**. Si la clase de entidad deseada no está en la lista, agréguela a o créela en Object Relational **Designer** para agregarla a la lista.

3. Guarde el archivo *.dbml*.

## <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>Para volver a cambiar el tipo de valor devuelto de un método de DataContext de una clase de entidad al tipo generado automáticamente

1. Seleccione el método <xref:System.Data.Linq.DataContext> en el panel **Métodos** y elimínelo.

2. Arrastre el objeto Database desde **Explorador de servidores** o **Explorador de bases de datos** a un área vacía de Object Relational **Designer**.

3. Guarde el archivo *.dbml*.

## <a name="see-also"></a>Vea también

- [LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) (Herramientas LINQ to SQL en Visual Studio)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [DataContext methods (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md) (Métodos DataContext [Object Relational Designer])
- [Cómo: Crear métodos DataContext asignados a funciones y procedimientos almacenados (Object Relational Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)