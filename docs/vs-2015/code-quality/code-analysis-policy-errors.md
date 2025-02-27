---
title: Errores de directiva de análisis de código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.policyfailures
helpviewer_keywords:
- policy errors, code analysis
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8cb50fffc1411e77f771b0f74fbb947144eb6017
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672922"
---
# <a name="code-analysis-policy-errors"></a>Errores de las directivas de análisis de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los errores siguientes se producen si la directiva de análisis de código no se cumple en el momento de la protección:

 **La configuración de análisis de código de uno o varios proyectos no es compatible con la Directiva de análisis de código.**

 La comprobación de los requisitos de análisis de código para el control de código fuente de proyecto de equipo no se cumplió para uno o varios proyectos de código. Este error puede deberse a una o más de las condiciones siguientes:

1. El análisis de código no está habilitado en la compilación para todos los proyectos de la solución.

2. El conjunto de reglas local para el proyecto en Visual Studio tiene un valor de **acción** menos restrictivo que el conjunto de reglas del proyecto de equipo, por ejemplo, una regla que se establece en **acción** =**error** en el servidor tiene su **acción** establecida en **ADVERTENCIA** o **ninguno** en el conjunto de reglas que se ejecuta en Visual Studio).

3. El conjunto de reglas especificado en Visual Studio no contiene todas las reglas incluidas en el conjunto de reglas especificado en la directiva de inserción en el repositorio de análisis de código del proyecto de equipo.

   **Error en la Directiva de análisis de código. Hay errores en el proyecto {0} o la compilación no está actualizada.**

   La compilación contiene errores o éstos se corrigieron pero no se realizó el análisis de código después de la corrección.

   **Error en la inserción en el repositorio. La Directiva de análisis de código requiere que se proteja a través de Visual Studio con una solución abierta.**

   La directiva de análisis de código requiere que todos los archivos que se están protegiendo estén en la solución actualmente abierta. Para corregir este error, abra la solución que contiene el archivo que se va a proteger.

   **No todos los archivos de la protección pendiente están dentro de la solución actualmente abierta.**

   La directiva de análisis de código requiere que todos los archivos que se están protegiendo estén en la solución actualmente abierta. Este error se produce cuando hay una solución abierta pero algunos archivos de la vista "inserción en el repositorio pendiente" no forman parte de la solución actualmente abierta. Para corregir este error, abra la solución que contiene el archivo que se va a proteger.

   **La versión de ' {0} ' no es correcta. El nombre seguro especificado en la Directiva es ' {1} '.**

   Este error se aplica a los proyectos de .NET. Un archivo .dll de regla requerido por la directiva de análisis de código existe en el equipo local, pero la versión/clave pública no coincide. Para corregir este error, el creador de la Directiva debe actualizar los archivos. dll en el directorio *c:\Archivos de Programa\microsoft Visual Studio 8 \ Team Tools\Static Analysis Tools\FxCop\Rules \\* del equipo.

   **el ensamblado ' {0} ' especificado en la Directiva no existe.**

   Este error se aplica a los proyectos de .NET. Una regla requerida por la directiva de análisis de código no tiene el archivo dll correspondiente instalado en el equipo cliente. Para corregir este error, el creador de la Directiva debe actualizar el archivo dll en *c:\Archivos de Programa\microsoft Visual Studio 8 \ Team Tools\Static Analysis Tools\FxCop\Rules \\* Directory en su equipo.

   **La configuración de las reglas del proyecto {0} no cumple la Directiva de análisis de código.**

   Este error se aplica a los proyectos de .NET. La configuración de las reglas de código administrado no es tan estricta como exige la directiva. Para corregir este error, la configuración del cliente debe ser igual o más estricta que el requisito de la directiva del servidor.

   **El análisis de código no está habilitado en la configuración activa. Cambie a la {0} de configuración y compile el {1} del proyecto antes de proteger.**

   En [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], la configuración activa no tiene el análisis de código habilitado, pero hay al menos un análisis de código habilitado.

   **Debe habilitar el análisis de código para los binarios administrados en las propiedades del proyecto {0} y compilar antes de la protección.**

   Este error se aplica a las aplicaciones de [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]. La directiva exige realizar el análisis del código administrado, pero no está habilitado en el proyecto actual en el cliente.

   **Debe habilitar el análisis de código en las propiedades del proyecto {0} y compilar antes de la protección.**

   Este error se aplica a proyectos [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] y proyectos web. La directiva exige realizar el análisis del código administrado, pero no está habilitado en el proyecto actual en el cliente.

   **Debe habilitar el análisis deC++ código C/en las propiedades del proyecto {0} y compilar antes de la protección.**

   Este error se aplica a los proyectos no administrados. La directiva de análisis de código requiere análisis de código para C/C++, pero no está habilitada en el proyecto actual en el cliente.

## <a name="see-also"></a>Vea también
 [Errores de la aplicación de análisis de código](../code-quality/code-analysis-application-errors.md)
