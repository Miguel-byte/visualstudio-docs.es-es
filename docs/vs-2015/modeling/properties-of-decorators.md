---
title: Propiedades de los elementos Decorator | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
ms.assetid: f6322fe5-dc08-4d32-a6b3-0bd18879136d
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cb837c9b3d465d229f64fac08dac02af8d50f5fa
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652017"
---
# <a name="properties-of-decorators"></a>Propiedades de los decoradores
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los elementos Decorator son iconos, texto o cheurones de expansión/contracción que pueden aparecer en formas o conectores en el diagrama. En las tablas siguientes se muestran las propiedades de los tres tipos de Decorator. Algunas de las propiedades solo aparecen en los decoradores de forma o solo en los elementos Decorator del conector.

 Para obtener más información, consulte [cómo definir un lenguaje específico de dominio](../modeling/how-to-define-a-domain-specific-language.md). Para obtener más información sobre cómo usar estas propiedades, vea [personalizar y extender un lenguaje específico de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="expandcollapse-decorator"></a>Expandir o contraer Decorator

|Propiedad.|Descripción|Predeterminado|
|--------------|-----------------|-------------|
|DisplayName|Nombre del elemento Decorator que se mostrará en el diseñador generado.|Expandir decorador de contracción|
|Name|Nombre del elemento Decorator.|ExpandCollapseDecorator|
|Notas|Notas informales asociadas a este elemento Decorator.|\<none>|
|HorizontalOffset|Desplazamiento horizontal, en pulgadas, relativo a la posición predeterminada del elemento Decorator. (Solo en formas).|0|
|VerticalOffset|Desplazamiento vertical, relativo a la posición predeterminada del elemento Decorator, en pulgadas. (Solo en formas).|0|
|OffsetFromLine|Desplazamiento del elemento Decorator desde la línea, con respecto a su posición predeterminada, en pulgadas. (Solo en conectores).|0|
|OffsetFromShape|Desplazamiento del elemento Decorator a partir de la forma, con respecto a su posición predeterminada, en pulgadas. (Solo en conectores).|0|
|Posición|Posición predeterminada del elemento Decorator.|SourceTop|

## <a name="icon-decorator"></a>Icono Decorator

|Propiedad.|Descripción|Predeterminado|
|--------------|-----------------|-------------|
|DefaultIcon|Ruta de acceso del archivo de icono o imagen que se va a mostrar.|\<none>|
|DisplayName|Nombre del elemento Decorator que se va a mostrar en el diseñador generado.|Icono Decorator|
|Name|Nombre del elemento Decorator.|IconDecorator|
|Notas|Notas informales asociadas al elemento Decorator.|\<none>|
|HorizontalOffset|Desplazamiento horizontal, en pulgadas, relativo a la posición predeterminada del elemento Decorator. (Solo en formas).|0|
|VerticalOffset|Desplazamiento vertical, relativo a la posición predeterminada del elemento Decorator, en pulgadas. (Solo en formas).|0|
|OffsetFromLine|Desplazamiento del elemento Decorator desde la línea, con respecto a su posición predeterminada, en pulgadas. (Solo en conectores).|0|
|OffsetFromShape|Desplazamiento del elemento Decorator a partir de la forma, con respecto a su posición predeterminada, en pulgadas. (Solo en conectores).|0|
|Posición|Posición predeterminada del elemento Decorator.|SourceTop|

## <a name="textdecorator"></a>TextDecorator

|Propiedad.|Descripción|Predeterminado|
|--------------|-----------------|-------------|
|DefaultText|Texto predeterminado que se va a mostrar.|Etiqueta|
|DisplayName|Nombre del elemento Decorator que se va a mostrar en el diseñador generado.|Etiqueta|
|FontSize|Tamaño de fuente para el texto que se muestra en el elemento Decorator.|8|
|FontStyle|Estilo de fuente para el texto que se muestra en el elemento Decorator.|Estándar|
|Name|Nombre del elemento Decorator.|Etiqueta|
|Notas|Notas informales asociadas al elemento Decorator.|\<none>|
|HorizontalOffset|Desplazamiento horizontal, en pulgadas, relativo a la posición predeterminada del elemento Decorator. (Solo en formas).|0|
|VerticalOffset|Desplazamiento vertical, relativo a la posición predeterminada del elemento Decorator, en pulgadas. (Solo en formas).|0|
|OffsetFromLine|Desplazamiento del elemento Decorator desde la línea, con respecto a su posición predeterminada, en pulgadas. (Solo en conectores).|0|
|OffsetFromShape|Desplazamiento del elemento Decorator a partir de la forma, con respecto a su posición predeterminada, en pulgadas. (Solo en conectores).|0|
|Posición|Posición predeterminada del elemento Decorator.|TargetBottom|

## <a name="see-also"></a>Vea también
 [Glosario de las Herramientas del lenguaje específico de dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
