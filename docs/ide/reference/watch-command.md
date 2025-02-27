---
title: Inspección (Comando)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 411452ba0cf8f8625ee67bca51c2f3735f6dc924
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747693"
---
# <a name="watch-command"></a>Inspección (Comando)
Crea y abre una instancia especificada de una ventana **Inspección** . Puede usar una ventana **Inspección** para calcular los valores de variables, expresiones y registros, para editar estos valores y para guardar los resultados.

## <a name="syntax"></a>Sintaxis

```cmd
Debug.Watch[index]
```

## <a name="arguments"></a>Argumentos

`index`\
Obligatorio. El número de instancia de la ventana Inspección.

## <a name="remarks"></a>Comentarios

`index` debe ser un entero. Los valores válidos son 1, 2, 3 o 4.

## <a name="example"></a>Ejemplo

```cmd
>Debug.Watch1
```

## <a name="see-also"></a>Vea también

- [Ventanas de variables locales y automáticas](../../debugger/autos-and-locals-windows.md)
- [Establece una inspección en Variables mediante la inspección y las ventanas de inspección rápida en Visual Studio](../../debugger/watch-and-quickwatch-windows.md)
- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Ventana Comandos](../../ide/reference/command-window.md)
- [Cuadro Buscar/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)