---
title: Almacenar en caché el origen de datos en el documento de Office mediante programación
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- StartCaching method
- data caching [Office development in Visual Studio], programmatically
- data [Office development in Visual Studio], caching
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 241ce42c2d411fdaf611f3a7f2b52eb40c8c32a2
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189585"
---
# <a name="how-to-programmatically-cache-a-data-source-in-an-office-document"></a>Cómo: almacenar en caché un origen de datos en un documento de Office mediante programación
  Puede agregar mediante programación un objeto de datos a la memoria caché de datos en un documento llamando al método `StartCaching` de un elemento host, como un <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook>o <xref:Microsoft.Office.Tools.Excel.Worksheet>. Quite un objeto de datos de la memoria caché de datos llamando al método `StopCaching` de un elemento host.

 El método `StartCaching` y el método `StopCaching` son privados, pero aparecen en IntelliSense.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Cuando se usa el método `StartCaching` para agregar un objeto de datos a la memoria caché de datos, no es necesario declarar el objeto de datos con el atributo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>. Sin embargo, el objeto de datos debe cumplir ciertos requisitos que se van a agregar a la memoria caché de datos. Para obtener más información, vea [almacenar datos en caché](../vsto/caching-data.md).

## <a name="to-programmatically-cache-a-data-object"></a>Para almacenar en caché mediante programación un objeto de datos

1. Declare el objeto de datos en el nivel de clase, no dentro de un método. En este ejemplo se da por supuesto que está declarando una <xref:System.Data.DataSet> denominada `dataSet1` que desea almacenar en caché mediante programación.

     [!code-csharp[Trin_VstcoreDataExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#12)]
     [!code-vb[Trin_VstcoreDataExcel#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#12)]

2. Cree una instancia del objeto de datos y, a continuación, llame al método `StartCaching` de la instancia del documento o de la hoja de cálculo y pase el nombre del objeto de datos.

     [!code-csharp[Trin_VstcoreDataExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#13)]
     [!code-vb[Trin_VstcoreDataExcel#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#13)]

## <a name="to-stop-caching-a-data-object"></a>Para detener el almacenamiento en caché de un objeto de datos

1. Llame al método `StopCaching` de la instancia del documento o de la hoja de cálculo y pase el nombre del objeto de datos. En este ejemplo se da por supuesto que tiene un <xref:System.Data.DataSet> denominado `dataSet1` que desea detener el almacenamiento en caché.

     [!code-csharp[Trin_VstcoreDataExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#14)]
     [!code-vb[Trin_VstcoreDataExcel#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#14)]

    > [!NOTE]
    > No llame a `StopCaching` desde el controlador de eventos para el evento de `Shutdown` de un documento o una hoja de cálculo. En el momento en que se genera el evento de `Shutdown`, es demasiado tarde para modificar la caché de datos. Para obtener más información sobre el evento `Shutdown`, vea [eventos en proyectos de Office](../vsto/events-in-office-projects.md).

## <a name="see-also"></a>Vea también

- [Datos de caché](../vsto/caching-data.md)
- [Cómo: almacenar datos en caché para su uso sin conexión o en un servidor](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Cómo: almacenar datos en caché en un documento protegido mediante contraseña](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Acceder a los datos de documentos en el servidor](../vsto/accessing-data-in-documents-on-the-server.md)
- [Guardar datos](../data-tools/save-data-back-to-the-database.md)
