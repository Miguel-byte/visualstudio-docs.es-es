---
title: Uso compartido de la devolución de llamada de registro de Unity con VSTU | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
caps.latest.revision: 5
author: conceptdev
ms.author: crdun
manager: jillfra
ms.openlocfilehash: b58d693980ffc55ccfe613d52e868bccca9908b8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68145731"
---
# <a name="share-the-unity-log-callback-with-vstu"></a>Compartir la devolución de llamada de registro de Unity con VSTU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio Tools para Unity registra una devolución de llamada de registro con Unity para poder transmitir su consola a Visual Studio. Si las secuencias de comandos del editor también registran una devolución de llamada de registro con Unity, la devolución de llamada de VSTU puede interferir con la devolución de llamada. Para evitar esta posibilidad, use el evento `VisualStudioIntegration.LogCallback` para cooperar con VSTU.  
  
## <a name="demonstrates"></a>Demostraciones  
 Cómo compartir la devolución de llamada de registro de Unity creada por Visual Studio Tools para Unity.  
  
## <a name="example"></a>Ejemplo  
  
```csharp  
using System;  
  
using UnityEngine;  
using UnityEditor;  
  
using SyntaxTree.VisualStudio.Unity.Bridge;  
  
[InitializeOnLoad]  
public class LogCallbackHook  
{  
    static LogCallbackHook()  
    {  
        VisualStudioIntegration.LogCallback += (string condition, string trace, LogType type) =>  
        {  
            // place code that implements your log callback here  
        };  
    }  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo: generación de archivos del proyecto](../cross-platform/customize-project-files-created-by-vstu.md)
