---
title: Propiedades de las formas de puerto
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.port
helpviewer_keywords:
- Domain-Specific Language, port shape
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 60498c57e80b474bae8d5c320183442bbc4fcfd4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747443"
---
# <a name="properties-of-port-shapes"></a>Propiedades de las formas de puerto
Puede usar las formas de puerto para representar las clases de dominio en el diseñador generado.

 Para obtener más información, consulte [cómo definir un lenguaje específico de dominio](../modeling/how-to-define-a-domain-specific-language.md). Para obtener más información sobre cómo usar estas propiedades, vea [personalizar y extender un lenguaje específico de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Las formas de Puerto tienen las propiedades que se enumeran en la tabla siguiente.

|Propiedad.|Descripción|Predeterminado|
|-|-|-|
|Color de relleno|Color de relleno de esta forma.|Blanco|
|Modo de degradado de relleno|Modo de degradado de relleno de esta forma.|Horizontal|
|Geometry|Geometría de esta forma (rectángulo, rectángulo redondeado, elipse o círculo).|Rectángulo|
|Tiene puntos de conexión predeterminados|Si `True`, la forma usará los puntos de conexión superior, inferior, izquierdo y derecho en el diseñador generado.|False|
|Color del contorno|Color del contorno de esta forma.|Negro|
|Estilo de guión del contorno|El estilo de guión del contorno de esta forma (sólido, guión, punto, DashDot, DashDotDot o personalizado).|Sólido|
|Grosor del contorno|Grosor del contorno de esta forma.|0,03125|
|Color del texto|Color que se usa para los decoradores de texto que están asociados a esta forma.|Negro|
|Modificador de acceso|Nivel de acceso de la clase (`public` o `internal`).|Public|
|Atributos personalizados|Se utiliza para agregar atributos a la clase de código fuente que se genera a partir de esta forma.|\<none>|
|Genera Double derived|Si `True`, se generarán una clase base y una clase parcial (para admitir la personalización mediante invalidaciones). Para obtener más información, vea [invalidación y extensión de las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md) .|False|
|Tiene un constructor personalizado|Si `True`, se proporcionará un constructor personalizado en el código fuente. Para obtener más información, vea [invalidación y extensión de las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Inheritance (modificador)|Describe el tipo de herencia de la clase de código fuente que se genera a partir del puerto (`none`, `abstract` o `sealed`).|ninguna|
|Puerto base|Clase base de esta forma.|(ninguno)|
|Name|Nombre de esta forma.|Nombre actual|
|Espacio de nombres|El espacio de nombres que está asociado con esta forma.|Espacio de nombres actual|
|Tipo de información sobre herramientas|Cómo se define la información sobre herramientas (Fixed, variable o None). Si es Fixed, el valor de la propiedad `Fixed Tooltip Text` se utiliza como información sobre herramientas; Si es variable, la información sobre herramientas se define en código personalizado.|ninguna|
|Notas|Notas informales asociadas a esta forma.|\<none>|
|Alto inicial|Alto inicial de esta forma, en pulgadas.|1|
|Ancho inicial|Ancho inicial de esta forma, en pulgadas.|1.5|
|Color de relleno expuesto como propiedad<br /><br /> Modo de degradado de relleno expuesto<br /><br /> Color de esquema expuesto como propiedad<br /><br /> Estilo de guión del contorno expuesto como propiedad<br /><br /> Grosor del contorno expuesto como propiedad<br /><br /> Expone el color del texto|Si `True`, el usuario puede establecer la propiedad indicada de una forma. Para establecer esto, haga clic con el botón secundario en la definición de la forma y haga clic en **Agregar expuesto**.|False|
|Descripción|Se usa para documentar el diseñador generado.|\<none>|
|Display Name|Nombre que se mostrará en el diseñador generado para esta forma.|\<none>|
|Texto de información sobre herramientas fijo|Texto que se usa para una información sobre herramientas fija.|\<none>|
|Help Keyword|Palabra clave que se usa para indizar la ayuda de F1 para esta forma.|\<none>|

## <a name="see-also"></a>Vea también

- [Glosario de las Herramientas del lenguaje específico de dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)