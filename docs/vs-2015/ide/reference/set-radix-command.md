---
title: Establecer base (Comando) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 050cbe6e639f4177694d9af3ecbc0b768065b7d9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665414"
---
# <a name="set-radix-command"></a>Establecer base (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Establece o devuelve la base numérica que se ha usado para mostrar valores enteros.

## <a name="syntax"></a>Sintaxis

```
Debug.SetRadix [10 | 16 | hex | dec]
```

## <a name="arguments"></a>Argumentos
 `10` o `16` o `hex` o `dec` opcional. Indica decimal (10 o dec) o hexadecimal (16 o hex). Si se omite un argumento, se devuelve el valor base actual.

## <a name="example"></a>Ejemplo
 En este ejemplo se establece el entorno para mostrar valores enteros en formato hexadecimal.

```
>Debug.SetRadix hex
```

## <a name="see-also"></a>Otras referencias
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md) [ventana comandos](../../ide/reference/command-window.md) [Buscar/comando cuadro](../../ide/find-command-box.md) de comandos de [Visual Studio alias de comandos](../../ide/reference/visual-studio-command-aliases.md)
