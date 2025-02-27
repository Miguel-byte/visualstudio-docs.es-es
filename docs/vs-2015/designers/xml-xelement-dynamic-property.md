---
title: Xml (Propiedad dinámica de XElement) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c794d79d62fc580001efc5cf16993d4ac5fef48b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663845"
---
# <a name="xml-xelement-dynamic-property"></a>Xml (Propiedad dinámica de XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obtiene el contenido XML sin formato del elemento.

## <a name="syntax"></a>Sintaxis

```
elem.Xml
```

## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto
 Un <xref:System.String> que representa el contenido XML sin formato del elemento.

## <a name="remarks"></a>Comentarios
 Esta propiedad es equivalente al método <xref:System.Xml.Linq.XNode.ToString%28System.Xml.Linq.SaveOptions%29> de la clase <xref:System.Xml.Linq.XNode?displayProperty=fullName>, con el parámetro `SaveOptions` establecido en <xref:System.Xml.Linq.SaveOptions>.

## <a name="see-also"></a>Otras referencias
 [Valor](../designers/value-xelement-dynamic-property.md) de [las propiedades dinámicas de la clase XElement](../designers/xelement-class-dynamic-properties.md)
