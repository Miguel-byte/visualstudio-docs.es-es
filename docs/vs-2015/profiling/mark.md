---
title: MarK | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e6d7902ec588af2687b048639a930847ec02b3fa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68155788"
---
# <a name="mark"></a>Marca
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La opción **MarK** (marca) de VSPerfCmd.exe inserta la información especificada en el archivo de datos de generación de perfiles. La marca puede incluirse en un informe de VSPerfReport independiente o en la vista de informe de marca de la interfaz de usuario del generador de perfiles. **Mark** se puede usar para especificar los puntos inicial y final en los filtros de informe y vista.  
  
 La opción **Mark** debe ser la única especificada en la línea de comandos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
VSPerfCmd.exe /Mark:MarkID,[MarkName]  
```  
  
#### <a name="parameters"></a>Parámetros  
 `MarkID`  
 Entero definido por el usuario que aparece como el identificador de marca en los informes y vistas de generador de perfiles. `MarkID` no tiene que ser único.  
  
 `MarkName`  
 (Opcional) Cadena definida por el usuario que aparece como el nombre de la marca en los informes y vistas de generador de perfiles. Si `MarkName` no se especifica, el campo de nombre de la marca aparecerá vacío. Entrecomille las cadenas que contengan espacios o barras diagonales ("/").  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se inserta una marca con un identificador "123" y el nombre de marca "TestMark".  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
VSPerfCmd.exe /Mark:123,TestMark  
```  
  
## <a name="see-also"></a>Otras referencias  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles para aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Generar perfiles de servicios](../profiling/command-line-profiling-of-services.md)
