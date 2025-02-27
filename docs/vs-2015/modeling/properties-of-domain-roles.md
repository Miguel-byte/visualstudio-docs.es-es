---
title: Propiedades de los roles de dominio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
ms.assetid: 5a7bb18c-638e-45e8-9d79-9aa6a9e14b0e
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a0cddfb3d5c95e5636e9dac069106e3010bedff8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671465"
---
# <a name="properties-of-domain-roles"></a>Propiedades de los roles de dominio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las propiedades de la tabla siguiente están asociadas a un rol de dominio. Para obtener información sobre los roles de dominio, vea Descripción de los [modelos, las clases y las relaciones](../modeling/understanding-models-classes-and-relationships.md). Para obtener más información sobre cómo usar estas propiedades, vea [personalizar y extender un lenguaje específico de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Propiedad.|Descripción|Predeterminado|
|--------------|-----------------|-------------|
|Tipo de colección|Si este rol tiene una multiplicidad de 0.. * o 1.. \*, esta propiedad Personaliza el tipo genérico que se utiliza para almacenar la colección de vínculos.|se utiliza `(none)`  -  <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601>|
|Atributos personalizados|Los atributos que especifique aquí se agregarán como atributos a la clase de código generada.|\<none>|
|La propiedad es explorable|Si `True`, y si la multiplicidad de la relación es 0.. 1 o 1.. 1, el usuario puede examinar la propiedad de rol en la ventana **propiedades** . La propiedad muestra el nombre del elemento en el otro extremo del vínculo de relación.|`True`|
|Generador de propiedades is|Si `True`, se genera una propiedad de rol para este rol, que puede usar para atravesar la relación en el código del programa. Si establece este valor en false, puede atravesar la relación de una manera menos eficaz mediante el uso de métodos estáticos de la relación de dominio.|`True`|
|Modificador de acceso de captador de propiedad|Modificador de acceso del captador de la propiedad generada (`public`, `internal`, `private`, `protected` o `protected internal`).|`public`|
|Modificador de acceso del establecedor de propiedad|Modificador de acceso del establecedor para la propiedad generada (`public`, `internal`, `private`, `protected` o `protected internal`).|`public`|
|Multiplicity|El número de elementos del modelo que pueden desempeñar el rol opuesto (`0..1`, `1..1`, `0..*` o `1..*`). Si la multiplicidad es `0..*` o `1..*`, la propiedad generada representa una colección; de lo contrario, la propiedad generada representa un elemento de modelo único.|Depende del tipo de relación y de si es el rol de origen o de destino en la relación.|
|Name|Nombre del rol de dominio. Esta propiedad no puede contener espacios en blanco.|El nombre de la clase de dominio del encargado de rol para este rol.|
|Propaga la copia|`DoNotPropagateCopy`: el encargado de rol copiado no tendrá ninguna copia de este vínculo.<br /><br /> `PropagateCopyToLinkOnly`: el vínculo copiado apunta al encargado de rol opuesto existente.<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer`: el vínculo copiado apunta a una copia del encargado de rol opuesto.|`PropagateCopyToLinkAndOppositeRolePlayer` para los roles de origen de las incrustaciones.<br /><br /> `DoNotPropagateCopy` para otros roles.<br /><br /> Para obtener más información, vea [personalizar el comportamiento de copia](../modeling/customizing-copy-behavior.md)|
|Propaga la eliminación|`True` eliminar el elemento que desempeña este rol cuando se elimina el vínculo asociado.|`True` para el destino de un rol de incrustación.<br /><br /> `False` para otros roles.<br /><br /> Para obtener más información, vea [personalizar el comportamiento de eliminación](../modeling/customizing-deletion-behavior.md).|
|Nombre de la propiedad|Nombre de la propiedad generada en el código del encargado de rol. Este nombre no puede contener espacios en blanco.|Nombre del rol opuesto si este rol tiene una multiplicidad de cero a uno o de uno a uno. de lo contrario, el nombre plural del rol opuesto.|
|Encargado de rol|Clase de dominio del elemento que puede desempeñar este rol en la relación. Esta propiedad es de sólo lectura.|La clase de dominio del encargado de rol para este rol.|
|Notas|Notas informales asociadas al rol de dominio.|\<none>|
|Categoría|La categoría en la que aparece la propiedad generada en la ventana **propiedades** del diseñador generado. Si esta propiedad está vacía, la propiedad generada aparece bajo la categoría **varios** .|\<none>|
|Descripción|La descripción que se usa para documentar el código y se usa en la interfaz de usuario del diseñador generado.<br /><br /> La descripción aparece en la información sobre herramientas de IntelliSense para la propiedad generada en la clase de encargado de rol.|`Description for` *el nombre completo del rol*|
|Display Name|El nombre que se muestra en el diseñador generado para el rol de dominio.|Valor ajustado de la propiedad Name.|
|Help Keyword|Palabra clave opcional que se usa para indizar la ayuda de F1 para el rol de dominio.|\<none>|
|Nombre para mostrar de la propiedad|Nombre que se muestra en el diseñador generado para la propiedad de rol generada.|Valor ajustado de la propiedad de nombre de propiedad.|

> [!NOTE]
> El valor predeterminado de un nombre para mostrar se basa en el valor de propiedad asociado insertando espacios delante de cada carácter en mayúscula que va precedido por un carácter en minúsculas y no seguido de otro carácter en mayúsculas.

## <a name="see-also"></a>Vea también
 [Propiedades de las relaciones de dominio](../modeling/properties-of-domain-relationships.md)
