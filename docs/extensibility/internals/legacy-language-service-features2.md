---
title: Incluye 2 del servicio de lenguaje heredado | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], code development aides
ms.assetid: 97c38622-ae0b-4ae0-90ed-604072c298d3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de7e0fa6a229929a34ed3654c3a4e03e02d1129b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333501"
---
# <a name="legacy-language-service-features"></a>Características del servicio de lenguaje heredado
Los temas siguientes enumeran algunas de las características del servicio de lenguaje heredado que puede proporcionar.

 Servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la forma más reciente para implementar características de servicio de lenguaje es usar las extensiones MEF. Para obtener más información acerca de la nueva forma de implementar un servicio de lenguaje, consulte [Editor y extensiones de servicio de lenguaje](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Se recomienda que comience a usar el nuevo editor de API tan pronto como sea posible. Esto mejorará el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.

## <a name="in-this-section"></a>En esta sección
- [Colores de la sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Explica cómo implementar los colores de sintaxis.

- [Formato automático en un servicio de lenguaje heredado](../../extensibility/internals/automatic-formatting-in-a-legacy-language-service.md)

 Explica cómo implementar el formato automático.

- [Información de parámetros en un servicio de lenguaje heredado](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 Explica cómo implementar el parámetro de IntelliSense información sobre herramientas.

- [Finalización de declaraciones en un servicio de lenguaje heredado](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 Explica cómo implementar la lista de instrucciones de IntelliSense y la lista de finalización de miembros.

- [Esquematización y texto oculto en un servicio de lenguaje heredado](../../extensibility/internals/outlining-and-hidden-text-in-a-legacy-language-service.md)

 Explica cómo implementar el texto de esquematización u oculto.

- [Cómo: Proporcionar compatibilidad con esquematización ampliada en un servicio de lenguaje heredado](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 Se explican algunos de los pasos para implementar la compatibilidad con el depurador...

## <a name="related-sections"></a>Secciones relacionadas