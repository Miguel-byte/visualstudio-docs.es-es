---
title: Especificar controladores de archivo para extensiones de nombre de archivo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0fe2f26a959fc6a185bf244bfa4571846b7991a5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63447188"
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>Especificación de identificadores de archivo para extensiones de nombre de archivo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hay varias maneras de determinar la aplicación que administra un archivo que tiene una extensión de archivo determinada. Los verbos OpenWithList y OpenWithProgids son dos formas de especificar controladores de archivo bajo la entrada del registro de la extensión de archivo.  
  
## <a name="openwithlist-verb"></a>Verbo OpenWithList  
 Cuando hace clic en un archivo en el Explorador de Windows, verá el **abierto** comando. Si más de un producto está asociado con una extensión, verá un **abrir con** submenú.  
  
 Puede registrar aplicaciones diferentes para abrir una extensión mediante el establecimiento de la clave OpenWithList para la extensión de archivo en HKEY_CLASSES_ROOT. Las aplicaciones enumeradas en esta clave para una extensión de archivo aparecen bajo el **programas recomendado** encabezado en el **abrir con** cuadro de diálogo. El ejemplo siguiente muestra las aplicaciones registradas para abrir la extensión de archivo .vcproj.  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithList\  
         devenv.exe  
```  
  
> [!NOTE]
> Son las claves de la especificación de las aplicaciones en la lista HKEY_CLASSES_ROOT\Applications.  
  
 Al agregar una clave OpenWithList, declare que la aplicación admite una extensión de archivo, incluso si otra aplicación toma posesión de la extensión. Podría tratarse de una versión futura de la aplicación u otra aplicación.  
  
## <a name="openwithprogids"></a>OpenWithProgIDs  
 Identificadores programáticos (ProgID) son versiones descriptivas de ClassID que identifica una versión de una aplicación o un objeto COM. Cada objeto compartida que se puede crear debe tener su propio ProgID. Por ejemplo, VisualStudio.DTE.7.1 inicia Visual Studio .NET 2003 mientras se inicia VisualStudio.DTE.10.0 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Como propietario de un tipo de proyecto o el tipo de elemento de proyecto, debe crear un ProgID específico de la versión para la extensión de archivo. Estos ProgID pueden ser redundante en que más de un ProgID puede iniciar la aplicación misma. Para obtener más información, consulte [registrar verbos para extensiones de nombre de archivo](../extensibility/registering-verbs-for-file-name-extensions.md).  
  
 Use la siguiente convención de nomenclatura para archivos con control de versiones ProgID para evitar la duplicación con el registro de otros proveedores:  
  
|Extensión de archivo|Con control de versiones ProgID|  
|--------------------|----------------------|  
|transferidas|ProductName. extension.versionMajor.versionMinor|  
  
 Puede registrar las aplicaciones diferentes que pueden abrir una extensión de archivo determinada mediante la adición de ProgID con control de versiones como valores a HKEY_CLASSES_ROOT\\*\<extensión >* \OpenWithProgids clave. Esta clave del registro contiene una lista de alternativas ProgID asociados con la extensión de archivo. Las aplicaciones asociadas con el ProgID de la lista aparecen en el **abrir con**_Product Name_ submenú. Si se especifica la misma aplicación tanto en el `OpenWithList` y `OpenWithProgids` claves, el sistema operativo combina los duplicados.  
  
> [!NOTE]
> El `OpenWithProgids` clave solo se admite en Windows XP. Dado que otros sistemas operativos de pasar por alto esta clave, no usarlo como el registro solo para los controladores de archivo. Use esta clave para ofrecer una mejor experiencia de usuario en Windows XP.  
  
 Agregue los ProgID deseados como valores del tipo REG_NONE. El código siguiente proporciona un ejemplo de registro ProgID para una extensión de archivo (. *ext*).  
  
```  
HKEY_CLASSES_ROOT\  
   .ext\  
      (default)="MyProduct.ext.14.0"  
      OpenWithProgids  
         progid        REG_NONE (zero-length binary value)  
         otherprogid   REG_NONE (zero-length binary value)  
```  
  
 El ProgID especificado como el valor predeterminado para la extensión de archivo es el controlador de archivo predeterminado. Si modifica el ProgID de una extensión de archivo que se incluye con una versión anterior de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] o que pueda hacerse cargo de otras aplicaciones, a continuación, debe registrar el `OpenWithProgids` la clave para la extensión de archivo y especificar el nuevo ProgID de la lista junto con el ProgID antiguos que admiten. Por ejemplo:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithProgids  
         vcprojfile              //old progid  
         VisualStudio.vcproj.12.0 //old progid  
         VisualStudio.vcproj.14.0 //new progid  
```  
  
 Si la antigua ProgID tiene verbos asociados con él y, después, estos verbos también aparecerá bajo **abrir con** *Product Name* en el menú contextual.  
  
## <a name="see-also"></a>Vea también  
 [Acerca de las extensiones de nombre de archivo](../extensibility/about-file-name-extensions.md)   
 [Registro de verbos para extensiones de nombre de archivo](../extensibility/registering-verbs-for-file-name-extensions.md)
