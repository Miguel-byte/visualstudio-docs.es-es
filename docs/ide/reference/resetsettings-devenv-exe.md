---
title: -ResetSettings (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
- settings [Visual Studio], resetting
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3549801001ba8df60634884dc58137a8fa77d905
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655563"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)

Restaura la configuración predeterminada de Visual Studio e inicia automáticamente el IDE de Visual Studio. Este modificador restablece de forma opcional la configuración a un archivo de configuración especificado.

La configuración predeterminada se determina mediante el perfil que se ha seleccionado después de iniciar Visual Studio por primera vez.

> [!TIP]
> Para obtener información sobre cómo restablecer la configuración mediante el entorno de desarrollo integrado (IDE), vea [Restablecer la configuración](../environment-settings.md#reset-settings).

## <a name="syntax"></a>Sintaxis

```shell
devenv /ResetSettings [SettingsFile|DefaultCollectionSpecifier]
```

## <a name="arguments"></a>Argumentos

- *SettingsFile*

  Opcional. Ruta de acceso completa y nombre del archivo de configuración que se aplicarán en Visual Studio.

- *DefaultCollectionSpecifier*

  Opcional. Especificador que representa una colección predeterminada de opciones de configuración que se restaurarán. Seleccione uno de los especificadores de colección predeterminada que aparecen en la tabla.

  | Nombre de colección predeterminada | Especificador de la colección |
  | --- | --- |
  | **General** | `General` |
  | **JavaScript** | `JavaScript` |
  | **Visual Basic** | `VB` |
  | **Visual C#** | `CSharp` |
  | **Visual C++** | `VC` |
  | **Desarrollo web** | `Web` |
  | **Desarrollo web (solo código)** | `WebCode` |

## <a name="remarks"></a>Comentarios

Si no se especifica ningún elemento *SettingsFile*, el IDE se abre con la configuración existente.

## <a name="example"></a>Ejemplo

En el primer ejemplo se aplica la configuración almacenada en el archivo `MySettings.vssettings`.

En el segundo, se restaura el perfil predeterminado de Visual C#.

```shell
devenv /resetsettings "%USERPROFILE%\MySettings.vssettings"

devenv /resetsettings CSharp
```

## <a name="see-also"></a>Vea también

- [Configuración del entorno](../environment-settings.md)
- [Personalizar el IDE de Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)