---
title: Crear consultas parametrizadas de TableAdapter
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- TableAdapters, parameterized queries
- data [Visual Studio], searching data
- queries [Visual Studio], creating
- TableAdapters, searching data
- queries [Visual Studio], TableAdapters
ms.assetid: 104d1d19-b5a9-4071-b81e-1b3af08e9c7b
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 560587e70365a485c3391a0623b959f88d417698
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671064"
---
# <a name="create-parameterized-tableadapter-queries"></a>Crear consultas parametrizadas de TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Una consulta parametrizada devuelve datos que cumplen las condiciones de una cláusula WHERE dentro de la consulta. Por ejemplo, puede parametrizar una lista de clientes para mostrar solo los clientes de una determinada ciudad; para ello, agrega `WHERE City = @City` al final de la instrucción SQL que devuelve una lista de clientes.

Cree consultas de TableAdapter parametrizadas en el Diseñador de DataSet. También puede crearlos en una aplicación Windows con el comando **parametrizar origen de datos** en el menú **datos** . El comando **parametrizar origen de datos** crea controles en el formulario, donde puede especificar los valores de los parámetros y ejecutar la consulta.

> [!NOTE]
> Al construir una consulta parametrizada, utilice la notación de parámetros que es específica de la base de datos con la que se va a codificar. Por ejemplo, los orígenes de datos de Access y Oledb usan el signo de interrogación “?” para denotar los parámetros, por lo que la cláusula WHERE tendría esta apariencia: `WHERE City = ?`.

> [!NOTE]
> Los cuadros de diálogo y los comandos de menú que se ven pueden diferir de los descritos en la ayuda, en función de la configuración activa o de la edición que esté usando. Para cambiar la configuración, vaya al menú **herramientas** y seleccione **importar y exportar configuraciones**. Para obtener más información, vea [Personalizar la configuración de desarrollo en Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="create-a-parameterized-tableadapter-query"></a>Crear una consulta parametrizada de TableAdapter

- Cree un nuevo TableAdapter y agregue una cláusula WHERE con los parámetros deseados a la instrucción SQL. Para obtener más información, vea [crear y configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md).

     o bien

- Agregue una consulta a un TableAdapter existente, y agregue una cláusula WHERE con los parámetros deseados a la instrucción SQL.

### <a name="create-a-parameterized-query-while-designing-a-data-bound-form"></a>Crear una consulta con parámetros al diseñar un formulario enlazado a datos

1. Seleccione en el formulario un control que ya esté enlazado a un conjunto de datos. Para obtener más información, vea [enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

2. En el menú **datos** , seleccione**Agregar consulta**.

3. Complete el cuadro de diálogo **Generador de criterios de búsqueda** y agregue una cláusula WHERE con los parámetros deseados a la instrucción SQL.

### <a name="add-a-query-to-an-existing-data-bound-form"></a>Agregar una consulta a un formulario enlazado a datos existente

1. Abra el formulario en el **Diseñador de Windows Forms**.

2. En el menú **datos** , seleccione **Agregar consulta** o **etiquetas inteligentes de datos**.

   > [!NOTE]
   > Si **Agregar consulta** no está disponible en el menú **Datos**, seleccione un control en el formulario que muestra el origen de datos al que quiere agregar parametrización. Por ejemplo, si el formulario muestra datos en un control <xref:System.Windows.Forms.DataGridView>, selecciónelo. Si el formulario muestra datos en controles individuales, seleccione un control enlazado a datos.

3. En el área **seleccionar tabla de origen de datos** , seleccione el tablethat al que desea agregar la parametrización.

4. Escriba un nombre en el cuadro **Nuevo nombre de consulta** si va a crear una nueva consulta.

    o bien

    Seleccione una consulta en el cuadro **Nombre de consulta existente**.

5. En el cuadro de **texto consulta** , escriba una consulta que toma parámetros.

6. Seleccione **Aceptar**.

    Se agregan al formulario un control para especificar los valores del parámetro y un botón **Cargar**, en un control <xref:System.Windows.Forms.ToolStrip>.

   Los parámetros de TableAdapter pueden tener asignados valores NULL cuando se desea consultar los registros que no tienen ningún valor actual. Por ejemplo, considere la siguiente consulta que tiene un parámetro `ShippedDate` en su cláusula `WHERE`:

   ```sql
   SELECT CustomerID, OrderDate, ShippedDate
   FROM Orders
   WHERE (ShippedDate = @ShippedDate) OR
   (ShippedDate IS NULL)
   ```

Si se tratara de una consulta en un TableAdapter, podría consultar todos los pedidos que no se han enviado con el código siguiente:

   [!code-csharp[VbRaddataTableAdapters#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Form2.cs#8)]
   [!code-vb[VbRaddataTableAdapters#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Form2.vb#8)]

### <a name="enable-a-query-to-accept-null-values"></a>Habilitar una consulta para aceptar valores NULL

1. En el **Diseñador de DataSet**, seleccione la consulta TableAdapter que necesita aceptar valores de parámetro null.

2. En la ventana **propiedades** , seleccione **parámetros**. A continuación, presione el botón de puntos suspensivos ( **...** ) para abrir el editor de la **colección de parámetros**.

3. Seleccione el parámetro que permite valores NULL y establezca la propiedad **AllowDBNull** en `true`.

## <a name="see-also"></a>Vea también

- [Llenar conjuntos de datos mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)