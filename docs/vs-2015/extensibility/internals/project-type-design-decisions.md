---
title: Las decisiones de diseño de tipo de proyecto | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cd26e08ab153e96fc601e89788008cb0e9ca38c8
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704076"
---
# <a name="project-type-design-decisions"></a>Decisiones de diseño del tipo de proyecto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Antes de crear un nuevo tipo de proyecto, debe realizar varias decisiones de diseño con respecto a su tipo de proyecto. Debe decidir qué tipos de elementos que se va a contener los proyectos, cómo se conservarán los archivos de proyecto y qué modelo de compromiso va a usar.  
  
## <a name="project-items"></a>Elementos de proyecto  
 ¿Usará el proyecto archivos u objetos abstractos? ¿Si utiliza archivos, serán archivos basado en el directorio o referencia? ¿Son los archivos o los objetos abstractos que va a ser local o remoto?  
  
 Los elementos de un proyecto pueden ser archivos, o pueden ser objetos más abstractos como los objetos de una base de datos repositorio o conexiones de datos a través de Internet. Si los elementos son archivos, puede ser el proyecto basado en una referencia o un proyecto basado en el directorio.  
  
 En los proyectos basados en referencias, elementos pueden aparecer en más de un proyecto. Sin embargo, el archivo real que representa un elemento se encuentra en un solo directorio. En proyectos basados en el directorio, todos los elementos de proyecto existen en la estructura de directorios. Para obtener más información, consulte [NIB: administración elementos en proyectos](https://msdn.microsoft.com/762e606b-7f44-4b66-97a1-e30a703654a0).  
  
 Los elementos locales se almacenan en el mismo equipo donde está instalada la aplicación. Elementos remotos pueden almacenarse en un servidor independiente en una red local o en otro lugar en Internet.  
  
## <a name="project-file-persistence"></a>Persistencia de archivo de proyecto  
 ¿Datos se almacenarán en sistemas de archivos planos comunes o en almacenamiento estructurado? ¿Se abrirá los archivos mediante un editor estándar o un editor específico del proyecto?  
  
 Para conservar sus datos, la mayoría de las aplicaciones guardan sus datos en un archivo y leerlo cuando un usuario debe revisar o cambiar la información.  
  
 Almacenamiento estructurado, denominado también archivos compuestos, normalmente se usa cuando varios objetos de modelo de objetos componentes (COM) necesitan almacenar los datos persistentes en un único archivo. Con el almacenamiento estructurado, varios componentes de software diferentes pueden compartir un único archivo de disco.  
  
 Tiene varias opciones para considerar con respecto a la persistencia para los elementos en el proyecto. Puede realizar cualquiera de las siguientes opciones:  
  
- Guarde cada archivo individualmente cuando se ha cambiado.  
  
- Capturar muchas transacciones en un único **guardar** operación.  
  
- Guardar archivos localmente y, a continuación, publicar en un servidor o usar otro método para guardar elementos de proyecto cuando el elemento representa una conexión de datos a un objeto remoto.  
  
  Para obtener más información acerca de la persistencia, consulte [persistencia de un proyecto](../../extensibility/internals/project-persistence.md) y [abriendo y guardando elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="project-commitment-model"></a>Modelo de compromiso de proyectos  
 ¿Se abrirán los objetos de datos persistentes en modo directo o en modo de transacción?  
  
 Cuando se abren los objetos de datos en modo directo, se incorporan los cambios realizados a los datos inmediatamente o cuando el usuario guarda manualmente el archivo.  
  
 Cuando los objetos de datos se abren mediante el modo de transacción, los cambios se guardan en una ubicación temporal en memoria y no se confirman hasta que el usuario decide guardar el archivo manualmente. En ese momento, todos los cambios deben producirse entre sí o no se realizará ningún cambio.  
  
## <a name="see-also"></a>Vea también  
 [Lista de comprobación: Creación de nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [NIB: administración elementos en proyectos](https://msdn.microsoft.com/762e606b-7f44-4b66-97a1-e30a703654a0)   
 [Abrir y guardar elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Persistencia de un proyecto](../../extensibility/internals/project-persistence.md)   
 [Elementos de un modelo de proyecto](../../extensibility/internals/elements-of-a-project-model.md)   
 [Componentes principales de modelo de proyecto](../../extensibility/internals/project-model-core-components.md)   
 [Creación de tipos de proyecto](../../extensibility/internals/creating-project-types.md)
