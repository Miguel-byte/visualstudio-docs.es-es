---
title: Compatibilidad con propiedades de configuración y de proyecto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, supporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8bf0581eee4fade779d89143f4633f1b87d3ce0f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723161"
---
# <a name="support-for-project-and-configuration-properties"></a>Compatibilidad con las propiedades de proyecto y configuración
La ventana **propiedades** del entorno de desarrollo integrado (IDE) de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] puede mostrar las propiedades de configuración y del proyecto. Puede proporcionar una página de propiedades para su propio tipo de proyecto, de modo que el usuario pueda establecer las propiedades de la aplicación.

 Al seleccionar un nodo de proyecto en **Explorador de soluciones** y, a continuación, hacer clic en **propiedades** en el menú **proyecto** , puede abrir un cuadro de diálogo que incluye propiedades de configuración y de proyecto. En [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] y [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], y los tipos de proyecto derivados de estos lenguajes, este cuadro de diálogo aparece como una página con pestañas en el [cuadro de diálogo general, entorno, opciones](../../ide/reference/general-environment-options-dialog-box.md). Para obtener más información, vea [no está en la compilación: Tutorial: exponer propiedades de configuraciónC#y de proyecto ()](https://msdn.microsoft.com/library/d850d63b-25e2-4505-9f3d-eb038d7c1d0e).

 Managed Package Framework for Projects (MPFProj) proporciona clases auxiliares para crear y administrar el nuevo sistema del proyecto. Puede encontrar el código fuente y las instrucciones de compilación en [MPF para proyectos-Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

## <a name="persistence-of-project-and-configuration-properties"></a>Persistencia de las propiedades de configuración y de proyecto
 Las propiedades de configuración y de proyecto se guardan en un archivo de proyecto que tiene cualquier extensión de nombre de archivo asociada al tipo de proyecto, por ejemplo,. csproj,. vbproj y. MyProj. Los proyectos de lenguaje suelen usar un archivo de plantilla para generar el archivo de proyecto. Sin embargo, hay varias formas de asociar tipos y plantillas de proyecto. Para obtener más información, consulte [Descripción del directorio de plantillas (. Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).

 Las propiedades de configuración y de proyecto se crean agregando elementos al archivo de plantilla. Estas propiedades están disponibles para cualquier proyecto creado con el tipo de proyecto que usa esta plantilla. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] proyectos y los MPFProj usan el esquema [Not in Build: información general de MSBuild](/previous-versions/visualstudio/visual-studio-2008/ms171452(v=vs.90)) para los archivos de plantilla. Estos archivos tienen una sección PropertyGroup para cada configuración. Las propiedades de los proyectos se conservan normalmente en la primera sección de PropertyGroup, que tiene un argumento de configuración establecido en una cadena nula.

 En el código siguiente se muestra el inicio de un archivo de proyecto básico de MSBuild.

```
<Project MSBuildVersion="2.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
    <Name>SomeProjectSix</Name>
    <SchemaVersion>2.0</SchemaVersion>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
    <Optimize>false</Optimize>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">
    <Optimize>true</Optimize>
```

 En este archivo de proyecto, `<Name>` y `<SchemaVersion>` son propiedades del proyecto y `<Optimize>` es una propiedad de configuración.

 Es responsabilidad del proyecto conservar el proyecto y las propiedades de configuración del archivo de proyecto.

> [!NOTE]
> Un proyecto puede optimizar la persistencia conservando únicamente los valores de propiedad que difieren de sus valores predeterminados.

## <a name="support-for-project-and-configuration-properties"></a>Compatibilidad con las propiedades de proyecto y configuración
 La clase `Microsoft.VisualStudio.Package.SettingsPage` implementa las páginas de propiedades de configuración y de proyecto. La implementación predeterminada de `SettingsPage` ofrece propiedades públicas a un usuario en una cuadrícula de propiedades genérica. El método `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` selecciona clases derivadas de `SettingsPage` para las cuadrículas de propiedades del proyecto. El método `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` selecciona clases derivadas de `SettingsPage` para las cuadrículas de propiedades de configuración. El tipo de proyecto debe invalidar estos métodos para seleccionar las páginas de propiedades apropiadas.

 La clase `SettingsPage` y la clase `Microsoft.VisualStudio.Package.ProjectNode` ofrecen estos métodos para conservar las propiedades de configuración y del proyecto:

- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` y `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` conservar las propiedades del proyecto.

- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` y `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` conservan las propiedades de configuración.

  > [!NOTE]
  > Las implementaciones de las clases `Microsoft.VisualStudio.Package.SettingsPage` y `Microsoft.VisualStudio.Package.ProjectNode` usan los métodos `Microsoft.Build.BuildEngine` (MSBuild) para obtener y establecer las propiedades de proyecto y configuración del archivo de proyecto.

  La clase que se deriva de `SettingsPage` debe implementar `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` y `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` para conservar las propiedades de configuración o de proyecto del archivo de proyecto.

## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute y ruta de acceso del registro
 Las clases derivadas de `SettingsPage` están diseñadas para compartirse entre los VSPackages. Para que un VSPackage pueda crear una clase derivada de `SettingsPage`, agregue un `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` a una clase derivada de `Microsoft.VisualStudio.Shell.Package`.

 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]

 El VSPackage al que está asociado el atributo no es importante. Cuando se registra un VSPackage con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], se registra el identificador de clase (CLSID) de cualquier objeto que se pueda crear para que una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> pueda crearlo.

 La ruta de acceso del registro de un objeto que se puede crear se determina mediante la combinación de <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, la palabra, CLSID y el GUID del tipo de objeto. Si `MyProjectPropertyPage` clase tiene un GUID de {3c693da2-5bca-49b3-bd95-ffe0a39dd723} y UserRegistryRoot es HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, la ruta de acceso del registro sería HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\ 8.0 exp \ CLSID \\ {3c693da2-5bca-49b3-bd95-ffe0a39dd723}.

## <a name="project-and-configuration-property-attributes-and-layout"></a>Diseño y atributos de la propiedad de configuración y del proyecto
 Los atributos <xref:System.ComponentModel.CategoryAttribute>, <xref:System.ComponentModel.DisplayNameAttribute> y <xref:System.ComponentModel.DescriptionAttribute> determinan el diseño, el etiquetado y la descripción de las propiedades de configuración y del proyecto en una página de propiedades genérica. Estos atributos determinan la categoría, el nombre para mostrar y la descripción de la opción, respectivamente.

> [!NOTE]
> Los atributos equivalentes, SRCategory, LocDisplayName y SRDescription, usan recursos de cadena para la localización y se definen en [MPF para proyectos-Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Observe el fragmento de código siguiente:

 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]

 La propiedad de configuración `MyConfigProp` aparece en la página de propiedades configuración como **mi propiedad config** en la categoría, **mi categoría**. Si la opción está seleccionada, la descripción, **mi Descripción**, aparece en el panel Descripción.

## <a name="see-also"></a>Vea también
- [Adición y eliminación de páginas de propiedades](../../extensibility/adding-and-removing-property-pages.md)
- [Proyectos](../../extensibility/internals/projects.md)
- [Archivos de descripción del directorio de plantilla (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
