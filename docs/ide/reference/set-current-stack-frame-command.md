---
title: Establecer marco de pila actual (Comando)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setcurrentstackframe
helpviewer_keywords:
- Set Current Stack Frame command
- Debug.SetCurrentStackFrame command
ms.assetid: 3dcf52c0-6781-4598-bac2-0094dce67c20
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 088fe9871b54e69b015ffdc9dcdaf23de3d98e0e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747756"
---
# <a name="set-current-stack-frame-command"></a>Establecer marco de pila actual (Comando)
Le permite establecer un marco de pila determinado.

## <a name="syntax"></a>Sintaxis

```cmd
Debug.SetCurrentStackFrame index
```

## <a name="arguments"></a>Argumentos
`index`

Obligatorio. Selecciona un marco de pila por su índice.

## <a name="example"></a>Ejemplo

```cmd
>Debug.SetCurrentStackFrame 1
```

## <a name="see-also"></a>Vea también

- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Ventana Comandos](../../ide/reference/command-window.md)
- [Cuadro Buscar/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)