---
title: Recopilación del seguimiento de ETL con PerfView
ms.date: 09/27/2019
ms.topic: conceptual
helpviewer_keywords:
- perfview
- ETL Trace
author: mikeblome
ms.author: mblome
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Use perfview.exe to collect ETL traces for troubleshooting issues with Visual Studio
ms.openlocfilehash: c1e8a0ca18a857a71fb9cfb6b79a18fef40191a4
ms.sourcegitcommit: 4f82de3fb0cfae226aef1abb40c47e63d2036a5c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72919164"
---
# <a name="collect-an-etl-trace-with-perfview"></a>Recopilación del seguimiento de ETL con PerfView

PerfView es una herramienta que crea archivos ETL (registro de seguimiento de eventos) basados en el [Seguimiento de eventos para Windows](/windows/desktop/ETW/event-tracing-portal) que pueden resultar útiles para solucionar diferentes tipos de problemas con Visual Studio. Ocasionalmente, cuando informa un problema, el equipo del producto puede solicitarle que ejecute PerfView para recopilar información adicional.

## <a name="install-perfview"></a>Instalación de PerfView

Descargue PerfView de [GitHub](https://github.com/Microsoft/perfview/blob/master/documentation/Downloading.md).

## <a name="run-perfview"></a>Ejecución de PerfView

1. Haga clic derecho en **PerfView.exe** en el Explorador de Windows y elija **Ejecutar como administrador** como administrador.
1. En el menú Collect (Recopilar), elija **Collect** (Recopilar).
1. Active **Zip** (Comprimir), **Merge** (Combinar), and **ThreadTime** (Tiempo de subproceso).
1. Aumente **Circular MB** (MB circular) a 1000.
1. Cambie **Current Dir** (Dir actual) para guardar los seguimientos de ETL en una carpeta especificada y el archivo de datos si va a recopilar más de una vez.
1. Para iniciar el registro de los datos, seleccione el botón **Start Collection** (Iniciar la recopilación).
1. Para detener el registro de los datos, seleccione el botón **Stop Collection** (Detener la recopilación). El archivo PrefView.etl.zip se guardará en el directorio especificado.

PerfView puede almacenar solo los datos más recientes que quepan en su búfer. Por lo tanto, intente detener la recolección en cuanto perciba que Visual Studio empieza a bloquearse o ralentizarse. No recopile durante más de 30 segundos después de encontrar un problema.

Para obtener más información, vea el [tutorial de PerfView en Channel9](https://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-1-Collecting-data-with-the-Run-command).
