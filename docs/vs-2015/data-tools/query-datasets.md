---
title: Consultar conjuntos de valores | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7ccd5deffb0127769e2cd9dff3bf2accf75617eb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607447"
---
# <a name="query-datasets"></a>Consultar conjuntos de datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para buscar registros específicos en un conjunto de registros, use el método FindBy en DataTable, escriba su propio bucle foreach en la colección Rows de la tabla o use [LINQ to DataSet](https://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17). LINQ to DataSet.

## <a name="dataset-case-sensitivity"></a>Distinción de mayúsculas y minúsculas
 Dentro de un conjunto de DataSet, los nombres de tabla y de columna no distinguen mayúsculas de minúsculas de forma predeterminada, es decir, una tabla de un conjunto de información denominada "Customers" también puede denominarse "Customers". Esto coincide con las convenciones de nomenclatura de muchas bases de datos, incluido SQL Server.In SQL Server, el comportamiento predeterminado es que los nombres de los elementos de datos no se pueden distinguir solo por el uso de mayúsculas y minúsculas.

> [!NOTE]
> A diferencia de los conjuntos de datos, los documentos XML distinguen mayúsculas de minúsculas, por lo que los nombres de los elementos de datos definidos en esquemas distinguen mayúsculas de minúsculas. Por ejemplo, el protocolo de esquema permite que el esquema defina una tabla denominada "Customers" y otra tabla denominada "Customers". Esto puede dar lugar a conflictos de nombres cuando se utiliza un esquema que contiene elementos que solo se diferencian por el uso de mayúsculas y minúsculas para generar una clase de conjunto de resultados.

 Sin embargo, la distinción entre mayúsculas y minúsculas puede ser un factor de cómo se interpretan los datos en el conjunto de datos. Por ejemplo, si filtra los datos en una tabla de conjunto de datos, los criterios de búsqueda podrían devolver resultados diferentes en función de si la comparación distingue entre mayúsculas y minúsculas. Puede controlar la distinción de mayúsculas y minúsculas del filtrado, la búsqueda y la ordenación estableciendo la propiedad <xref:System.Data.DataSet.CaseSensitive%2A> del conjunto de valores. Todas las tablas del conjunto de valores heredan el valor de esta propiedad de forma predeterminada. (Puede invalidar esta propiedad para cada tabla individual estableciendo la propiedad <xref:System.Data.DataTable.CaseSensitive%2A> de la tabla).

## <a name="locate-a-specific-row-in-a-data-table"></a>Buscar una fila específica en una tabla de datos

#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>Para buscar una fila en un conjunto de tipos con un valor de clave principal

