---
title: Insertar nuevos registros en una base de datos | Microsoft Docs
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
- TableAdapters, inserting new records into
- data [Visual Studio], saving
- databases, inserting new records into
- records, inserting
- saving data
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3c686a764f42f50a3e59da3e8b37b219ddb7b11c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651557"
---
# <a name="insert-new-records-into-a-database"></a>Insertar nuevos registros en una base de datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para insertar nuevos registros en una base de datos, puede utilizar el método `TableAdapter.Update` o uno de los métodos DBDirect del TableAdapter (específicamente el método `TableAdapter.Insert`).

 Si la aplicación no usa TableAdapters, puede utilizar objetos de comando (por ejemplo, <xref:System.Data.SqlClient.SqlCommand>) para insertar nuevos registros en la base de datos.

 Si la aplicación usa conjuntos de datos para almacenar datos, use el método `TableAdapter.Update`. El método `Update` envía todos los cambios (actualizaciones, inserciones y eliminaciones) a la base de datos.

 Si la aplicación usa objetos para almacenar datos, o si desea un control más preciso sobre la creación de nuevos registros en la base de datos, use el método `TableAdapter.Insert`.

 Si el TableAdapter no tiene un método `Insert`, significa que el TableAdapter está configurado para usar procedimientos almacenados o que su propiedad `GenerateDBDirectMethods` está establecida en `false`. Intente establecer la propiedad `GenerateDBDirectMethods` del TableAdapter en `true` desde el Diseñador de DataSet y, a continuación, guarde el conjunto de contenido. Esto volverá a generar el TableAdapter. Si el TableAdapter todavía no tiene un método `Insert`, es probable que la tabla no proporcione suficiente información de esquema para distinguir entre las filas individuales (por ejemplo, puede que no haya ninguna clave principal establecida en la tabla).

## <a name="insert-new-records-by-using-tableadapters"></a>Insertar nuevos registros mediante TableAdapters
 Los TableAdapters proporcionan diferentes maneras de insertar nuevos registros en una base de datos, en función de los requisitos de la aplicación.

 Si la aplicación usa conjuntos de datos para almacenar datos, puede simplemente agregar nuevos registros al <xref:System.Data.DataTable> deseado en el conjunto de datos y, a continuación, llamar al método `TableAdapter.Update`. El método `TableAdapter.Update` envía los cambios del <xref:System.Data.DataTable> a la base de datos (incluidos los registros modificados y eliminados).

#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>Para insertar nuevos registros en una base de datos mediante el método TableAdapter. Update

1. Agregue nuevos registros a la <xref:System.Data.DataTable> deseada creando un nuevo <xref:System.Data.DataRow> y agregándolo a la colección de <xref:System.Data.DataTable.Rows%2A>. Para obtener más información, vea [Cómo: Agregar filas a un objeto DataTable](https://msdn.microsoft.com/library/78ebbb43-c402-49cf-81da-0715289487bf).

2. Una vez agregadas las nuevas filas a la <xref:System.Data.DataTable>, llame al método `TableAdapter.Update`. Puede controlar la cantidad de datos que se van a actualizar pasando en una <xref:System.Data.DataSet> completa, en una <xref:System.Data.DataTable>, en una matriz de <xref:System.Data.DataRow>s o en un solo <xref:System.Data.DataRow>.

    En el código siguiente se muestra cómo agregar un nuevo registro a un <xref:System.Data.DataTable> y, a continuación, llamar al método `TableAdapter.Update` para guardar la nueva fila en la base de datos. (En este ejemplo se utiliza la tabla `Region` de la base de datos Northwind).

    [!code-csharp[VbRaddataSaving#14](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#14)]
    [!code-vb[VbRaddataSaving#14](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#14)]

   Si la aplicación utiliza objetos para almacenar datos, puede utilizar el método `TableAdapter.Insert` para crear nuevas filas directamente en la base de datos. El método `Insert` acepta los valores individuales de cada columna como parámetros. Al llamar al método, se inserta un nuevo registro en la base de datos con los valores de parámetro pasados.

   En el procedimiento siguiente se utiliza la tabla `Region` de la base de datos Northwind como ejemplo.

#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>Para insertar nuevos registros en una base de datos mediante el método TableAdapter. Insert

- Llame al método `Insert` del TableAdapter, pasando los valores de cada columna como parámetros.

    > [!NOTE]
    > Si no tiene una instancia disponible, cree una instancia del TableAdapter que desee usar.

     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]

## <a name="insert-new-records-by-using-command-objects"></a>Insertar nuevos registros mediante objetos de comando
 En el ejemplo siguiente se insertan nuevos registros directamente en una base de datos mediante objetos de comando.

 En el procedimiento siguiente se utiliza la tabla `Region` de la base de datos Northwind como ejemplo.

#### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Para insertar nuevos registros en una base de datos mediante objetos de comando

- Cree un nuevo objeto de comando y, a continuación, establezca sus propiedades `Connection`, `CommandType` y `CommandText`.

     [!code-csharp[VbRaddataSaving#16](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#16)]
     [!code-vb[VbRaddataSaving#16](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#16)]

## <a name="net-framework-security"></a>Seguridad de .NET Framework
 Debe tener acceso a la base de datos a la que está intentando conectarse, así como permiso para realizar inserciones en la tabla deseada.

## <a name="see-also"></a>Vea también
 [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)
