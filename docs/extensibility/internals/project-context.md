---
title: Contexto del proyecto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8afa595a264f218fcc20f18de1c261a9ead6e030
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725770"
---
# <a name="project-context"></a>Contexto del proyecto
Cuando el usuario agrega o trabaja con proyectos y elementos de proyecto, el IDE usa la noción de contexto del proyecto para determinar cómo se deben realizar varias operaciones.

 Normalmente, los archivos son los objetos de proyecto estándar que el usuario crea explícitamente seleccionando el comando **nuevo proyecto** o hace que esté disponible seleccionando el comando **Abrir proyecto** en el menú **archivo** . En estos casos, los archivos se crean y se abren en el contexto de un proyecto y el tipo de proyecto define el contexto para editar el documento.

 Algunos proyectos proporcionan un contexto muy rico. Por ejemplo, el proyecto administra una conexión de base de datos de ámbito de proyecto o de ámbito de proyecto para el enlace de datos. Con frecuencia, el usuario puede abrir archivos o conexiones de bases de datos directamente mediante un objeto de proyecto determinado, como un elemento de proyecto que se muestra en Explorador de soluciones.

 En otras ocasiones, no se especifica explícitamente el contexto del proyecto de un elemento. Por ejemplo, el contexto de un elemento no está disponible cuando el usuario abre un archivo seleccionando el comando **Abrir archivo existente** en el menú **archivo** , cuando el depurador funciona en un archivo o cuando el usuario hace clic en el comando **Buscar en archivos** en la  **Cuadro de diálogo Buscar y reemplazar** . Para controlar estas situaciones, el IDE llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> para administrar el proceso de búsqueda del mejor proyecto para abrir un documento.

## <a name="see-also"></a>Vea también
- [Prioridad del proyecto](../../extensibility/internals/project-priority.md)
- [Adición de plantillas de proyecto y de elementos de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)