---
title: Crear definiciones de sitio para SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5a75b7143412d360a7663e7cf94a1244d66d15a2
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984523"
---
# <a name="create-site-definitions-for-sharepoint"></a>Crear definiciones de sitio para SharePoint
  El proyecto de definición del sitio de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] le permite crear una *definición de sitio*, que sirve como base para un nuevo sitio de SharePoint. Estas definiciones no solo determinan la apariencia y el comportamiento del sitio de SharePoint, sino también el contenido y la funcionalidad predeterminados. En la definición, puede incluir listas preconfiguradas, tipos de contenido, receptores de eventos, imágenes y otros elementos. SharePoint incluye algunas definiciones de sitio, como el BLOG, por ejemplo. Cuando se crea un sitio basado en la definición del sitio de BLOG, el sitio contiene las listas, los elementos Web y otros elementos que requiere un sitio de blog.

 Para obtener más información acerca de las definiciones de sitio, consulte [plantillas de sitio y definiciones](/previous-versions/office/developer/sharepoint-2010/ms434313(v=office.14)).

## <a name="site-definition-projects"></a>Proyectos de definición de sitio
 Los proyectos de definición de sitio en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proporcionan solo los archivos básicos que necesita un sitio de SharePoint; no proporcionan ninguna funcionalidad predeterminada. Debe agregar archivos y contenido para proporcionar la funcionalidad que desee. Puede compilar el sitio manualmente creando y agregando los archivos que necesita.

## <a name="feature-stapling"></a>Grapado de características
 Una ventaja de crear definiciones de sitio en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] es que usan automáticamente el *grapado de características*. El grapado de características asocia una característica a una definición de sitio en lugar de insertar su funcionalidad en la propia definición de sitio. Esto le permite agregar la característica a cualquier sitio creado mediante la definición del sitio sin modificar la definición del sitio original. Para obtener más información, consulte [grapado de características](/previous-versions/office/developer/sharepoint-2007/bb861862(v=office.12)).

## <a name="site-definition-project-components"></a>Componentes del proyecto de definición de sitio
 Cuando se crea una solución de definición de sitio, se agregan los siguientes archivos predeterminados a su nodo **SiteDefinition** .

|Nombre de archivo|Descripción|
|---------------|-----------------|
|*default. aspx*|La Página principal de ASPX predeterminada para el nuevo sitio de SharePoint.|
|*archivo Onet. XML*|Especifica la configuración del nuevo sitio, los componentes de la plantilla de definición del sitio y el comportamiento predeterminado. Esta configuración puede incluir atributos como los tipos de contenido que están habilitados, las vistas de lista predeterminadas, los archivos de plantilla de documento y los elementos Web que se incluyen con el sitio. De forma predeterminada, en la sección `Modules` se enumeran los archivos que se van a agregar al sitio de SharePoint y cómo se configuran.|
|*webtemp_\<SiteDefinitionName >. XML*|Especifica las configuraciones de definición de sitio que aparecen en la sección **selección de plantilla** de la página **nuevo sitio de SharePoint** .|

 De forma predeterminada, todas las definiciones de sitio se almacenan en la carpeta *\<unidad: > \Archivos de Programa\archivos Comunes\microsoft Shared\Web Server Extensions\14\TEMPLATE\SiteTemplates* Cada definición de sitio tiene su propia subcarpeta.

## <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Tutorial: Crear un proyecto de definición de sitio básico](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|Conduce paso a paso a través de la creación de un proyecto de definición de sitio básico en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|
|[Cómo: crear una definición y una configuración de sitio personalizadas](/previous-versions/office/developer/sharepoint-2010/ms454677(v=office.14))|Describe cómo crear una definición de sitio personalizada en SharePoint mediante la copia de una definición de sitio existente y la modificación de la copia.|
|[*WebTemp. XML*](/previous-versions/office/developer/sharepoint-2010/ms447717(v=office.14))|Describe el archivo original que especifica las definiciones de sitio disponibles en la sección **selección de plantilla** de la página **nuevo sitio de SharePoint** .|
|[Localizar soluciones de SharePoint](../sharepoint/localizing-sharepoint-solutions.md)|Describe cómo preparar las soluciones de SharePoint para su uso global.|
|[Crear elementos Web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Describe cómo puede crear partes de una página de SharePoint que los usuarios pueden modificar.|
|[Crear controles reutilizables para elementos Web o páginas de aplicación](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Describe cómo puede crear controles reutilizables que se ejecutan en páginas de aplicación y elementos web.|
|[Visual Web Developer](/previous-versions/visualstudio/visual-studio-2010/ms178093(v=vs.100))|Describe cómo utilizar el diseñador que aparece al abrir una página web en el proyecto.|
|[Información general de ASP.NET Web Pages](/previous-versions/aspnet/428509ah(v=vs.100))|Proporciona información general sobre la estructura de [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] páginas web, cómo se procesan las páginas [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]y cómo las páginas [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] muestran el marcado que cumple con los estándares XHTML.|
|[Sintaxis de la Página Web ASP.NET](/previous-versions/aspnet/k33801s3(v=vs.100))|Describe los elementos de marcado que componen una página de ASP.NET.|
|[ASP.NET Web Pages de programación](/previous-versions/aspnet/0yt4zca8(v=vs.100))|Proporciona información sobre cómo crear controladores de eventos en [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] páginas y cómo trabajar con scripts de cliente.|
|[Programar en Windows SharePoint Services](/previous-versions/office/developer/sharepoint-services/ms430674(v=office.12))|Describe cómo utilizar el modelo de objetos administrados que se proporciona en [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)].|

## <a name="see-also"></a>Vea también
- [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)
