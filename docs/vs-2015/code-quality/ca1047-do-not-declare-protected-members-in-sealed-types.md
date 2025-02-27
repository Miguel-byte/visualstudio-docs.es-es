---
title: 'CA1047: no declarar miembros protegidos en tipos sellados | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDeclareProtectedMembersInSealedTypes
- CA1047
helpviewer_keywords:
- CA1047
- DoNotDeclareProtectedMembersInSealedTypes
ms.assetid: 829033b5-a9d8-4f26-a719-45494c9dd035
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ebc6732e559b70e753a44b14cf45b7de9fc150d4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668182"
---
# <a name="ca1047-do-not-declare-protected-members-in-sealed-types"></a>CA1047: No declarar miembros protegidos en tipos sealed
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|
|Identificador de comprobación|CA1047|
|Categoría|Microsoft. Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un tipo público es `sealed` (`NotInheritable` en Visual Basic) y declara un miembro protegido o un tipo anidado protegido. Esta regla no notifica las infracciones de métodos <xref:System.Object.Finalize%2A>, que deben seguir este patrón.

## <a name="rule-description"></a>Descripción de la regla
 Los tipos declaran miembros protegidos para que los tipos heredados puedan obtener acceso o reemplazar el miembro. Por definición, no se puede heredar de un tipo sellado, lo que significa que no se puede llamar a los métodos protegidos en tipos sellados.

 El C# compilador emite una advertencia para este error.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie el nivel de acceso del miembro a Private o haga que el tipo sea heredable.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. Si se deja el tipo en su estado actual, se pueden producir problemas de mantenimiento y no se proporciona ninguna ventaja.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo que infringe esta regla.

 [!code-csharp[FxCop.Design.SealedNoProtected#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.SealedNoProtected/cs/FxCop.Design.SealedNoProtected.cs#1)]
 [!code-vb[FxCop.Design.SealedNoProtected#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.SealedNoProtected/vb/FxCop.Design.SealedNoProtected.vb#1)]
