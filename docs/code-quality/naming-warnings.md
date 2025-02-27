---
title: advertencias de nomenclatura
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.namingrules
helpviewer_keywords:
- managed code analysis warnings, naming warnings
- naming warnings
- warnings, naming
ms.assetid: f97223ce-1d39-4134-81c9-fff2c75d979b
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: afcaca34c937cc5a90c78a6f4de69ec395df4f42
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649195"
---
# <a name="naming-warnings"></a>advertencias de nomenclatura

Las advertencias de nomenclatura admiten el cumplimiento de las convenciones de nomenclatura de las instrucciones de diseño de .NET.

## <a name="in-this-section"></a>En esta sección

|Regla|Descripción|
|----------|-----------------|
|[CA1700: No nombrar valores de enumeración como 'Reserved'](../code-quality/ca1700.md)|Esta regla supone que un miembro de la enumeración con un nombre que contiene la palabra "reserved" no se utiliza actualmente pero hace de marcador de posición para que se pueda quitar o cambiar el nombre en una versión posterior. Quitar o cambiar el nombre de un miembro es un cambio importante.|
|[CA1713: Los eventos no deberían tener prefijos antes ni después](../code-quality/ca1713.md)|El nombre de un evento empieza por "Before" o "After". Para nombrar los eventos relacionados que se provocan en una secuencia específica, utilice el tiempo presente o pasado para indicar la posición relativa en la secuencia de acciones.|
|[CA1714: Las enumeraciones Flags deberían tener nombres en plural](../code-quality/ca1714.md)|Una enumeración pública tiene el atributo System. FlagsAttribute y su nombre no termina en "s". Los tipos marcados con FlagsAttribute tienen nombres que son plurales porque el atributo indica que se puede especificar más de un valor.|
|[CA1704: Los identificadores deberían tener la ortografía correcta](../code-quality/ca1704.md)|El nombre de un identificador visible externamente contiene una o varias palabras que la biblioteca de correctores ortográficos de Microsoft no reconoce.|
|[CA1708: Los identificadores se deberían diferenciar en algo más que en el uso de mayúsculas y minúsculas](../code-quality/ca1708.md)|Los identificadores de los espacios de nombres, miembros y parámetros no puede distinguirse sólo por mayúsculas o minúsculas porque los lenguajes que tienen como destino el Common Language Runtime no necesitan distinguir entre mayúsculas y minúsculas.|
|[CA1715: Los identificadores deberían tener el prefijo correcto](../code-quality/ca1715.md)|El nombre de una interfaz visible externamente no empieza con una "I" mayúscula.  El nombre de un parámetro de tipo genérico en un tipo o método visible externamente no empieza con una "T" mayúscula.|
|[CA1720: Los identificadores no deben contener nombres de tipo](../code-quality/ca1720.md)|El nombre de un parámetro en un miembro visible externamente contiene un nombre de tipo de datos o el nombre de un miembro visible externamente contiene un nombre de tipo de datos específico del lenguaje.|
|[CA1722: Los identificadores no deberían tener el prefijo incorrecto](../code-quality/ca1722.md)|Por convención, sólo ciertos elementos de programación tienen nombres que comienzan con un prefijo concreto.|
|[CA1711: Los identificadores no deberían tener el sufijo incorrecto](../code-quality/ca1711.md)|Por convención, los nombres de tipos que extienden determinados tipos base o que implementan algunas interfaces, o tipos derivados de estos tipos, deben terminar con unos sufijos reservados específicos. Otros nombres de tipo no deben utilizar estos sufijos reservados.|
|[CA1717: Solo las enumeraciones FlagsAttribute deberían tener nombres en plural](../code-quality/ca1717.md)|Las convenciones de nomenclatura establecen que un nombre en plural para una enumeración indica que se pueden especificar varios valores de enumeración al mismo tiempo.|
|[CA1725: Los nombres de parámetro deberían coincidir con la declaración base](../code-quality/ca1725.md)|El uso del mismo nombre para un parámetro en una jerarquía de reemplazo aumenta la utilidad de los reemplazos de método. Cuando el nombre de un parámetro en un método derivado es distinto del nombre de la declaración base, puede resultar difícil determinar si el método es un reemplazo del método base o una nueva sobrecarga del método.|
|[CA1719: Los nombres de parámetro no deberían coincidir con los nombres de miembro](../code-quality/ca1719.md)|Un nombre de parámetro debe comunicar el significado de un parámetro, y un nombre de miembro debe comunicar el significado de un miembro. Sería un diseño extraño si éstos fueran los mismos. Denominar un parámetro igual que el nombre del miembro no es intuitivo y dificulta el uso de la biblioteca.|
|[CA1701: En las palabras compuestas de la cadena de recursos se deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1701.md)|Cada palabra de la cadena de recursos se divide en tokens que se basan en el uso de mayúsculas y minúsculas. La biblioteca de correctores ortográficos de Microsoft comprueba cada combinación de dos tokens contiguos. Si la reconoce, la palabra genera una infracción de la regla.|
|[CA1703: Las cadenas de recursos deberían tener la ortografía correcta](../code-quality/ca1703.md)|Una cadena de recurso contiene una o varias palabras que la biblioteca de correctores ortográficos de Microsoft no reconoce.|
|[CA1724: Los nombres de tipo no deberían coincidir con los espacios de nombres](../code-quality/ca1724.md)|Los nombres de tipo no deben coincidir con los nombres de los espacios de nombres de .NET. Una infracción de esta regla puede reducir la facilidad de uso de la biblioteca.|
|[CA1707: Los identificadores no deberían contener subrayado](../code-quality/ca1707.md)|Por convención, los nombres del identificador no contienen el carácter de subrayado (_). Esta regla comprueba espacios de nombres, tipos, miembros y parámetros.|
|[CA1721: Los nombres de propiedades no deberían coincidir con los métodos get](../code-quality/ca1721.md)|El nombre de un miembro público o protegido empieza por "Get" y en cualquier otro caso coincide con el nombre de una propiedad pública o protegida. Las propiedades y métodos "Get" deberían tener nombres que distingan claramente su función.|
|[CA1716: Los identificadores no deberían coincidir con palabras clave](../code-quality/ca1716.md)|Un nombre de espacio de nombres o un nombre de tipo coinciden con una palabra clave reservada en un lenguaje de programación. Los identificadores para los espacios de nombres y tipos no deberían coincidir con palabras clave definidas por los lenguajes que tienen como destino el Common Language Runtime.|
|[CA1726: Utilizar términos preferidos](../code-quality/ca1726.md)|El nombre de un identificador visible externamente incluye un término para el que existe un término alternativo más apropiado. Alternativamente, el nombre incluye el término "Flag" o "Flags".|
|[CA1709: Los identificadores deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1709.md)|Por Convención, los nombres de parámetro usan mayúsculas y minúsculas Camel, y los nombres de espacio de nombres, tipo y miembro usan mayúsculas y minúsculas Pascal.|
|[CA1702: En las palabras compuestas se deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1702.md)|El nombre de un identificador contiene varias palabras y al menos una de ellas parece ser una palabra compuesta en la que no se utilizan correctamente las mayúsculas y minúsculas.|
|[CA1712: No utilizar prefijos en valores de enumeración con el nombre del tipo](../code-quality/ca1712.md)|Los nombres de los miembros de enumeración no tienen como prefijo el nombre de tipo porque se espera que las herramientas de Desarrollo proporcionen información de tipo.|
|[CA1710: Los identificadores deberían tener el sufijo correcto](../code-quality/ca1710.md)|Por Convención, los nombres de tipos que extienden determinados tipos base o que implementan determinadas interfaces, o tipos derivados de estos tipos, tienen un sufijo que está asociado con el tipo base o la interfaz.|
