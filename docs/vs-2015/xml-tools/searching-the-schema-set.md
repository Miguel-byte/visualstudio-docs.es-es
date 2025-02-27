---
title: Buscar en el conjunto de esquemas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0e3a8563d5e2cd29c9c521761498d7ef87b7cbab
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656157"
---
# <a name="searching-the-schema-set"></a>Buscar en el conjunto de esquemas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El Explorador de esquemas XML permite buscar en el conjunto de esquemas de las maneras siguientes:

- Búsqueda de palabra clave.

- Búsqueda específica del esquema.

## <a name="keyword-search"></a>Búsqueda de palabra clave
 Para realizar búsquedas de palabras clave, escriba una subcadena en el cuadro de texto **Buscar de búsqueda** de la barra de herramientas del explorador de esquemas XML.

 ![Búsqueda de palabras clave del explorador de esquema XML](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")

 El Explorador de esquemas XML busca en el conjunto de esquemas lo siguiente:

- Cualquier atributo `name` o `ref` que coincida con la palabra clave especificada. Esto permite buscar elementos, atributos, tipos, etc. por nombre.

- Los atributos `schemaLocation` de las instrucciones include.

- Los atributos `namespace` de las instrucciones import.

## <a name="schema-specific-search"></a>Búsqueda específica del esquema
 El Explorador de esquemas XML también incluye buscadores integrados a los que se tiene acceso mediante el menú contextual del explorador. Para obtener más información acerca de los menús contextuales disponibles, consulte [menús contextuales](../xml-tools/context-menus-xml-schema-explorer.md). También puede realizar una búsqueda específica del esquema desde la vista Inicio. para obtener más información, consulte la sección "detalles del conjunto de esquemas" en el tema de la [vista Inicio](../xml-tools/start-view.md) .

## <a name="displaying-and-navigating-search-results"></a>Mostrar y navegar en los resultados de la búsqueda
 Una vez finalizada la búsqueda, se agrega el panel de resumen de resultados a la barra de herramientas con los resultados de la búsqueda. Los resultados de la búsqueda también se resaltan en el Explorador de esquemas XML y se marcan en la barra de desplazamiento vertical. Puede navegar por los resultados de la búsqueda mediante los botones **ir a siguiente resultado** de la búsqueda e **ir al resultado de la búsqueda anterior** en el panel de resultados de Resumen de la barra de herramientas del explorador de esquemas XML. mediante las teclas de teclado F3 y MAYÚS + F3; o bien, haga clic en las marcas de graduación de la barra de desplazamiento.

 Puede Agregar los resultados de la búsqueda al área de trabajo haciendo clic en el botón **agregar nodos resaltados al área de trabajo** en el panel de resultados de resumen.

 ![Resultado de búsqueda del explorador de esquemas XML](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")

## <a name="clearing-search-results"></a>Borrar los resultados de una búsqueda
 Para borrar los resultados de la búsqueda, haga clic en el botón **x** del panel de resultados de Resumen de la barra de herramientas de búsqueda del explorador de esquemas XML.

## <a name="see-also"></a>Vea también
 [Explorador de esquemas XML](../xml-tools/xml-schema-explorer.md)
