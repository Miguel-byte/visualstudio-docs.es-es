---
title: No hay ningún origen disponible | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.nosource
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- No Source Code Available for the Current Location dialog box
ms.assetid: ed0732bc-4b8c-490f-adb1-af06869a2a6b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9f08ed499e61e54ffbc6508bc8353ea955d9a20c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72730871"
---
# <a name="no-source-available"></a>No hay código fuente disponible
El proyecto no contiene código fuente para el código que se está intentando ver. El motivo habitual es hacer doble clic en un módulo que no tiene código fuente en la **Ventana Pila de llamadas** o en la **Ventana Subprocesos**. Puede seguir depurando, pero no puede utilizar la ventana de código fuente para establecer puntos de interrupción y realizar otras acciones en dicha ubicación. Si necesita establecer un punto de interrupción, utilice la **Ventana Desensamblado** en su lugar.

 En las Páginas de propiedades de la solución, puede cambiar los directorios en los que el depurador busca archivos de código fuente e indicar al depurador que omita los archivos de código fuente seleccionados. Vea [depurar archivos de código fuente, propiedades comunes, páginas de propiedades de solución (cuadro de diálogo)](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md).

 **Examinar para buscar código fuente** Haga clic en este vínculo para abrir un cuadro de diálogo donde puede buscar el código fuente.

 **Mostrar desensamblado** Inicia la **ventana Desensamblado**.

 **Mostrar siempre el desensamblado de los archivos de origen que faltan** Seleccione esta opción para mostrar la **ventana Desensamblado** automáticamente cuando no haya ningún origen disponible. Esta configuración también se puede cambiar en el cuadro de diálogo **Opciones**, categoría **Depuración**, página **General**. Para ello active o desactive **Mostrar desensamblado si el código fuente no está disponible**.

## <a name="see-also"></a>Vea también
- [Depurar archivos de código fuente, Propiedades comunes, Cuadro de diálogo Páginas de propiedades de Solución](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)
- [Especificar archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [SOS.dll (Extensión de depuración de SOS)](/dotnet/framework/tools/sos-dll-sos-debugging-extension)