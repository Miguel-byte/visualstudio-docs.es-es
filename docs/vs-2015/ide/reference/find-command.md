---
title: Comando Buscar | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.find
helpviewer_keywords:
- Find command
- Edit.Find command
ms.assetid: f0c705dc-2b97-423d-abbf-5584d4827208
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6ce0e4a3aaca752cbdeda0a83e469977306c3404
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657683"
---
# <a name="find-command"></a>Buscar (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Busca en los archivos mediante el uso de un subconjunto de las opciones disponibles en la pestaña **Buscar en archivos** de la ventana **Buscar y reemplazar**.

## <a name="syntax"></a>Sintaxis

```
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]
```

## <a name="arguments"></a>Argumentos
 `findwhat` Obligatorio. Texto que debe coincidir.

## <a name="switches"></a>Modificadores
 /case o /c Opcional. Se encuentran coincidencias solo si los caracteres en mayúsculas y minúsculas coinciden exactamente con los especificados en el argumento `findwhat`.

 /doc o /d Opcional. Busca solo en el documento actual. Especifique solo uno de los ámbitos de búsqueda disponibles: `/doc`, `/proc`, `/open` o `/sel`.

 /markall o /m Opcional. Coloca un gráfico en cada línea que contenga una coincidencia de búsqueda en el documento actual.

 /open o /o Opcional. Busca en todos los documentos abiertos como si fueran un documento. Especifique solo uno de los ámbitos de búsqueda disponibles: `/doc`, `/proc`, `/open` o `/sel`.

 /options o /t Opcional. Muestra una lista de los valores de la opción de búsqueda actual y no lleva a cabo una búsqueda.

 /proc o /p Opcional. Busca solo en el procedimiento actual. Especifique solo uno de los ámbitos de búsqueda disponibles: `/doc`, `/proc`, `/open` o `/sel`.

 /reset o /e Opcional. Establece las opciones de búsqueda en su configuración predeterminada y no lleva a cabo una búsqueda.

 /sel o /s Opcional. Busca solo en la selección actual. Especifique solo uno de los ámbitos de búsqueda disponibles: `/doc`, `/proc`, `/open` o `/sel`.

 /up o /u Opcional. Busca desde la ubicación actual en el archivo hacia el principio del archivo. De forma predeterminada, las búsquedas comienzan en la ubicación actual en el archivo y buscan hacia el final del archivo.

 /regex o /r Opcional. Usa caracteres especiales predefinidos en el argumento `findwhat` como notaciones que representan patrones de texto en lugar de los caracteres literales. Para obtener una lista completa de caracteres de expresiones regulares, vea [Expresiones regulares](../../ide/using-regular-expressions-in-visual-studio.md).

 /wild o /l Opcional. Usa caracteres especiales predefinidos en el argumento `findwhat` como notaciones para representar un carácter o una secuencia de caracteres.

 /word o /w Opcional. Busca solo palabras completas.

## <a name="example"></a>Ejemplo
 En este ejemplo se realiza una búsqueda que distingue entre mayúsculas y minúsculas de la palabra "somestring" en la sección de código seleccionada.

```
>Edit.Find somestring /sel /case
```

## <a name="see-also"></a>Otras referencias
 [Ventana comandos](../../ide/reference/command-window.md) [cuadro Buscar/comando](../../ide/find-command-box.md) [comandos de Visual](../../ide/reference/visual-studio-commands.md) Studio [alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
