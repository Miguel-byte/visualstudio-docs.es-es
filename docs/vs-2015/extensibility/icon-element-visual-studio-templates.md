---
title: Icon (elemento) (plantillas de Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Icon
helpviewer_keywords:
- Icon element [Visual Studio project templates]
ms.assetid: ec01d903-f4c2-4ca2-9cbc-e939ec84016c
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3de31652af7bc3fd2da3c5e67e37df8e9ff120e8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204001"
---
# <a name="icon-element-visual-studio-templates"></a>Icon (Elemento, Plantillas de Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Especifica la ruta de acceso y el nombre de archivo del archivo de imagen que actúa como el icono, que aparece en cualquiera de los **nuevo proyecto** o el **Agregar nuevo elemento** cuadro de diálogo, para la plantilla.  
  
 \<VSTemplate>  
 \<TemplateData >  
 \<Icono >  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<Icon>  
    IconFileName  
</Icon>  
```  
  
```  
<Icon Package="{PackageID}" ID="ResourceID" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|DESCRIPCIÓN|  
|---------------|-----------------|  
|`Package`|Atributo opcional para escenarios de usuario avanzada.<br /><br /> Un identificador GUID que especifica el id. paquete de Visual Studio.|  
|`ID`|Atributo opcional para escenarios de usuario avanzada.<br /><br /> Especifica el identificador de recurso de Visual Studio.|  
  
### <a name="child-elements"></a>Elementos secundarios  
 Ninguno.  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|DESCRIPCIÓN|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Clasifica la plantilla y define cómo se muestra en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento** .|  
  
## <a name="text-value"></a>Valor de texto  
 Se requiere un valor de texto a menos que se usen los atributos `Package` y `ID`.  
  
 El texto proporciona la ruta de acceso y el nombre del icono de la plantilla que va a aparecer en el **nuevo proyecto** cuadro de diálogo.  
  
## <a name="remarks"></a>Comentarios  
 `Icon` es un elemento secundario obligatorio de `TemplateData`.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra los metadatos para una plantilla de proyecto para un [!INCLUDE[csprcs](../includes/csprcs-md.md)] aplicación.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md)
