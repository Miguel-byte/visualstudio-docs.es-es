---
title: 'CA2144: el código transparente no debe cargar ensamblados desde matrices de bytes | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2144
ms.assetid: 777b1310-6e16-4413-b4ee-5f3136304f82
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 36b27880b5574e9e47067c240bc162cc15e8d3b6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610315"
---
# <a name="ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays"></a>CA2144: El código transparente no debe cargar ensamblados desde matrices de bytes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsShouldNotLoadAssembliesFromByteArrays|
|Identificador de comprobación|CA2144|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método transparente carga un ensamblado desde una matriz de bytes mediante uno de los métodos siguientes:

- <xref:System.Reflection.Assembly.Load%2A>

- <xref:System.Reflection.Assembly.Load%2A>

- <xref:System.Reflection.Assembly.Load%2A>

## <a name="rule-description"></a>Descripción de la regla
 La revisión de seguridad del código transparente no es tan exhaustiva como la revisión de seguridad del código crítico, porque el código transparente no puede realizar acciones que afectan a la seguridad. Los ensamblados cargados desde una matriz de bytes podrían no distinguirse en el código transparente, y esa matriz de bytes podría contener código importante crítico para la seguridad, que no hace falta auditar. Por lo tanto, el código transparente no debe cargar ensamblados de una matriz de bytes.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, marque el método que está cargando el ensamblado con el <xref:System.Security.SecurityCriticalAttribute> o el atributo de <xref:System.Security.SecuritySafeCriticalAttribute>.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 La regla se desencadena en el código siguiente porque un método transparente carga un ensamblado desde una matriz de bytes.

 [!code-csharp[FxCop.Security.CA2144.TransparentMethodsShouldNotLoadAssembliesFromByteArrays#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2144.transparentmethodsshouldnotloadassembliesfrombytearrays/cs/ca2144 - transparentmethodsshouldnotloadassembliesfrombytearrays.cs#1)]
