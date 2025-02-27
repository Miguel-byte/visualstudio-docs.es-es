---
title: Procedimiento Crear una. Archivo de Vsct | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a2483c000bb7c9446ac51bb94ef4006a7b2ac89f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68158344"
---
# <a name="how-to-create-a-vsct-file"></a>Procedimiento Crear un archivo .Vsct
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Hay varias maneras de crear un archivo de configuración (.vsct) basado en XML y Visual Studio Command Table.  
  
- Puede crear un nuevo VSPackage se muestra en el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] plantilla de paquete.  
  
- Puede usar el compilador de configuración de tabla de comando basado en XML, Vsct.exe, para generar un archivo desde un archivo .ctc existente.  
  
- Puede usar Vsct.exe para generar un archivo .vsct a partir de un archivo .cto existente.  
  
- Puede crear manualmente un nuevo archivo de vsct.  
  
  En este tema se explica cómo crear manualmente un nuevo archivo de vsct.  
  
### <a name="to-manually-create-a-new-vsct-file"></a>Para crear manualmente un nuevo archivo de vsct  
  
1. Inicie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
2. En el **archivo** menú, elija **New**y, a continuación, haga clic en **archivo**.  
  
3. En el **plantillas** panel, haga clic en **archivo XML** y, a continuación, haga clic en **abierto**.  
  
4. En el **vista** menú, haga clic en **ventana propiedades** para mostrar las propiedades del archivo XML.  
  
5. En el **propiedades** ventana, haga clic en el botón Examinar (...) en la propiedad de esquemas.  
  
6. En la lista de esquemas XSD, seleccione el esquema vsct.xsd. Si no está en la lista, haga clic en **agregar** y, a continuación, busque el archivo en una unidad local. Haga clic en **Aceptar** cuando haya terminado.  
  
7. En el archivo XML, escriba `<CommandTable` y, a continuación, presione la tecla TAB. Cerrar la etiqueta escribiendo `>`.  
  
     Esto crea un archivo .vsct básica.  
  
8. Rellenar los elementos del archivo XML que desea agregar, de acuerdo con la [VSCT esquema](../../extensibility/vsct-xml-schema-reference.md). Para obtener más información, consulte [Authoring. Archivos Vsct](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Basta con agregar un archivo .vsct a un proyecto no hace que se compile. Debe incorporarlo en el proceso de compilación.  
  
### <a name="to-add-a-vsct-file-to-project-compilation"></a>Para agregar un archivo .vsct a la compilación del proyecto  
  
1. Abra el archivo de proyecto en el editor. Si se carga el proyecto, primero debe descargarlo.  
  
2. Agregar un [elemento ItemGroup](../../msbuild/itemgroup-element-msbuild.md) que contiene un elemento VSCTCompile, tal como se muestra en el ejemplo siguiente.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     Siempre debe establecerse en el elemento ResourceName `Menus.ctmenu`.  
  
3. Si el proyecto contiene un archivo .resx, agregar un elemento EmbeddedResource que contiene un elemento MergeWithCTO, tal como se muestra en el ejemplo siguiente.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     Este marcado debe ir dentro del elemento ItemGroup que contiene recursos incrustados.  
  
4. Abra el archivo de paquete, normalmente denominado *ProjectName*Package.cs o *ProjectName*Package.vb, en el editor.  
  
5. Agregue un atributo ProvideMenuResource a la clase de paquete, tal como se muestra en el ejemplo siguiente.  
  
    ```csharp  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     El primer valor del parámetro debe coincidir con el valor del atributo ResourceName que define en el archivo de proyecto.  
  
## <a name="see-also"></a>Vea también  
 [Creación. Archivos Vsct](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Tabla de comandos de Visual Studio (. Archivos Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Procedimientos: Crear una. Archivo de Vsct desde una existente. Archivos de CTC](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file.md)   
 [Procedimientos: Crear una. Archivo de Vsct desde una existente. Archivo de director de tecnología](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md)   
 [Referencia del esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md)
