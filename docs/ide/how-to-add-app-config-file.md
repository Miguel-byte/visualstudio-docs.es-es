---
title: Adición de un archivo app.config a un proyecto
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 48e6516b48b524c3da4d80bc5171608ac1aea03d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654262"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Procedimiento para agregar un archivo de configuración de la aplicación a un proyecto de C#

Al agregar un archivo de configuración de la aplicación (archivo *app.config*) a un proyecto de C#, puede personalizar el modo en que Common Language Runtime busca y carga archivos de ensamblado. Para obtener más información sobre los archivos de configuración de la aplicación, consulte [Cómo el motor en tiempo de ejecución ubica ensamblados (.NET Framework)](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).

> [!NOTE]
> Las aplicaciones UWP no contienen un archivo *app.config*.

Cuando se compila el proyecto, el entorno de desarrollo copia automáticamente el archivo *app.config*, cambia el nombre de archivo de la copia para que coincida con el archivo ejecutable y, después, mueve la copia al directorio **bin**.

## <a name="to-add-an-application-configuration-file-to-a-c-project"></a>Para agregar un archivo de configuración de la aplicación a un proyecto de C#

1. En la barra de menús, elija **Proyecto** >  **Agregar nuevo elemento**.

     Aparecerá el cuadro de diálogo **Agregar nuevo elemento**.

1. Expanda **Instalado** > **Elementos de Visual C#** y, a continuación, elija la plantilla **Archivo de configuración de aplicación**.

1. En el cuadro de texto **Nombre**, escriba un nombre y, después, elija el botón **Agregar**.

     Se agrega al proyecto un archivo denominado *app.config*.

## <a name="see-also"></a>Vea también

- [Administración de la configuración de la aplicación (.NET)](../ide/managing-application-settings-dotnet.md)
- [Esquema de los archivos de configuración (.NET Framework)](/dotnet/framework/configure-apps/file-schema/index)
- [Configurar aplicaciones (.NET Framework)](/dotnet/framework/configure-apps/index)