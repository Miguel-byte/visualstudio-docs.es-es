---
title: 'CA1062: validar argumentos de métodos públicos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
ms.assetid: db1f69ca-68f7-477e-94f3-d135cc5dfcbc
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 50044b51a3e576ff7d1c11b19b2f498f99b63019
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663652"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062: Validar argumentos de métodos públicos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|Identificador de comprobación|CA1062|
|Categoría|Microsoft. Design|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Un método visible externamente desreferencia uno de sus argumentos de referencia sin comprobar si ese argumento es `null` (`Nothing` en Visual Basic).

## <a name="rule-description"></a>Descripción de la regla
 Todos los argumentos de referencia que se pasan a métodos visibles externamente deben comprobarse con `null`. Si es necesario, inicie una <xref:System.ArgumentNullException> cuando el argumento sea `null`.

 Si se puede llamar a un método desde un ensamblado desconocido porque se ha declarado público o protegido, debe validar todos los parámetros del método. Si el método está diseñado para que solo lo llamen los ensamblados conocidos, debe hacer que el método sea interno y aplicar el atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> al ensamblado que contiene el método.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, valide cada argumento de referencia en `null`.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Puede suprimir una advertencia de esta regla si está seguro de que el parámetro desreferenciado se ha validado mediante otra llamada al método en la función.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un método que infringe la regla y un método que cumple la regla.

 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#1)]
 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#1)]
 [!code-vb[FxCop.Design.ValidateArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#1)]

## <a name="example"></a>Ejemplo
 En [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)], esta regla no detecta que los parámetros se pasan a otro método que realiza la validación.

 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#2)]
 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#2)]
 [!code-vb[FxCop.Design.ValidateArguments#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#2)]

## <a name="example"></a>Ejemplo
 Los constructores de copia que rellenan el campo o las propiedades que son objetos de referencia también pueden infringir la regla CA1062. La infracción se produce porque el objeto copiado que se pasa al constructor de copias podría ser `null` (`Nothing` en Visual Basic). Para resolver la infracción, use un método estático (compartido en Visual Basic) para comprobar que el objeto copiado no es NULL.

 En el siguiente ejemplo de clase `Person`, el objeto `other` que se pasa al constructor de copia `Person` podría ser `null`.

```

public class Person
{
    public string Name { get; private set; }
    public int Age { get; private set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    // Copy constructor CA1062 fires because other is dereferenced
    // without being checked for null
    public Person(Person other)
        : this(other.Name, other.Age)
    {
    }
}
```

## <a name="example"></a>Ejemplo
 En el siguiente ejemplo revisado `Person`, el objeto `other` que se pasa al constructor de copias se comprueba primero si es null en el método `PassThroughNonNull`.

```
public class Person
{
    public string Name { get; private set; }
    public int Age { get; private set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    // Copy constructor
    public Person(Person other)
        : this(PassThroughNonNull(other).Name,
          PassThroughNonNull(other).Age)
    {
    }

    // Null check method
    private static Person PassThroughNonNull(Person person)
    {
        if (person == null)
            throw new ArgumentNullException("person");
        return person;
    }
}
```
