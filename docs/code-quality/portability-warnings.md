---
title: advertencias de portabilidad
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.PortabilityRules
helpviewer_keywords:
- portability warnings
- managed code analysis warnings, portability warnings
- warnings, portability
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3e1959066f81663d66e8af2af8039080d8cace6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649131"
---
# <a name="portability-warnings"></a>advertencias de portabilidad
Las advertencias de portabilidad admiten la portabilidad en diferentes sistemas operativos.

## <a name="in-this-section"></a>En esta sección

|Regla|Descripción|
|----------|-----------------|
|[CA1900: Los campos de tipo de valor deberían ser portátiles](../code-quality/ca1900.md)|Esta regla comprueba que las estructuras que se declaran mediante un atributo de diseño explícito se alinearán correctamente cuando se calculen las referencias a código no administrado en sistemas operativos de 64 bits.|
|[CA1901: Las declaraciones P/Invoke deben ser portables](../code-quality/ca1901.md)|Esta regla evalúa el tamaño de cada parámetro y el valor devuelto de P/Invoke, y comprueba que su tamaño es correcto cuando se calculan las referencias a código no administrado en sistemas operativos de 32 y 64 bits.|
|[CA1903: Usar solo API de la versión de .NET Framework de destino](../code-quality/ca1903.md)|Un miembro o tipo utiliza un miembro o tipo que se introdujo en un Service Pack no incluido junto con la versión de .NET Framework de destino del proyecto.|
