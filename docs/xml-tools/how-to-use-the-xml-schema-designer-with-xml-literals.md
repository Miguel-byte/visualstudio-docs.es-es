---
title: 'Cómo: Usar el Diseñador de esquemas XML con literales XML'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: ed987a54004004fe8c4fbfba686ae1a35d12bb06
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601850"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Cómo: usar el diseñador de esquemas XML con literales XML

En este tema se explica cómo ver un esquema asociado a un literal XML en un proyecto Visual Basic.

## <a name="create-a-new-visual-basic-project"></a>Crear un nuevo proyecto de Visual Basic

1. Abra Visual Studio.

2. Cree un nuevo proyecto de **aplicación de consola** de Visual Basic denominado **XMLLiterals**.

     El nuevo proyecto contiene un archivo de origen de Visual Basic, *Module1. VB*.

## <a name="add-an-existing-xsd-file"></a>Agregar un archivo XSD existente

1. Abra un nuevo archivo de texto en el Bloc de notas. Copie el código de ejemplo del esquema XML del [esquema del pedido de compra](../xml-tools/sample-xsd-file-simple-schema.md) y péguelo en el archivo.

2. Guarde el archivo en alguna ubicación con el nombre *PurchaseOrderSchema. xsd*.

3. En **Explorador de soluciones**, haga clic con el botón secundario en el nombre del proyecto, seleccione **Agregar**y, a continuación, seleccione **elemento existente**. Aparece el cuadro de diálogo **elemento agregar** . Busque el archivo *PurchaseOrderSchema. xsd* , selecciónelo y, a continuación, haga clic en **Agregar**.

     El proyecto XMLLiterals contiene ahora dos archivos: *Module1. VB* y *PurchaseOrderSchema. xsd*.

## <a name="add-code"></a>Agregar código

Para agregar Visual Basic código con un literal XML, basado en el archivo XSD incluido en el proyecto:

1. Reemplace el código del archivo *Module1. VB* por el código siguiente:

   ```vb
   Imports <xmlns:ns="http://tempuri.org/PurchaseOrderSchema.xsd">

   Module Module1
      Sub Main()

          Dim XMLLiteral = <ns:PurchaseOrder OrderDate="1900-01-01">
                               <ns:ShipTo country="US">
                                   <ns:name>name1</ns:name>
                                   <ns:street>street1</ns:street>
                                   <ns:city>city1</ns:city>
                                   <ns:state>state1</ns:state>
                                   <ns:zip>1</ns:zip>
                               </ns:ShipTo>
                               <ns:BillTo country="US">
                                   <ns:name>name1</ns:name>
                                   <ns:street>street1</ns:street>
                                   <ns:city>city1</ns:city>
                                   <ns:state>state1</ns:state>
                                   <ns:zip>1</ns:zip>
                               </ns:BillTo>
                           </ns:PurchaseOrder>

      End Sub
   End Module
   ```

2. Haga clic con el botón secundario en cualquier nodo XML de un literal XML o una importación de espacio de nombres XML y seleccione **Mostrar en el explorador de esquemas**.

   El **Explorador de esquemas XML** se muestra en paralelo con un archivo Visual Basic que tiene el literal XML asociado al conjunto de esquemas XML.