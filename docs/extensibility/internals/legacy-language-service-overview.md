---
title: Información general del servicio de lenguaje heredado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], about language services
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8dfec9cc8b57dfb12b3977cc04e2e62ecc0dea96
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726864"
---
# <a name="legacy-language-service-overview"></a>Información general del servicio de lenguaje heredado
Un servicio de lenguaje proporciona compatibilidad con el editor que permite implementar ciertas características de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Las clases de servicio de lenguaje de Managed Package Framework (MPF) proporcionan compatibilidad completa con las características usadas con frecuencia y compatibilidad parcial con otras características.

## <a name="fully-supported-features-in-the-mpf"></a>Características totalmente compatibles en MPF
 Las clases de servicio del lenguaje MPF admiten las siguientes características:

- Resalte de sintaxis

- esquematizar

- Comentar bloques de código

- Coincidencia de llaves

- Fragmentos de código

- Propiedades de documento personalizadas

- Información de parámetros de IntelliSense

- Información rápida de IntelliSense

- Finalización de miembros de IntelliSense

- Finalización de palabras de IntelliSense

## <a name="partially-supported-features-in-the-mpf"></a>Características admitidas parcialmente en MPF
 MPF solo proporciona compatibilidad parcial con las siguientes características. Esto significa que debe implementar los métodos a los que llama el MPF.

- Volver a dar formato al código. Debe proporcionar el código que implementa el nuevo formato.

- Validación de puntos de interrupción mediante la identificación de intervalos de código válidos. Debe proporcionar el código que identifica los intervalos de código.

- Compatibilidad con la ventana **automático** del depurador para mostrar variables. Proporcione el código que determina lo que se va a mostrar en la ventana.

- Compatibilidad con la **barra de navegación** para una navegación rápida entre tipos y miembros. Implementa y devuelve una clase auxiliar que rellena las listas en los cuadros combinados de la **barra de navegación** .

## <a name="implementation"></a>Implementación
 Debe completar varios pasos para implementar el propio servicio de lenguaje y las características del servicio de lenguaje que desea admitir para su idioma. Estos pasos se describen en los temas siguientes:

- [Implementación de un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service2.md)

- [Registro de un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md)

- [Coloreado de sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

- [Coincidencia de llaves en un servicio de lenguaje heredado](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

- [Esquematización en un servicio de lenguaje heredado](../../extensibility/internals/outlining-in-a-legacy-language-service.md)

- [Comentario de código en un servicio de lenguaje heredado](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)

- [Cambio de formato de código en un servicio de lenguaje heredado](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)

- [Propiedades de documento personalizado en un servicio de lenguaje heredado](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)

- [Compatibilidad con fragmentos de código en un servicio de lenguaje heredado](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

- [Compatibilidad con la barra de navegación en un servicio de lenguaje heredado](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

- [Finalización de palabras en un servicio de lenguaje heredado](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)

- [Finalización de miembro en un servicio de lenguaje heredado](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)

- [Información de parámetros en un servicio de lenguaje heredado](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)

- [Información rápida en un servicio de lenguaje heredado](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)

- [Compatibilidad con la ventana Automático en un servicio de lenguaje heredado](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)

- [Validación de puntos de interrupción en un servicio de lenguaje heredado](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)

## <a name="see-also"></a>Vea también
- [Implementación de un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Extensibilidad de servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-extensibility.md)