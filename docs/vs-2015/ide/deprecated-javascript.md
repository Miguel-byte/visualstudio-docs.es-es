---
title: '&lt;deprecated &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: cf33d371-59da-4310-95ee-d7524fd9d58c
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 343f3ebe4bea7ee999f60741c189f35defb0ac7b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665803"
---
# <a name="ltdeprecatedgt-javascript"></a>&lt;deprecated&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Especifica una función o un método en desuso.

## <a name="syntax"></a>Sintaxis

```
<deprecated
    type="deprecate|remove"
    locid="descriptionID">description
</deprecated>
```

#### <a name="parameters"></a>Parámetros
 `type` Opcional. Especifica si la función o el método se quitará en futuras versiones, o si la función o el método ya se ha quitado y su uso puede producir un error. Establézcalo en `deprecate` para especificar que la función o el método se quitará en futuras versiones. Establézcalo en `remove` para especificar que la función o el método ya se ha quitado.

 `locid` Opcional. Identificador de la información de localización sobre la función o el método. El identificador es un identificador de miembro o corresponde al valor del atributo `name` en un paquete de mensajes definido por los metadatos de OpenAjax. El tipo de identificador depende del formato especificado en el elemento [\<loc>](../ide/loc-javascript.md).

 `description` Opcional. Descripción de la función o el método que se va a desusar.

## <a name="remarks"></a>Comentarios
 Los elementos utilizados para anotar funciones, entre los que se incluye `<deprecated>`, se deben colocar en el cuerpo de la función antes de cualquier instrucción. Al marcar una función como desusada, se recomienda reemplazar su [\<summary elemento >](../ide/summary-javascript.md) por el elemento `<deprecated>`.

## <a name="example"></a>Ejemplo
 En el código siguiente se muestra cómo usar el elemento `<deprecated>`.

```javascript
function areaFunction(radiusParam) {
    /// <deprecated type="deprecate" >Determines the area of a circle when supplied a radius parameter.</deprecated>
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>
    /// <returns type="Number">The area.</returns>
    var areaVal;
    areaVal = Math.PI * radiusParam * radiusParam;
    return areaVal;
}

```

## <a name="see-also"></a>Otras referencias
 [Comentarios de documentación XML](../ide/xml-documentation-comments-javascript.md)
