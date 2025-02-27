---
title: Data Tools para .NET
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
- dotnet
ms.openlocfilehash: 224fef3a02a2441553728a9a75fc5f9c456081a1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648088"
---
# <a name="visual-studio-data-tools-for-net"></a>Visual Studio Data Tools para .NET

En conjunto, Visual Studio y .NET proporcionan una amplia compatibilidad con API y herramientas para conectarse a bases de datos, modelar datos en memoria y mostrar los datos en la interfaz de usuario. Las clases .NET que proporcionan la funcionalidad de acceso a datos se conocen como [ADO.net](/dotnet/framework/data/adonet/index). ADO.NET, junto con las herramientas de datos en Visual Studio, se diseñó principalmente para admitir bases de datos relacionales y XML. Estos días, muchos proveedores de bases de datos NoSQL, o terceros, ofrecen proveedores de ADO.NET.

[.Net Core](/dotnet/core/) admite ADO.net, excepto los conjuntos de valores y sus tipos relacionados. Si el destino es .NET Core y requiere una capa de asignación relacional de objetos (ORM), use [Entity Framework Core](/ef/core/).

En el diagrama siguiente se muestra una vista simplificada de la arquitectura básica:

![Arquitectura de ADO.NET](../data-tools/media/raddata-ado-net-architecture-diagram.png)

## <a name="typical-workflow"></a>Flujo de trabajo típico

El flujo de trabajo típico es el siguiente:

1. Instale una base de datos de desarrollo o de prueba en el equipo local. Vea [instalar sistemas de base de datos, herramientas y ejemplos](../data-tools/installing-database-systems-tools-and-samples.md). Si usa un servicio de datos de Azure, este paso no es necesario.

2. Pruebe la conexión con la base de datos (o el servicio o el archivo local) en Visual Studio. Consulte [Agregar nuevas conexiones](../data-tools/add-new-connections.md).

3. Opta Use las herramientas para generar y configurar un nuevo modelo. Los modelos basados en Entity Framework son la recomendación predeterminada para las nuevas aplicaciones. El modelo, cualquiera que use, es el origen de datos con el que interactúa la aplicación. El modelo se encuentra lógicamente entre la base de datos o el servicio y la aplicación. Consulte [agregar nuevos orígenes de datos](../data-tools/add-new-data-sources.md).

4. Arrastre el origen de datos desde la ventana **orígenes de datos** hasta una superficie de diseño Windows Forms, ASP.NET o Windows Presentation Foundation para generar el código de enlace de datos que mostrará los datos al usuario de la forma que especifique. Vea [enlazar controles a datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

5. Agregue código personalizado para cosas como reglas de negocios, búsqueda y validación de datos, o para aprovechar las ventajas de la funcionalidad personalizada que expone la base de datos subyacente.

Puede omitir el paso 3 y programar una aplicación .NET para emitir comandos directamente a una base de datos, en lugar de usar un modelo. En este caso, encontrará la documentación pertinente aquí: [ADO.NET](/dotnet/framework/data/adonet/index). Tenga en cuenta que todavía puede usar el Asistente para la **configuración de orígenes de datos** y los diseñadores para generar código de enlace de datos al rellenar sus propios objetos en la memoria y, a continuación, enlazar los controles de IU de datos a esos objetos.

## <a name="see-also"></a>Vea también

- [Acceso a datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)