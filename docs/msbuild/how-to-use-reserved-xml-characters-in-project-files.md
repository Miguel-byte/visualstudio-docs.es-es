---
title: Procedimiento Usar caracteres XML reservados en archivos de proyecto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, using reserved XML characters
- MSBuild, reserved XML characters
ms.assetid: 1ae37275-96bf-4e6e-897b-6b048e5bbe93
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c79dfa33af5e0e80db682f272c5673856dbbcd8d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62840387"
---
# <a name="how-to-use-reserved-xml-characters-in-project-files"></a>Procedimiento Usar caracteres XML reservados en archivos de proyecto
Al crear archivos de proyecto, es posible que deba utilizar caracteres XML reservados, por ejemplo, en los valores de propiedad o en los valores de parámetro de la tarea. Sin embargo, algunos caracteres reservados se deben reemplazar por una entidad con nombre para que se pueda analizar el archivo del proyecto.

## <a name="use-reserved-characters"></a>Usar caracteres reservados
 En la tabla siguiente se describen los caracteres XML reservados que se deben reemplazar por la entidad con nombre correspondiente para que se pueda analizar el archivo del proyecto.

|Carácter reservado|Entidad con nombre|
|------------------------|------------------|
|\<|&amp;lt;|
|>|&amp;gt;|
|&|&amp;amp;|
|"|&amp;quot;|
|'|&amp;apos;|

#### <a name="to-use-double-quotes-in-a-project-file"></a>Para utilizar comillas dobles en un archivo del proyecto

- Reemplace las comillas dobles por la entidad con nombre correspondiente, &amp;quot;. Por ejemplo, para colocar comillas dobles alrededor de la lista de elementos `EXEFile`, escriba:

    ```xml
    <Message Text="The output file is &quot;@(EXEFile)&quot;."/>
    ```

## <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente, se utilizan comillas dobles para resaltar el nombre de archivo en el mensaje que el archivo del proyecto genera.

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >
    <!-- Set the application name as a property -->
    <PropertyGroup>
        <appname>"HelloWorldCS"</appname>
    </PropertyGroup>
    <!-- Specify the inputs -->
    <ItemGroup>
        <CSFile Include = "consolehwcs1.cs" />
    </ItemGroup>
    <Target Name = "Compile">
        <!-- Run the Visual C# compilation using input
        files of type CSFile -->
        <Csc Sources = "@(CSFile)">
            <!-- Set the OutputAssembly attribute of the CSC task
            to the name of the executable file that is created -->
            <Output
                TaskParameter = "OutputAssembly"
                ItemName = "EXEFile"/>
        </Csc>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is &quot;@(EXEFile)&quot;."/>
    </Target>
</Project>
```

## <a name="see-also"></a>Vea también
- [Referencia de MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