- Para buscar una fila, llame al método `FindBy` fuertemente tipado que usa la clave principal de la tabla.

     En el ejemplo siguiente, la columna `CustomerID` es la clave principal de la tabla `Customers`. Esto significa que el método de `FindBy` generado es `FindByCustomerID`. En el ejemplo se muestra cómo asignar un <xref:System.Data.DataRow> específico a una variable mediante el método `FindBy` generado.

     [!code-csharp[VbRaddataEditing#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#18)]
     [!code-vb[VbRaddataEditing#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#18)]

#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>Para buscar una fila en un conjunto de filas sin tipo con un valor de clave principal

- Llame al método <xref:System.Data.DataRowCollection.Find%2A> de una colección <xref:System.Data.DataRowCollection>, pasando la clave principal como parámetro.

     En el ejemplo siguiente se muestra cómo declarar una nueva fila denominada `foundRow` y asignarle el valor devuelto del método <xref:System.Data.DataRowCollection.Find%2A>. Si se encuentra la clave principal, el contenido del índice de columna 1 se muestra en un cuadro de mensaje.

     [!code-csharp[VbRaddataEditing#19](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#19)]
     [!code-vb[VbRaddataEditing#19](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#19)]

## <a name="findrows-by-column-values"></a>FindRows por valores de columna

#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>Para buscar filas basadas en los valores de una columna

- Las tablas de datos se crean con el método <xref:System.Data.DataTable.Select%2A>, que devuelve una matriz de <xref:System.Data.DataRow>s basándose en la expresión que se pasa al método <xref:System.Data.DataTable.Select%2A>. Para obtener más información sobre la creación de expresiones válidas, vea la sección "Sintaxis de expresiones" de la página sobre la propiedad <xref:System.Data.DataColumn.Expression%2A>.

     En el ejemplo siguiente se muestra cómo utilizar el método <xref:System.Data.DataTable.Select%2A> del <xref:System.Data.DataTable> para buscar filas específicas.

     [!code-csharp[VbRaddataEditing#20](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#20)]
     [!code-vb[VbRaddataEditing#20](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#20)]

## <a name="access-related-records"></a>Acceder a los registros relacionados
 Cuando las tablas de un conjunto de registros están relacionadas, un objeto <xref:System.Data.DataRelation> puede hacer que los registros relacionados estén disponibles en otra tabla. Por ejemplo, un conjunto de DataSet que contiene `Customers` y `Orders` tablas pueden estar disponibles.

 Puede utilizar un objeto <xref:System.Data.DataRelation> para buscar registros relacionados llamando al método <xref:System.Data.DataRow.GetChildRows%2A> de una <xref:System.Data.DataRow> de la tabla primaria. Este método devuelve una matriz de registros secundarios relacionados. O bien, puede llamar al método <xref:System.Data.DataRow.GetParentRow%2A> de una <xref:System.Data.DataRow> en la tabla secundaria. Este método devuelve un <xref:System.Data.DataRow> único de la tabla primaria.

 En esta página se proporcionan ejemplos de uso de conjuntos de DataSet con tipo. Para obtener información sobre cómo navegar por las relaciones en conjuntos de datos sin tipo, vea [explorar objetos DataRelation](https://msdn.microsoft.com/library/e5e673f4-9b44-45ae-aaea-c504d1cc5d3e).

> [!NOTE]
> Si está trabajando en una aplicación Windows Forms y usa las características de enlace de datos para mostrar los datos, el formulario generado por el diseñador podría proporcionar la funcionalidad suficiente para la aplicación. Para obtener más información, vea [enlazar controles a datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

 En los siguientes ejemplos de código se muestra cómo desplazarse por las relaciones hacia arriba y hacia abajo en conjuntos de tipos de DataSet. En los ejemplos de código se usa <xref:System.Data.DataRow>s con tipo (`NorthwindDataSet.OrdersRow`) y los métodos generados `FindBy`*PrimaryKey* (`FindByCustomerID`) para buscar una fila deseada y devolver los registros relacionados. Los ejemplos se compilan y ejecutan correctamente solo si tiene:

- Una instancia de un conjunto de información denominado `NorthwindDataSet` con una tabla de `Customers`.

- Tabla de `Orders`.

- Una relación denominada `FK_Orders_Customers`relating las dos tablas disponibles para el ámbito del código

Además, ambas tablas deben rellenarse con datos para que se devuelvan los registros.

#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>Para devolver los registros secundarios de un registro primario seleccionado

- Llame al método <xref:System.Data.DataRow.GetChildRows%2A> de una fila de datos `Customers` específica y devuelva una matriz de filas de la tabla `Orders`:

     [!code-csharp[VbRaddataDatasets#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#6)]
     [!code-vb[VbRaddataDatasets#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#6)]

#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>Para devolver el Registro primario de un registro secundario seleccionado

- Llame al método <xref:System.Data.DataRow.GetParentRow%2A> de una fila de datos `Orders` específica y devuelva una sola fila de la tabla `Customers`:

     [!code-csharp[VbRaddataDatasets#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#7)]
     [!code-vb[VbRaddataDatasets#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#7)]
