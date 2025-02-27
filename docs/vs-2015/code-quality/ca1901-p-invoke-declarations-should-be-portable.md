---
title: 'CA1901: las declaraciones P-Invoke deben ser portátiles | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
helpviewer_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d1b4c0c5bcf22db6558f156fd1acd0be94026b08
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661059"
---
# <a name="ca1901-pinvoke-declarations-should-be-portable"></a>CA1901: Las declaraciones P/Invoke deben ser portátiles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PInvokeDeclarationsShouldBePortable|
|Identificador de comprobación|CA1901|
|Categoría|Microsoft. portabilidad|
|Cambio problemático|Interrumpir: Si la P/Invoke es visible fuera del ensamblado. No problemático: Si la P/Invoke no es visible fuera del ensamblado.|

## <a name="cause"></a>Motivo
 Esta regla evalúa el tamaño de cada parámetro y el valor devuelto de P/Invoke y comprueba que su tamaño, cuando se calculan las referencias a código no administrado en plataformas de 32 bits y de 64 bits, es correcto. La infracción más común de esta regla es pasar un entero de tamaño fijo en el que se requiere una variable de tamaño de puntero dependiente de la plataforma.

## <a name="rule-description"></a>Descripción de la regla
 Uno de los escenarios siguientes infringe esta regla:

- El valor devuelto o el parámetro se escribe como un entero de tamaño fijo cuando se debe escribir como `IntPtr`.

- El valor devuelto o el parámetro se escribe como un `IntPtr` cuando se debe escribir como un entero de tamaño fijo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Puede corregir esta infracción mediante el uso de `IntPtr` o `UIntPtr` para representar controladores en lugar de `Int32` o `UInt32`.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No debe suprimir esta advertencia.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra una infracción de esta regla.

```csharp
internal class NativeMethods
{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, IntPtr nIconIndex);
}
```

 En este ejemplo, el parámetro `nIconIndex` se declara como una `IntPtr`, que es de 4 bytes de ancho en una plataforma de 32 bits y 8 bytes de ancho en una plataforma de 64 bits. En la declaración no administrada que aparece a continuación, puede ver que `nIconIndex` es un entero sin signo de 4 bytes en todas las plataformas.

```csharp
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,
    UINT nIconIndex);
```

## <a name="example"></a>Ejemplo
 Para corregir la infracción, cambie la declaración a lo siguiente:

```csharp
internal class NativeMethods{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, uint nIconIndex);
}
```

## <a name="see-also"></a>Vea también
 [Advertencias de portabilidad](../code-quality/portability-warnings.md)
