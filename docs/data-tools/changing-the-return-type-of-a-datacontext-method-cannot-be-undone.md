---
title: El cambio del tipo devuelto de un método DataContext no se puede deshacer
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 95d75e084b4824cf7cc8e717b1ce9174e76aa2e7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648690"
---
# <a name="changing-the-return-type-of-a-datacontext-method-cannot-be-undone"></a>El cambio del tipo devuelto de un método DataContext no se puede deshacer

El cambio del tipo devuelto de un método DataContext no se puede deshacer. Para volver al tipo generado automáticamente, debe arrastrar de nuevo el elemento desde el **Explorador de servidores** o **Explorador de bases de datos** hasta Object Relational Designer. ¿Está seguro de que desea cambiar el tipo devuelto?

El tipo de valor devuelto de un método de <xref:System.Data.Linq.DataContext> difiere según la ubicación donde se coloque el elemento en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Si se coloca un elemento directamente en una clase de entidad existente, se crea un método de <xref:System.Data.Linq.DataContext> que tiene el tipo de valor devuelto de la clase de entidad. Si se coloca un elemento en un área vacía del [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], se crea un método de <xref:System.Data.Linq.DataContext> que devuelve un tipo generado automáticamente. Se puede cambiar el tipo de valor devuelto de un método de <xref:System.Data.Linq.DataContext> después de agregarlo al panel de métodos. Para examinar o cambiar el tipo de valor devuelto de un método <xref:System.Data.Linq.DataContext>, selecciónelo y haga clic en la propiedad **Tipo devuelto** en la ventana **Propiedades**.

## <a name="to-change-the-return-type-of-a-datacontext"></a>Para cambiar el tipo de valor devuelto de un método de DataContext

- Haga clic en **Sí**.

## <a name="to-exit-the-message-box-and-leave-the-return-type-unchanged"></a>Para salir del cuadro de mensaje sin modificar el tipo de valor devuelto

- Haga clic en **No**.

## <a name="to-revert-to-the-original-return-type-after-changing-the-return-type"></a>Para revertir al tipo de valor devuelto original después de cambiar el tipo de valor devuelto

1. Seleccione el método <xref:System.Data.Linq.DataContext> en [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] y elimínelo.

2. Busque el elemento en el **Explorador de servidores/Explorador de bases de datos** y arrástrelo hasta [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

    Se crea un método de <xref:System.Data.Linq.DataContext> con el tipo de valor devuelto predeterminado original.

## <a name="see-also"></a>Vea también

- [LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) (Herramientas LINQ to SQL en Visual Studio)