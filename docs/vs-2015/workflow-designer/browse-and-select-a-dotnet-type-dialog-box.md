---
title: Examinar y seleccionar un cuadro de diálogo de tipo .NET | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- TypeBrowser.UI
- ActivityTypeResolver.UI
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fa7d087d8354a25b5e16f89b72963c2bfdb55132
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657038"
---
# <a name="browse-and-select-a-net-type-dialog-box"></a>Examinar y seleccionar un cuadro de diálogo de tipo .NET
En la ventana **propiedades** , los cuadros de diálogo o los diseñadores como el diseñador de variables, al seleccionar **Buscar tipos..** . en una lista de tipos de datos, es el cuadro de diálogo **examinar y seleccionar un tipo .net** (al que se hace referencia en forma abreviada como "explorador de tipos"). En este cuadro de diálogo, puede escoger un tipo en una vista de árbol de ensamblados y proyectos.

 Este cuadro de diálogo se emplea en varios escenarios de usuario, lo cual incluye lo siguiente:

- Cuando se establece el tipo de una variable o argumento.

- Cuando se selecciona un tipo para una actividad genérica.

- Cuando se agrega una instrucción catch en la actividad <xref:System.Activities.Statements.TryCatch>.

> [!NOTE]
> El explorador de tipo puede mostrar tipos de matrices escalonadas Visual Basic de matriz, pero no tipos de matrices multidimensionales. Vea [matrices escalonadas](http://go.microsoft.com/fwlink/?LinkId=195226) y [matrices multidimensionales](http://go.microsoft.com/fwlink/?LinkId=195227) para obtener más información.

## <a name="selecting-a-value-or-reference-type-from-the-type-browser"></a>Seleccionar un tipo de valor y de referencia en el explorador de tipo

#### <a name="to-select-a-value-or-reference-type-from-the-type-browser"></a>Para seleccionar un tipo de valor y de referencia en el explorador de tipo

1. En el cuadro **nombre de tipo** , escriba el nombre del tipo que desea utilizar.

2. Realice una de las siguientes acciones:

    - Una vez que el nombre del tipo que desea utilizar aparece en el árbol en el cuadro **nombre de tipo** , haga doble clic en el tipo para seleccionarlo.

    - Escriba los caracteres suficientes en el cuadro **nombre de tipo** para identificar de forma única el tipo que desea utilizar y, a continuación, presione Entrar para seleccionar el tipo.

#### <a name="to-select-a-generic-type-from-the-type-browser"></a>Para seleccionar un tipo genérico en el explorador de tipo

1. En el cuadro **nombre de tipo** , escriba el nombre del tipo que desea utilizar.

2. Una vez que el nombre del tipo que desea utilizar aparece en el árbol en el cuadro **nombre de tipo** , haga clic en el tipo para seleccionarlo para que aparezcan los cuadros desplegables.

     Seleccione el tipo que desea utilizar para cerrar el genérico en los cuadros desplegables y, a continuación, haga clic en **Aceptar**.

## <a name="types-displayed-in-the-type-browser"></a>Tipos que se muestran en el explorador de tipo
 Los tipos que se muestran en el explorador pueden variar en función de cómo se haya iniciado el explorador de tipo. Si el explorador de tipo se inició desde un proyecto de flujo de trabajo dentro de **VS2010**, de forma predeterminada se muestran todos los tipos de los ensamblados a los que se hace referencia y los proyectos a los que se hace referencia. Si el explorador de tipo se inició desde fuera de un sistema de proyectos de **VS2010** (por ejemplo, en una aplicación de flujo de trabajo hospedada en otro host o en un archivo de flujo de trabajo independiente), de forma predeterminada se muestran los tipos de todos los ensamblados cargados en el AppDomain.

 Los tipos en el explorador de tipo se pueden filtrar por desarrolladores de software del diseñador de actividades. Respecto a una actividad en concreto, es posible que vea únicamente un subconjunto de los tipos. Por ejemplo, en la actividad <xref:System.Activities.Statements.TryCatch>, solo se muestran los tipos derivados de <xref:System.Exception> en el explorador de tipo.

## <a name="filtering-search-results-in-the-type-browser"></a>Filtrar los resultados de la búsqueda en el explorador de tipo
 La lista de tipos en el cuadro **nombre de tipo** se reduce a medida que se escriben más caracteres para encontrar una coincidencia. Solo aparecerán en la lista filtrada los tipos cuyo nombre completo o cuyo nombre corto comiencen con la cadena que ha escrito.

 Por ejemplo:

1. La **operación** de escritura coincide con <xref:System.OperationCanceledException> pero no <xref:System.InvalidOperationException>. Para buscar coincidencias con <xref:System.InvalidOperationException>, comience a escribir System.I o Invalid.

2. Escribir las coincidencias **genéricas** <xref:System.GenericUriParser> pero no los tipos del espacio de nombres <xref:System.Collections.Generic>. Para buscar tipos en el espacio de nombres <xref:System.Collections.Generic>, escriba el nombre completo del espacio de nombres.

## <a name="selecting-a-service-contract-using-the-type-browser-dialog"></a>Seleccionar un contrato de servicio usando el cuadro de diálogo de explorador de tipo
 Al seleccionar un tipo de contrato de servicio, el explorador de tipo muestra únicamente los tipos que tienen el atributo <xref:System.ServiceModel.ServiceContractAttribute>.

## <a name="see-also"></a>Vea también
 [Usar los diseñadores de actividad](../workflow-designer/using-the-activity-designers.md)