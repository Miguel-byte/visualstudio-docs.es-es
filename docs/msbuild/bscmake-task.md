---
title: Tarea BscMake | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.task.bscmake
- VC.Project.VCBscMakeTool.PreserveSBR
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), tasks
- BscMake task (MSBuild (C++))
ms.assetid: bb98fc67-cad8-43a7-9598-60df6d734db2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: acf9c0df17ec0e1bb97c1426d5d312f616de0a8e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747383"
---
# <a name="bscmake-task"></a>Tarea BscMake
> [!IMPORTANT]
> El IDE de Visual Studio ya no usa BscMake. A partir de Visual Studio 2008, la información de examen se almacena automáticamente en un archivo *.sdf* en la carpeta *Solution*.

 Incluye la herramienta Utilidad de mantenimiento de información de examen de Microsoft (*bscmake.exe*).  La herramienta *bscmake.exe* compila un archivo de información de examen ( *.bsc*) a partir de los archivos del explorador de origen ( *.sbr*) que se crean durante la compilación. Use el **Examinador de objetos** para ver un archivo *.bsc*. Para obtener más información, vea [Referencia de BSCMAKE](/cpp/build/reference/bscmake-reference).

## <a name="parameters"></a>Parámetros
 En la siguiente tabla se describen los parámetros de la tarea **BscMake**. La mayoría de los parámetros de tarea corresponden a una opción de línea de comandos.

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|**AdditionalOptions**|Parámetro **String** opcional.<br /><br /> Una lista de opciones especificada en la línea de comando. Por ejemplo, /\<option1> /\<option2> /\<option#>. Use este parámetro para especificar opciones que no están representadas por ningún otro parámetro de tarea **BscMake**.<br /><br /> Para obtener más información, vea las opciones en [Opciones de BSCMAKE](/cpp/build/reference/bscmake-options).|
|**OutputFile**|Parámetro **String** opcional.<br /><br /> Especifica un nombre de archivo que invalida el nombre de archivo de salida predeterminado.<br /><br /> Para obtener más información, vea la opción **/o** en [Opciones de BSCMAKE](/cpp/build/reference/bscmake-options).|
|**PreserveSBR**|Parámetro **Boolean** opcional.<br /><br /> Si es `true`, fuerza una compilación no incremental. Se produce una compilación no incremental completa independientemente de si existe o no un archivo *.bsc*, y evita que se trunquen los archivos *.sbr*.<br /><br /> Para obtener más información, vea la opción **/n** en [Opciones de BSCMAKE](/cpp/build/reference/bscmake-options).|
|**Sources**|Parámetro opcional de tipo **ITaskItem[]** .<br /><br /> Define una matriz de elementos de archivo origen de MSBuild que las tareas pueden consumir y emitir.|
|**SuppressStartupBanner**|Parámetro **Boolean** opcional.<br /><br /> Si es `true`, evita que se muestre el copyright y el mensaje de número de versión cuando la tarea se inicia.<br /><br /> Para obtener más información, vea la opción **/NOLOGO** en [Opciones de BSCMAKE](/cpp/build/reference/bscmake-options).|
|**TrackerLogDirectory**|Parámetro **String** opcional.<br /><br /> Especifica el directorio de registro de seguimiento.|

## <a name="see-also"></a>Vea también
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)