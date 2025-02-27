---
title: Propiedades de MSBuild compatibles con SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, MSBuild properties
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5470160c6b0af1af39238a14319ad497e1541a43
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985172"
---
# <a name="msbuild-properties-supported-by-sharepoint"></a>Propiedades de MsBuild compatibles con SharePoint
  Cualquier [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] propiedad definida en el archivo Microsoft. VisualStudio. SharePoint. targets, el archivo de proyecto o el archivo de usuario de proyecto se puede utilizar en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proyectos de SharePoint. Además de las propiedades de [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] comunes que proporciona el proyecto, SharePoint define propiedades adicionales que son específicas de los proyectos de SharePoint.

 Para obtener una lista de las propiedades de [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] comunes, vea [propiedades comunes del proyecto de MSBuild](/previous-versions/dotnet/netframework-4.0/bb629394(v=vs.100)). Para obtener una lista completa de las propiedades que admite el lenguaje de programación, busque en el archivo *. targets* , el archivo de proyecto ( *. csproj* o *. vbproj*) o el archivo de usuario del proyecto (*csproj. User* o *. vbproj. User*).

## <a name="msbuild-properties-specific-to-sharepoint"></a>Propiedades de MsBuild específicas de SharePoint
 En la tabla siguiente se enumeran las propiedades de [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] que se aplican específicamente a los proyectos de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Existen otras propiedades, pero son para uso interno.

|Nombre de la propiedad|Descripción|
|-------------------|-----------------|
|SharePointSiteUrl|Cadena que representa el [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] en el sitio de SharePoint.|
|SandboxedSolution|Un valor booleano que indica si la solución es una solución en espacio aislado.|
|ActiveDeploymentConfiguration|La configuración de implementación activa.|
|IncludeAssemblyInPackage|Valor booleano que indica si el ensamblado está incluido en el archivo de paquete.|
|PreDeploymentCommand|Valor de cadena que representa el comando que se va a ejecutar en el paso de comando anterior a la implementación.|
|PostDeploymentCommand|Valor de cadena que representa el comando que se va a ejecutar en el paso de comando posterior a la implementación.|
|CustomBeforeSharePointTargets|Cadena que representa la ruta de acceso de un archivo de destino [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]. Si el archivo de destinos existe y está definido, se importa antes que los datos de destino de SharePoint. Esta propiedad permite personalizar el proceso de paquete mediante la predefinición de las propiedades relacionadas con el empaquetado sin modificar el archivo de destinos de SharePoint enviado, aunque el archivo de destinos se aplica a todos los proyectos de SharePoint.|
|CustomAfterSharePointTargets|Cadena que representa la ruta de acceso de un archivo de destino [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]. Si el archivo de destinos existe y está definido, se importa después de todos los datos de destino de SharePoint. Esta propiedad le permite personalizar el proceso del paquete invalidando los destinos y las propiedades relacionadas con el empaquetado sin tener que modificar el archivo de destinos de SharePoint enviado, pero el archivo de destinos se sigue aplicando a todos los proyectos de SharePoint.|
|LayoutPath|Cadena que representa el directorio raíz en el que cada uno de los archivos que se van a empaquetar se coloca temporalmente antes de agregarse al archivo *. wsp* . Esta ruta de acceso puede ser útil para saber cuándo se invalidan los destinos BeforeLayout y AfterLayout para agregar, quitar o modificar los archivos que se van a empaquetar, ya que se puede usar para modificar el contenido del archivo *. wsp* .|
|BasePackagePath|Cadena que representa la carpeta en la que se coloca el paquete. Este valor usa el directorio de salida del proyecto, como Bin\Debug.|
|PackageExtension|Cadena que representa la extensión de nombre de archivo que se va a anexar al paquete. El valor predeterminado es WSP.|
|AssemblyDeploymentTarget|Cadena que representa la ubicación donde se implementa el ensamblado del proyecto en el servidor de SharePoint. Su valor es GlobalAssemblyCache (el valor predeterminado) o WebApplication. Esta propiedad también se puede establecer en el ventana Propiedades.|
|PackageWithValidation|Valor booleano que especifica si la validación se realiza antes del empaquetado. Esta propiedad le permite omitir los errores de validación durante la compilación de paquetes.|
|ValidatePackageDependsOn|Cadena que define los destinos adicionales que se van a ejecutar antes del destino ValidatePackage.|
|TokenReplacementFileExensions|Cadena que define los archivos que han reemplazado los tokens durante el empaquetado.|

## <a name="use-msbuild-properties-in-the-properties-page"></a>Usar las propiedades de MsBuild en la página Propiedades
 Para mayor flexibilidad, en lugar de usar cadenas codificadas de forma rígida en los cuadros de línea de comandos **anteriores** y **posteriores** a la implementación de la página de propiedades de SharePoint, puede usar las propiedades de SharePoint como argumentos. Por ejemplo, en lugar de especificar una cadena de [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] específica para el sitio de SharePoint, puede utilizar en su lugar `$(SharePointSiteUrl)`.

> [!NOTE]
> Puede usar la sintaxis de la variable [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] `$(`*propertyname*`)` o la sintaxis de la variable de entorno `%`*PropertyName*`%` para especificar una propiedad.

## <a name="see-also"></a>Vea también

- [Referencia de MSBuild](../msbuild/msbuild-reference.md)