---
title: -Setup (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
ms.assetid: 87608b7f-a156-400c-80f5-fc823f843e61
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a923d1f3532548ebc6ed651a0739e0e5792f7967
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663533"
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Fuerza a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] a combinar los metadatos de recursos que describen los menús, las barras de herramientas y los grupos de comandos de todos los VSPackages disponibles.

## <a name="syntax"></a>Sintaxis

```
devenv /setup
```

## <a name="remarks"></a>Comentarios
 Este modificador no toma ningún argumento. El comando `devenv /setup` suele ser el último paso del proceso de instalación. El uso del modificador `/setup` no inicia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

 Debe ejecutar `devenv` como administrador para poder usar los modificadores [/setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) y [/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md) .

## <a name="example"></a>Ejemplo
 En este ejemplo se muestra el último paso de la instalación de una versión de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] que incluye VSPackages.

```
devenv /setup
```

## <a name="see-also"></a>Otras referencias
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
