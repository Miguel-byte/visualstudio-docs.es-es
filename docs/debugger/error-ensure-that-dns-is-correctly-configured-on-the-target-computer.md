---
title: 'Error: Asegúrese de que DNS esté configurado correctamente en el equipo de destino | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.callback_dns_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c8a9a5346016964882bb524187d01ca83c203be1
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911561"
---
# <a name="error-ensure-that-dns-is-correctly-configured-on-the-target-computer"></a>Error: Asegúrese de que DNS está bien configurado en el equipo de destino
Al intentar realizar una depuración remota, es posible recibir el siguiente mensaje de error:

```cmd
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.
```

 Este error se produce cuando el equipo de destino no puede resolver el nombre del equipo host del depurador de Visual Studio. Compruebe la configuración de DNS en el equipo de destino.

- Para obtener información sobre cómo ver la configuración de DNS en Windows 8.1, Vista, Windows 7, Windows Server 2012, Windows Server 2008 o Windows Server 2008 R2, haga esto: en el menú **Inicio**, elija **Ayuda y soporte técnico** y después busque **Cambiar la configuración de TCP/IP**.

- Para obtener más información, vaya al [sitio web de Microsoft Windows](https://www.microsoft.com/windows/) y busque **Cambiar la configuración de TCP/IP**.

  Si no puede resolver el problema de DNS, intente ejecutar el depurador remoto con una cuenta diferente. Este error solo se produce cuando se ejecuta el depurador remoto con el sistema local o cuenta de servicio de red. Si ejecuta el depurador remoto con otra cuenta, puede que la cuenta use la autenticación NTLM, que no requiere DNS. . Para el procedimiento, consulte [error: el servicio Visual Studio Remote Debugger del equipo de destino no se puede volver a conectar a este equipo](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).
