---
title: Aspectos básicos de la integración del control de código fuente | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fcce3d8fdcc1c99c9b91bfebec572033ff3beb1a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723474"
---
# <a name="source-control-integration-essentials"></a>Conceptos básicos de la integración del control de código fuente
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] admite dos tipos de integración de control de código fuente: un complemento de control de código fuente que proporciona la funcionalidad básica y se crea mediante la API del complemento de control de código fuente (anteriormente conocida como MSSCCI API) y una solución de integración de control de código fuente basado en VSPackage Esto proporciona una funcionalidad más sólida.

## <a name="source-control-plug-in"></a>Complemento de control de código fuente
 Un complemento de control de código fuente se escribe como un archivo DLL que implementa la API del complemento de control de código fuente. La funcionalidad de integración de control de código fuente y registro se proporciona a través de la API. Este enfoque es más fácil de implementar que un VSPackage de control de código fuente y usa la interfaz de usuario (UI) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para la mayoría de las operaciones de control de código fuente.

 Para implementar un complemento de control de código fuente mediante la API del complemento de control de código fuente, siga estos pasos:

1. Cree un archivo DLL que implemente las funciones especificadas en los [Complementos de control de código fuente](../../extensibility/source-control-plug-ins.md).

2. Registre el archivo DLL mediante las entradas adecuadas del registro, como se describe en [Cómo: instalar un complemento de control de código fuente](../../extensibility/internals/how-to-install-a-source-control-plug-in.md).

3. Cree una interfaz de usuario auxiliar y mostrarla cuando el paquete del adaptador de control de código fuente lo solicite (el componente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que controla la funcionalidad de control de código fuente a través de complementos de control de código fuente).

   Para obtener más información, vea [crear un complemento de control de código fuente](../../extensibility/internals/creating-a-source-control-plug-in.md).

## <a name="source-control-vspackage"></a>VSPackage de control de código fuente
 Una implementación de VSPackage de control de código fuente permite desarrollar un reemplazo personalizado para la interfaz de usuario del control de código fuente de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Este enfoque proporciona un control completo sobre la integración del control de código fuente, pero requiere que proporcione los elementos de la interfaz de usuario e implemente las interfaces de control de código fuente que, de lo contrario, se proporcionaría en el enfoque del complemento.

 Para implementar un VSPackage de control de código fuente, debe:

1. Cree y registre su propio VSPackage de control de código fuente, como se describe en [registro y selección](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).

2. Reemplace la interfaz de usuario de control de código fuente predeterminada por la interfaz de usuario personalizada. Vea [interfaz de usuario personalizada](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).

3. Especifique los glifos que se van a usar y controle **Explorador de soluciones** eventos de glifo. Vea [control de glifo](../../extensibility/internals/glyph-control-source-control-vspackage.md).

4. Controlar los eventos de edición de consultas y de guardado de consultas, como se muestra en [query Edit Query Save](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md).

   Para obtener más información, vea [crear un VSPackage de control de código fuente](../../extensibility/internals/creating-a-source-control-vspackage.md).

## <a name="see-also"></a>Vea también
- [Información general](../../extensibility/internals/source-control-integration-overview.md)
- [Creación de un complemento de control de código fuente](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Creación de un VSPackage de control de código fuente](../../extensibility/internals/creating-a-source-control-vspackage.md)