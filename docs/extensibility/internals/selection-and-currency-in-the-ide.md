---
title: Selección y moneda en el IDE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: edff400420ca5f0c93e1df85fb9118eee6302d02
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723964"
---
# <a name="selection-and-currency-in-the-ide"></a>Selección y moneda en el IDE
El entorno de desarrollo integrado (IDE) de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mantiene información acerca de los objetos seleccionados actualmente por los usuarios mediante el *contexto*de selección. Con el contexto de selección, los VSPackages pueden participar en el seguimiento de moneda de dos maneras:

- Al propagar la información de moneda sobre los VSPackages al IDE.

- Mediante la supervisión de las selecciones activas de los usuarios en el IDE.

## <a name="selection-context"></a>Contexto de selección
 El IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] realiza un seguimiento global de la moneda del IDE en su propio objeto de contexto de selección global. En la tabla siguiente se muestran los elementos que componen el contexto de selección.

|Elemento|Descripción|
|-------------|-----------------|
|Jerarquía actual|Normalmente, el proyecto actual; una jerarquía actual nula indica que la solución en su conjunto es actual.|
|ItemID actual|Elemento seleccionado dentro de la jerarquía actual; cuando hay varias selecciones en una ventana de proyecto, puede haber varios elementos actuales.|
|@No__t_0 actual|Contiene uno o más objetos para los que el ventana Propiedades debe mostrar las propiedades.|

 Además, el entorno mantiene dos listas globales:

- Lista de identificadores de comandos de la interfaz de usuario activa

- Lista de los tipos de elemento activos actualmente.

### <a name="window-types-and-selection"></a>Tipos y selección de ventanas
 El IDE de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] organiza las ventanas en dos tipos generales:

- Jerarquía de tipos de ventanas

- Ventanas de marco, como ventanas de herramientas y de documentos

  El IDE realiza un seguimiento de la moneda de manera diferente para cada uno de estos tipos de ventanas.

  La ventana de tipo de proyecto más común es el explorador de soluciones, que controla el IDE. Una ventana de tipo de proyecto realiza un seguimiento de la jerarquía global y el ItemID del contexto de selección global, y la ventana se basa en la selección del usuario para determinar la jerarquía actual. En el caso de las ventanas de tipo de proyecto, el entorno proporciona la <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> de servicio global, a través de la cual los VSPackages pueden supervisar los valores actuales de los elementos abiertos. La exploración de propiedades en el entorno está controlada por este servicio global.

  Por otro lado, las ventanas de marco usan el DocObject dentro de la ventana de marco para enviar el valor SelectionContext (Hierarchy/ItemID/SelectionContainer trío). . Las ventanas de marco usan la <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> de servicio para este fin. El DocObject solo puede enviar valores para el contenedor de selección, de modo que los valores locales de Hierarchy y ItemID no se modifican, como es habitual en los documentos MDI secundarios.

### <a name="events-and-currency"></a>Eventos y moneda
 Pueden producirse dos tipos de eventos que afectan a la noción de moneda del entorno:

- Eventos que se propagan al nivel global y cambian el contexto de selección de marcos de ventana. Entre los ejemplos de este tipo de evento se incluye la apertura de una ventana secundaria MDI, la apertura de una ventana de herramientas global o la apertura de una ventana de herramientas de tipo de proyecto.

- Eventos que cambian los elementos de los que se realiza un seguimiento en el contexto de selección de marcos de ventana. Entre los ejemplos se incluye cambiar la selección dentro de un DocObject o cambiar la selección en una ventana de tipo de proyecto.

## <a name="see-also"></a>Vea también
- [Objetos de contexto de selección](../../extensibility/internals/selection-context-objects.md)
- [Comentarios para el usuario](../../extensibility/internals/feedback-to-the-user.md)