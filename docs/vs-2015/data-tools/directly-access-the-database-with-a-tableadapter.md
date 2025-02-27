---
title: Acceder directamente a la base de datos con un TableAdapter | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- databases [Visual Basic], accessing with a TableAdapter
- DBDirect methods
- datasets [Visual Basic], adding to projects
- data [Visual Studio], saving
- TableAdapter.Delete method
- GenerateDbDirectMethods property
- TableAdapter.Insert method
- TableAdapter.GenerateDBDirectMethods property
- TableAdapter.Update method
- saving data
- TableAdapters
ms.assetid: 012c5924-91f7-4790-b2a6-f51402b7014b
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 58500e59a624dac55824033b8b9667754a9040c5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657375"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Acceder directamente a la base de datos con un TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Además de `InsertCommand`, `UpdateCommand` y `DeleteCommand`, los TableAdapters se crean con métodos que se pueden ejecutar directamente en la base de datos. Se puede llamar a estos métodos (`TableAdapter.Insert`, `TableAdapter.Update` y `TableAdapter.Delete`) para manipular los datos directamente en la base de datos.

 Si no desea crear estos métodos directos, establezca la propiedad `GenerateDbDirectMethods` del TableAdapter en `false` en la ventana **propiedades** . Si se agregan consultas a un TableAdapter además de a la consulta principal del TableAdapter, son consultas independientes que no generan estos métodos DbDirect.

## <a name="sendcommandsdirectly-to-a-database"></a>Sendcommandsdirectly a una base de datos
 Llame al método DbDirect de TableAdapter que realiza la tarea que está intentando realizar.

#### <a name="to-insert-new-records-directly-into-a-database"></a>Para insertar nuevos registros directamente en una base de datos

- Llame al método `Insert` del TableAdapter, pasando los valores de cada columna como parámetros. En el procedimiento siguiente se usa un ejemplo en la tabla `Region` de las bases de datos Northwind.

    > [!NOTE]
    > Si no tiene una instancia disponible, cree una instancia del TableAdapter que desee usar.

     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]

#### <a name="to-update-records-directly-in-a-database"></a>Para actualizar registros directamente en una base de datos

- Llame al método `Update` del TableAdapter, pasando los valores nuevos y originales de cada columna como parámetros.

    > [!NOTE]
    > Si no tiene una instancia disponible, cree una instancia del TableAdapter que desee usar.

     [!code-csharp[VbRaddataSaving#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#18)]
     [!code-vb[VbRaddataSaving#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#18)]

#### <a name="to-delete-records-directly-from-a-database"></a>Para eliminar registros directamente de una base de datos

- Llame al método `Delete` del TableAdapter, pasando los valores de cada columna como parámetros del método `Delete`. En el procedimiento siguiente se usa un ejemplo en la tabla `Region` de las bases de datos Northwind.

    > [!NOTE]
    > Si no tiene una instancia disponible, cree una instancia del TableAdapter que desee usar.

     [!code-csharp[VbRaddataSaving#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#21)]
     [!code-vb[VbRaddataSaving#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#21)]

## <a name="see-also"></a>Vea también
 [Llenar conjuntos de datos mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)
