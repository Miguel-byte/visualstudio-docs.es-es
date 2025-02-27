---
title: Soluciones VBA y Office en Visual Studio en comparación con
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA code, managed code extensions
- managed code extensions [Office development in Visual Studio], VBA compared to
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 24e7d3674712a17d940b94637db808c0d91d2d6a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62982120"
---
# <a name="vba-and-office-solutions-in-visual-studio-compared"></a>Soluciones VBA y Office en Visual Studio en comparación con
  Microsoft Visual Basic para aplicaciones (VBA) utiliza código no administrado que se integra estrechamente con las aplicaciones de Office. Los proyectos de Microsoft Office creados con Visual Studio le permiten sacar partido de .NET Framework y las herramientas de diseño de Visual Studio.

 Para obtener información acerca de los tipos de soluciones de Office puede crear con Visual Studio, consulte [información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

## <a name="comparison"></a>Comparación
 En la tabla siguiente se proporciona una comparación básica entre las soluciones de VBA y de Office en Visual Studio.

|Soluciones de VBA|Soluciones de Office en Visual Studio|
|-------------------|---------------------------------------|
|Utiliza código que está conectado a un documento concreto y se conserva en él.|Utiliza código que se almacena por separado respecto al documento (para personalizaciones de nivel de documento), o en un ensamblado cargado por la aplicación (para complementos VSTO).|
|Funciona con los modelos de objetos de Office y las API de VBA.|Proporciona acceso a los modelos de objetos de Office y a las API de [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] .|
|Diseñado para la grabación de macros y para proporcionar una experiencia de desarrollo más sencilla.|Diseñado para proporcionar seguridad, facilitar el mantenimiento del código y permitir utilizar todo el entorno de desarrollo integrado (IDE) de Visual Studio.|
|Funciona bien con soluciones que se benefician de una estrecha integración con aplicaciones de Office.|Funciona bien con soluciones que se benefician de todos los recursos de Visual Studio y [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].|
|Tiene limitaciones para las empresas, especialmente en las áreas de seguridad e implementación.|Se ha diseñado para su uso en empresas.|

 Algunas cosas siguen siendo más fáciles de hacer rápidamente con VBA. En concreto, se recomienda seguir utilizando VBA para:

- Funciones de hoja de cálculo personalizadas.

- Grabación de macros.

## <a name="combine-vba-solutions-and-office-solutions-created-by-using-visual-studio"></a>Combinar soluciones de VBA y soluciones de Office creadas con Visual Studio
 Puede llamar a código de VBA desde soluciones de Office creadas con Visual Studio. Asimismo, puede llamar a código en soluciones de Office creadas con Visual Studio desde VBA. La técnica específica será diferente dependiendo de si la solución de Office es un complemento VSTO o una personalización de nivel de documento. Para obtener más información, consulte [llamar a código en complementos VSTO desde otras soluciones de Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md) y [combinar VBA y personalizaciones de nivel de documento](../vsto/combining-vba-and-document-level-customizations.md).

## <a name="see-also"></a>Vea también
- [Información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Llamar a código en complementos VSTO desde otras soluciones de Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Combinar VBA y personalizaciones de nivel de documento](../vsto/combining-vba-and-document-level-customizations.md)
- [Arquitectura de las personalizaciones de nivel de documento](../vsto/architecture-of-document-level-customizations.md)
- [Arquitectura de complementos VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Proteger soluciones de Office](../vsto/securing-office-solutions.md)
- [Introducción a &#40;desarrollo de Office en Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
