---
title: Consideraciones de seguridad del visualizador | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- visualizers, security
- security [Visual Studio], visualizers
ms.assetid: cdd86bd5-b729-409b-a7c6-374efa091eb1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c1c18ec84a6a62da6cd564c69ef4b83ea76bcfd6
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2019
ms.locfileid: "73187147"
---
# <a name="visualizer-security-considerations"></a>Consideraciones de seguridad del visualizador
Escribir datos en un visualizador implica poner en riesgo la seguridad. En la actualidad, no se conoce ningún tipo de ataque que intente aprovecharse de esta vulnerabilidad potencial, pero los desarrolladores deben tenerlo en cuenta y adoptar las debidas precauciones, tal y como se describe en este documento, para protegerse de futuros ataques.

 Los visualizadores del depurador requieren más privilegios de los permitidos por una aplicación de confianza parcial. Los visualizadores no se cargarán cuando la ejecución se detenga en código con confianza parcial. Para depurar con un visualizador, debe ejecutar el código con plena confianza.

## <a name="possible-malicious-debuggee-component"></a>Posibles componentes malintencionados del depurador
 Los visualizadores están formados, al menos, por dos clases: una en el lado depurador y otra en el lado depurado. Los visualizadores se implementan a menudo en ensamblados independientes colocados en directorios especiales, pero también se pueden cargar fuera del código depurado. Cuando ocurre esto, el depurador extrae el código del lado depurado y lo ejecuta en el depurador con plena confianza.

 La ejecución de código en el lado depurado con plena confianza resulta problemática cuando el código depurado no es de plena confianza. Si un visualizador intenta cargar un ensamblado de confianza parcial del código depurado en el depurador, Visual Studio finalizará el visualizador.

 Sin embargo, sigue existiendo una vulnerabilidad sin importancia. El código del lado depurado se puede asociar a código del lado depurador que se cargó de otro origen (distinto del depurado). A continuación, el lado depurado puede indicar que el lado depurador de confianza realice acciones en su nombre. Si la clase del lado depurado de confianza expone un mecanismo de tipo "eliminar este archivo", por ejemplo, el código depurado de confianza parcial podría invocar ese mecanismo cuando el usuario invoca su visualizador.

 Para mitigar esta vulnerabilidad, esté atento a las interfaces expuestas por el visualizador.

## <a name="see-also"></a>Vea también
- [Arquitectura de un visualizador](../debugger/visualizer-architecture.md)
- [Cómo: Escribir un visualizador](create-custom-visualizers-of-data.md)
- [Create Custom Visualizers](../debugger/create-custom-visualizers-of-data.md) (Crear visualizadores personalizados)
- [Ver datos en el depurador](../debugger/viewing-data-in-the-debugger.md)