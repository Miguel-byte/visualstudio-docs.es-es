---
title: SortOrder (elemento, plantillas de Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder
helpviewer_keywords:
- SortOrder element [Visual Studio Templates]
- <SortOrder> element [Visual Studio Templates]
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2875bcb4583c1d2ec47a935d1a8bb4f0de109a92
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719923"
---
# <a name="sortorder-element-visual-studio-templates"></a>SortOrder (Elemento, Plantillas de Visual Studio)
Especifica un valor que se usa para organizar la plantilla, entre otras plantillas de la misma categoría, tal y como aparece en el cuadro de diálogo **nuevo proyecto** o **Agregar nuevo elemento** .

 \<VSTemplate > \<TemplateData > \<SortOrder >

## <a name="syntax"></a>Sintaxis

```
<SortOrder> ... </SortOrder>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos
 Ninguno.

### <a name="child-elements"></a>Elementos secundarios
 Ninguno.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Clasifica la plantilla y define cómo se muestra en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento** .|

## <a name="text-value"></a>Valor de texto
 Se requiere un valor de texto.

 @No__t_0 que representa el valor del criterio de ordenación.

## <a name="remarks"></a>Comentarios
 `SortOrder` es un elemento opcional. El valor predeterminado es 100 y todos los valores deben ser múltiplos de 10.

 El elemento `SortOrder` se omite para las plantillas creadas por el usuario. Todas las plantillas creadas por el usuario se ordenan alfabéticamente.

 Las plantillas que tienen pocos valores de orden de ordenación aparecen en el cuadro de diálogo **nuevo proyecto** o **nuevo elemento para agregar** antes que las plantillas que tienen valores de criterio de ordenación altos.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestran los metadatos de una plantilla de clase de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] estándar.

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class template.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <SortOrder>290</SortOrder>
        <DefaultName>MyClass</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

 En este ejemplo, el elemento `SortOrder` es relativamente alto. Es probable que otras plantillas de elementos de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] tengan un valor `SortOrder` inferior a `290` y aparecerán delante de esta plantilla en el cuadro de diálogo **nuevo elemento** .

## <a name="see-also"></a>Vea también
- [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md)