---
title: 'Cómo: Crear plantillas web manualmente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, Web
- templates [Visual Studio], Web
- Web templates [Visual Studio]
- project templates [Visual Studio], Web
ms.assetid: 731c4027-a152-48c5-bfc4-93490bf1949f
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4bf604e747158c651f284c6463c2c2f65ae3c47a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651802"
---
# <a name="how-to-manually-create-web-templates"></a>Cómo: Crear plantillas web manualmente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La creación de una plantilla web es diferente de la creación de otros tipos de plantillas. Dado que las plantillas de proyecto web aparecen en el cuadro de diálogo **Agregar nuevo sitio web** y los elementos de proyecto web se clasifican por lenguaje de programación, el archivo .vstemplate debe especificar la plantilla como una plantilla web e identificar el lenguaje de programación.

> [!NOTE]
> Las plantillas web deben contener un archivo .webproj vacío que se especifica mediante el atributo `File` del elemento `Project`. Aunque los proyectos web no requieren archivos de proyecto, este archivo es necesario para que las plantillas web funcionen correctamente.

### <a name="to-manually-create-a-web-template"></a>Para crear una plantilla web manualmente

1. Cree un proyecto web.

2. Modifique o elimine los archivos del proyecto, o bien agregue nuevos archivos al proyecto.

3. Cree un archivo XML y guárdelo con la extensión de nombre de archivo .vstemplate en el mismo directorio del proyecto. No lo agregue al proyecto en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

4. Cree el archivo XML .vstemplate para proporcionar los metadatos de la plantilla de proyecto. Para más información, vea el ejemplo de la sección siguiente.

5. Busque el elemento `ProjectType` en el archivo .vstemplate y establezca el valor de texto en `Web`.

6. Después del elemento `ProjectType`, agregue un elemento `ProjectSubType` y establezca el valor de texto en el lenguaje de programación de la plantilla. El lenguaje de programación puede ser uno de estos valores:

   - CSharp

   - VisualBasic

     Por ejemplo:

   ```
   <TemplateData>
       ...
       <ProjectType>Web</ProjectType>
       <ProjectSubType>CSharp</ProjectSubType>
       ...
   </TemplateData>
   ```

7. Seleccione los archivos de la plantilla (incluido el archivo .vstemplate), haga clic con el botón derecho en la selección, haga clic en **Enviar a** y, después, en **Carpeta comprimida (en zip)** . Los archivos se comprimen en un archivo .zip.

8. Coloque el archivo de plantilla .zip en el directorio de plantillas de proyecto [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. De forma predeterminada, este directorio es \Mis documentos\Visual Studio *Versión*\My Exported Templates\\.

## <a name="example"></a>Ejemplo
 En este ejemplo se muestra un archivo .vstemplate básico para una plantilla de proyecto web.

```
<VSTemplate Version="2.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple Web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
    </TemplateData>
    <TemplateContent>
        <Project File="WebApplication.webproj">
            <ProjectItem>icon.ico</ProjectItem>
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>
            <ProjectItem>Default.aspx.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Vea también
 [Crear plantillas de proyecto y de elemento](../ide/creating-project-and-item-templates.md) [referencia de esquema de plantilla de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
