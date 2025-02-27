---
title: Procedimiento Recopilar datos de contadores de Windows | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.syscounter
- vs.performance.property.wincounter
helpviewer_keywords:
- windows counters
- performance tools, using windows counters
- profiling tools, using windows counters
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 730345edb42ff3d14608bdcce91bc7b97c4bb478
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62973856"
---
# <a name="how-to-collect-windows-counter-data"></a>Procedimiento Recopilar datos de contadores de Windows

Los contadores de Windows son contadores de rendimiento del sistema que se pueden recopilar durante la generación de perfiles a intervalos establecidos. En la vista Marcas del informe de herramientas de generación de perfiles, aparece una fila **AutoMark** para cada intervalo de la colección. La fila contiene columnas que describen los valores de contador de rendimiento en ese intervalo. Para restringir el análisis a un período de tiempo entre dos marcas concretas, seleccione las marcas, haga clic con el botón derecho y después seleccione **Filtrar por** > **marcas** en el menú contextual.

> [!NOTE]
> Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas. Las aplicaciones para UWP también requieren nuevas técnicas de recopilación. Consulte [Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="to-collect-windows-counter-data"></a>Para recopilar datos de contadores de Windows

1. En el Explorador de rendimiento, haga clic en la sesión para la que desea configurar los contadores de Windows y seleccione **Propiedades**.

2. En las **Páginas de propiedades**, haga clic en**Contadores de Windows**.

3. Seleccione la casilla **Recopilar contadores de Windows**.

4. En el cuadro de texto **Intervalo de recolección (ms)**, escriba un intervalo de tiempo.

5. Seleccione una categoría de la lista desplegable **Categoría de contador**.

6. Seleccione una instancia de la lista desplegable **Instancia**.

7. Seleccione los contadores que desea usar al generar perfiles de la aplicación.

8. Haga clic en **Aplicar.**

## <a name="see-also"></a>Vea también

[Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)
[Propiedades de las sesiones de rendimiento](../profiling/performance-session-properties.md)
[Contadores de Windows y de CPU](../profiling/cpu-and-windows-counters.md)