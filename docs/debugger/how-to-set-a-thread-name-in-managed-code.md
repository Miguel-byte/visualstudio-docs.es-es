---
title: 'Cómo: establecer un nombre de subproceso en código administrado | Microsoft Docs'
ms.date: 04/27/2017
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Thread.Name property
- threading [Visual Studio], names
- thread names
- debugging [Visual Studio], threads
ms.assetid: c0c4d74a-0314-4b71-81c9-b0b019347ab8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: cf05c0eea2ec05f04c1c792145218f570c4bce96
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72732780"
---
# <a name="how-to-set-a-thread-name-in-managed-code"></a>Cómo: Establecer un nombre de subproceso en código administrado
La denominación de los subprocesos es posible en cualquier edición de Visual Studio. La denominación de los subprocesos es útil para hacer el seguimiento en la ventana **Subprocesos**.

 Para establecer un nombre de subproceso en código administrado, utilice la propiedad <xref:System.Threading.Thread.Name%2A>.

## <a name="example"></a>Ejemplo

```csharp
public class Needle
{
    // This method will be called when the thread is started.
    public void Baz()
    {
        Console.WriteLine("Needle Baz is running on another thread");
    }
}

public void Main()
{
    Console.WriteLine("Thread Simple Sample");
    Needle oNeedle = new Needle();
    // Create a Thread object.
    System.Threading.Thread oThread = new System.Threading.Thread(oNeedle.Baz);
    // Set the Thread name to "MyThread".
    oThread.Name = "MyThread";
    // Starting the thread invokes the ThreadStart delegate
    oThread.Start();
}
```

```VB
Public Class Needle
    ' This method will be called when the thread is started.
    Sub Baz()
        Console.WriteLine("Needle Baz is running on another thread")
    End Sub
End Class

Sub Main()
    Console.WriteLine("Thread Simple Sample")
    Dim oNeedle As New Needle()
   ' Create a Thread object.
    Dim oThread As New System.Threading.Thread(AddressOf oNeedle.Baz)
    ' Set the Thread name to "MyThread".
    oThread.Name = "MyThread"
    ' Starting the thread invokes the ThreadStart delegate
    oThread.Start()
End Sub
```

## <a name="see-also"></a>Vea también
- [Depurar aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Cómo: Establecer un nombre de subproceso en código nativo](../debugger/how-to-set-a-thread-name-in-native-code.md)