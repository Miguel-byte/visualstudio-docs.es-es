---
title: Procedimiento Cambiar el tamaño de los controles NamedRange
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- NamedRange control, resizing
- ranges, resizing in Excel
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 80a7fd251d525541b6894c757d7acd148900047c
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252048"
---
# <a name="how-to-resize-namedrange-controls"></a>Procedimiento Cambiar el tamaño de los controles NamedRange
  Aunque se puede establecer el tamaño de un control <xref:Microsoft.Office.Tools.Excel.NamedRange> al agregarlo a un documento de Microsoft Office Excel, podrían ser necesarios cambios posteriores.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 En proyectos de nivel de documento, el tamaño de un rango con nombre se puede cambiar en tiempo de diseño o en tiempo de ejecución También se puede cambiar su tamaño en tiempo de ejecución en los complementos de VSTO de nivel de aplicación.

 En este tema se describen las tareas siguientes:

- [Cambiar el tamaño de los controles NamedRange en tiempo de diseño](#designtime)

- [Cambiar el tamaño de los controles NamedRange en tiempo de ejecución en un proyecto de nivel de documento](#runtimedoclevel)

- [Cambiar el tamaño de los controles NamedRange en tiempo de ejecución en un proyecto de complemento de VSTO](#runtimeaddin)

## <a name="designtime"></a>Cambiar el tamaño de los controles NamedRange en tiempo de diseño
 Para cambiar el tamaño de un rango con nombre, es necesario volver a definir el tamaño en el cuadro de diálogo **Definir nombre** .

### <a name="to-resize-a-named-range-by-using-the-define-name-dialog-box"></a>Para cambiar el tamaño de un rango con nombre mediante el cuadro de diálogo Definir nombre

1. Haga clic en un control <xref:Microsoft.Office.Tools.Excel.NamedRange> .

2. Haga clic en **Administrar rangos con nombre** en el menú contextual.

     Se mostrará el cuadro de diálogo **Definir nombre** .

3. Seleccione el rango con nombre cuyo tamaño quiere cambiar.

4. Desactive el cuadro **Se refiere a** .

5. Seleccione las celdas que quiere usar para definir el tamaño del rango con nombre.

6. Haga clic en **Aceptar**.

## <a name="runtimedoclevel"></a>Cambiar el tamaño de los controles NamedRange en tiempo de ejecución en un proyecto de nivel de documento
 Este tamaño se puede cambiar mediante programación, con la propiedad <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> .

> [!NOTE]
> En la ventana **Propiedades** , la propiedad <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> se marca como de solo lectura.

### <a name="to-resize-a-named-range-programmatically"></a>Para cambiar el tamaño de un rango con nombre mediante programación

1. Cree un control <xref:Microsoft.Office.Tools.Excel.NamedRange> en la celda **A1** de `Sheet1`.

     [!code-csharp[Trin_VstcoreHostControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreHostControlsExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#4)]

2. Cambie el tamaño del rango con nombre para incluir la celda **B1**.

     [!code-csharp[Trin_VstcoreHostControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreHostControlsExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#5)]

## <a name="runtimeaddin"></a>Cambiar el tamaño de los controles NamedRange en tiempo de ejecución en un proyecto de complemento de VSTO
 Se puede cambiar el tamaño de un control <xref:Microsoft.Office.Tools.Excel.NamedRange> en tiempo de ejecución en cualquier hoja de cálculo abierta. Para obtener más información sobre cómo agregar un <xref:Microsoft.Office.Tools.Excel.NamedRange> control a una hoja de cálculo mediante un complemento de VSTO, consulte [cómo: Agregar controles NamedRange a hojas de](../vsto/how-to-add-namedrange-controls-to-worksheets.md)cálculo.

### <a name="to-resize-a-named-range-programmatically"></a>Para cambiar el tamaño de un rango con nombre mediante programación

1. Cree un control <xref:Microsoft.Office.Tools.Excel.NamedRange> en la celda **A1** de `Sheet1`.

     [!code-csharp[Trin_Excel_Dynamic_Controls#10](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#10)]
     [!code-vb[Trin_Excel_Dynamic_Controls#10](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#10)]

2. Cambie el tamaño del rango con nombre para incluir la celda **B1**.

     [!code-csharp[Trin_Excel_Dynamic_Controls#11](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#11)]
     [!code-vb[Trin_Excel_Dynamic_Controls#11](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#11)]

## <a name="see-also"></a>Vea también
- [Ampliar documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Controles en documentos de Office](../vsto/controls-on-office-documents.md)
- [Información general sobre elementos y controles host](../vsto/host-items-and-host-controls-overview.md)
- [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)
- [NamedRange (control)](../vsto/namedrange-control.md)
- [Cómo: Agregar controles NamedRange a hojas de cálculo](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Cómo: Cambiar el tamaño de los controles Bookmark](../vsto/how-to-resize-bookmark-controls.md)
- [Cómo: Cambiar el tamaño de los controles ListObject](../vsto/how-to-resize-listobject-controls.md)
