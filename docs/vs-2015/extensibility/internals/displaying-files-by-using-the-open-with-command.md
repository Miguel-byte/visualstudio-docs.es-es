---
title: Visualización de archivos mediante la apertura con el comando | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: de43b6c4f441f8c6bde2d6c248274aed3937a7ee
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63408808"
---
# <a name="displaying-files-by-using-the-open-with-command"></a>Visualización de archivos mediante el comando Abrir con
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un proyecto puede pedir el IDE para mostrar el **abrir con** cuadro de diálogo. Esta solicitud pide al usuario que abra un archivo que tiene una selección de editores estándar. Los pasos siguientes describen este proceso.  
  
1. Las llamadas de proyecto <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, especificando un valor de OSE_UseOpenWithDialog para el `OSEOpenDocEditor` parámetro.  
  
2. En función de extensión de nombre de archivo del documento, el IDE determina qué editores enumerados en el puede registro abran el documento especificado y muestra esta información en el **abrir con** cuadro de diálogo.  
  
    > [!NOTE]
    > Los proyectos que tengan un editor intrínseco que debe incluirse en el **abrir con** cuadro de diálogo debe registrar un generador de editores de cada editor de este tipo. Intrínsecos editores sólo funcionan junto con un determinado tipo de proyecto, que se aplica en la implementación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método. El IDE tiene un generador de editores integrados para el editor de texto básico y el editor binario. El IDE también crea una instancia de un generador de editores en nombre de cada asociación de archivo registrado de Windows. Un ejemplo de este archivo es Microsoft Word.  
  
3. Tan pronto como el usuario selecciona un elemento de la **abrir con** cuadro de diálogo, el IDE, a continuación, abre el documento mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> método. Para obtener más información, vea [Cómo: Apertura de editores estándar](../../extensibility/how-to-open-standard-editors.md).  
  
## <a name="see-also"></a>Vea también  
 [Abrir y guardar elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Visualización de archivos mediante el comando Abrir archivo](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)   
 [Cómo: Abrir editores estándar](../../extensibility/how-to-open-standard-editors.md)
