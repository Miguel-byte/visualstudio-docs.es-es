---
title: Guardar un conjunto de DataSet como XML | Microsoft Docs
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
- XML [Visual Basic], datasets
- data [Visual Studio], saving as XML
- datasets [Visual Basic], saving as XML
- saving data
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e64c3c17934e5cdc5d6ca1f510c7164b86a77c1a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652861"
---
# <a name="save-a-dataset-as-xml"></a>Guardar un conjunto de datos como XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se puede tener acceso a los datos XML de un conjunto de datos mediante una llamada a los métodos XML disponibles en el conjunto de datos. Para guardar los datos en formato XML, puede llamar al método <xref:System.Data.DataSet.GetXml%2A> o al método <xref:System.Data.DataSet.WriteXml%2A> de una <xref:System.Data.DataSet>.

 La llamada al método <xref:System.Data.DataSet.GetXml%2A> devuelve una cadena que contiene los datos de todas las tablas de datos del conjunto de datos con formato XML.

 Al llamar al método <xref:System.Data.DataSet.WriteXml%2A> se envían los datos con formato XML a un archivo que se especifique.

### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Para guardar los datos de un conjunto de datos como XML en una variable

- El método <xref:System.Data.DataSet.GetXml%2A> devuelve un <xref:System.String>. Esto significa que se declara una variable de tipo <xref:System.String> y se le asignan los resultados del método <xref:System.Data.DataSet.GetXml%2A>.

     [!code-csharp[VbRaddataSaving#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#12)]
     [!code-vb[VbRaddataSaving#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#12)]

### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Para guardar los datos de un conjunto de datos como XML en un archivo

- El método <xref:System.Data.DataSet.WriteXml%2A> tiene varias sobrecargas. En el código siguiente se muestra cómo guardar los datos en un archivo. Declare una variable y asígnela una ruta de acceso válida para guardar el archivo.

     [!code-csharp[VbRaddataSaving#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#13)]
     [!code-vb[VbRaddataSaving#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#13)]

## <a name="see-also"></a>Vea también
 [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)
