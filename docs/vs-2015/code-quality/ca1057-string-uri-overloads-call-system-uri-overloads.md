---
title: 'CA1057: las sobrecargas URI de cadena llaman a sobrecargas System. Uri | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1057
- StringUriOverloadsCallSystemUriOverloads
helpviewer_keywords:
- StringUriOverloadsCallSystemUriOverloads
- CA1057
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ba7e7de4f3ef6336ed3d82dc1e1da03ec0bf2575
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603077"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057: Las sobrecargas URI de cadena llaman a sobrecargas System.Uri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|Identificador de comprobación|CA1057|
|Categoría|Microsoft. Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un tipo declara sobrecargas de método que solo difieren en el reemplazo de un parámetro de cadena con un parámetro <xref:System.Uri?displayProperty=fullName>, y la sobrecarga que toma el parámetro de cadena no llama a la sobrecarga que toma el parámetro <xref:System.Uri>.

## <a name="rule-description"></a>Descripción de la regla
 Dado que las sobrecargas solo difieren en el parámetro String/<xref:System.Uri>, se supone que la cadena representa un identificador uniforme de recursos (URI). Las representaciones de cadena de identificadores URI tienen tendencia a analizar y codificar errores, por lo que pueden crear puntos vulnerables en la seguridad. La clase <xref:System.Uri> proporciona estos servicios de forma segura. Para aprovechar las ventajas de la clase <xref:System.Uri>, la sobrecarga de la cadena debe llamar a la sobrecarga <xref:System.Uri> mediante el argumento de cadena.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Vuelva a implementar el método que usa la representación de cadena del URI para que cree una instancia de la clase <xref:System.Uri> mediante el argumento de cadena y, a continuación, pase el objeto <xref:System.Uri> a la sobrecarga que tiene el parámetro <xref:System.Uri>.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el parámetro de cadena no representa un URI.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra una sobrecarga de cadena implementada correctamente.

 [!code-cpp[FxCop.Design.CallUriOverload#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cpp/FxCop.Design.CallUriOverload.cpp#1)]
 [!code-csharp[FxCop.Design.CallUriOverload#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cs/FxCop.Design.CallUriOverload.cs#1)]
 [!code-vb[FxCop.Design.CallUriOverload#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/vb/FxCop.Design.CallUriOverload.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2234: Pase objetos System.Uri en lugar de cadenas](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1056: Las propiedades URI no deben ser cadenas](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: Los parámetros de URI no deben ser cadenas](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: Los valores devueltos URI no deben ser cadenas](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
