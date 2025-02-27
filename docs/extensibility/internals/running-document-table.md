---
title: Tabla de documentos en ejecución | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4645899e8c4cd73758316a3c2a8d74ccb169aa2d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724068"
---
# <a name="running-document-table"></a>Tabla de documentos en ejecución
El IDE mantiene la lista de todos los documentos abiertos actualmente en una estructura interna denominada tabla de documentos en ejecución (RDT). Esta lista incluye todos los documentos abiertos en la memoria, independientemente de si estos documentos se están editando en ese momento. Un documento es cualquier elemento que se conserva, incluidos los archivos de un proyecto o el archivo del proyecto principal (por ejemplo, un archivo. vcxproj).

## <a name="elements-of-the-running-document-table"></a>Elementos de la tabla de documentos en ejecución
 La tabla de documentos en ejecución contiene las siguientes entradas.

|Elemento|Descripción|
|-------------|-----------------|
|Moniker de documento|Cadena que identifica de forma única el objeto de datos del documento. Esta sería la ruta de acceso absoluta del archivo para un sistema de proyectos que administra archivos (por ejemplo, C:\MyProject\MyFile). Esta cadena también se utiliza para los proyectos guardados en almacenes que no son sistemas de archivos, como los procedimientos almacenados en una base de datos de. En este caso, el sistema del proyecto puede inventar una cadena única que pueda reconocer y posiblemente analizar para determinar cómo almacenar el documento.|
|Propietario de la jerarquía|Objeto de jerarquía que posee el documento, tal y como se representa mediante una interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>.|
|IDENTIFICADOR de elemento|Identificador de elemento para un elemento específico dentro de la jerarquía. Este valor es único entre todos los documentos de la jerarquía que posee este documento, pero no se garantiza que este valor sea único en las distintas jerarquías.|
|Objeto de datos de documento|Como mínimo, se trata de una `IUnknown`<br /><br /> objeto. El IDE no requiere ninguna interfaz determinada más allá de la interfaz `IUnknown` para un objeto de datos de documento del editor personalizado. Sin embargo, para un editor estándar, la implementación del editor de la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> es necesaria para controlar las llamadas de persistencia de archivos del proyecto. Para obtener más información, vea [guardar un documento estándar](../../extensibility/internals/saving-a-standard-document.md).|
|Marcas|Marcas que controlan si se guarda el documento, si se aplica un bloqueo de lectura o edición, etc., se puede especificar cuando se agregan entradas a RDT. Para obtener más información, vea la enumeración <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.|
|Editar número de bloqueos|Recuento de bloqueos de edición. Un bloqueo de edición indica que algún editor tiene abierto el documento para su edición. Cuando el recuento de bloqueos de edición cambia a cero, se pide al usuario que guarde el documento, si se ha modificado. Por ejemplo, cada vez que se abre un documento en un editor mediante el comando **nueva ventana** , se agrega un bloqueo de edición para ese documento en el RDT. Para que se establezca un bloqueo de edición, el documento debe tener una jerarquía o un identificador de elemento.|
|Recuento de bloqueos de lectura|Recuento de bloqueos de lectura. Un bloqueo de lectura indica que el documento se está leyendo a través de algún mecanismo, como un asistente. Un bloqueo de lectura contiene un documento activo en RDT, mientras que indica que el documento no se puede editar. Puede establecer un bloqueo de lectura incluso si el documento no tiene una jerarquía o un identificador de elemento. Esta característica permite abrir un documento en la memoria y escribirlo en el RDT sin que el documento sea propiedad de ninguna jerarquía. Esta característica rara vez se usa.|
|Marcador de bloqueo|Instancia de una interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>. El titular del bloqueo se implementa mediante características como asistentes que abren y editan documentos fuera de un editor. Un marcador de bloqueo permite a la característica agregar un bloqueo de edición al documento para evitar que el documento se cierre mientras todavía se está editando. Normalmente, los bloqueos de edición solo se agregan mediante ventanas de documento (es decir, editores).|

 Cada entrada de RDT tiene un identificador de elemento o jerarquía único asociado a él, que generalmente corresponde a un nodo del proyecto. Todos los documentos disponibles para editar suelen pertenecer a una jerarquía. Las entradas realizadas en el RDT controlan qué proyecto, o bien, de forma más precisa, qué jerarquía posee actualmente el objeto de datos del documento que se está editando. Con la información de RDT, el IDE puede evitar que un documento se abra en más de un proyecto a la vez.

 La jerarquía también controla la persistencia de los datos y usa la información de RDT para actualizar los cuadros de diálogo **Guardar** y **Guardar como** . Cuando los usuarios modifican un documento y, a continuación, eligen el comando **salir** en el menú **archivo** , el IDE los solicita con el cuadro de diálogo **Guardar cambios** para mostrar todos los proyectos y elementos de proyecto que se han modificado actualmente. Esto permite a los usuarios elegir qué documentos se van a guardar. La lista de documentos que se van a guardar (es decir, los documentos que tienen cambios) se genera a partir de RDT. Los elementos que espera ver en el cuadro de diálogo **Guardar cambios** al salir de la aplicación deben tener registros en RDT. RDT coordina qué documentos se guardan y si se solicita al usuario una operación de guardar usando los valores especificados en la entrada Flags para cada documento. Para obtener más información sobre las marcas RDT, vea la enumeración <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.

## <a name="edit-locks-and-read-locks"></a>Editar bloqueos y leer bloqueos
 Edite los bloqueos y los bloqueos de lectura que se encuentran en RDT. La ventana de documento aumenta y disminuye el bloqueo de edición. Por lo tanto, cuando un usuario abre una nueva ventana de documento, el número de bloqueos de edición se incrementa en uno. Cuando el número de bloqueos de edición llega a cero, la jerarquía se señaliza para conservar o guardar los datos del documento asociado. A continuación, la jerarquía puede conservar los datos de cualquier manera, incluso guardarlos como un archivo o como un elemento de un repositorio. Puede usar el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> de la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> para agregar bloqueos de edición y bloqueos de lectura, y el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> para quitar estos bloqueos.

 Normalmente, cuando se crea una instancia de la ventana de documento para un editor, el marco de ventana agrega automáticamente un bloqueo de edición para el documento en el RDT. Sin embargo, si crea una vista personalizada de un documento que no utiliza una ventana de documento estándar (es decir, no implementa la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>), deberá establecer su propio bloqueo de edición. Por ejemplo, en un asistente, se edita un documento sin abrirlo en un editor. Para que los bloqueos de documento estén abiertos por asistentes y entidades similares, estas entidades deben implementar la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>. Para registrar el marcador de bloqueo del documento, llame al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> y pase la implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>. Al hacerlo, se agrega el titular del bloqueo del documento a RDT. Otro escenario para implementar un marcador de bloqueo de documento es si abre un documento a través de una ventana de herramientas especial. En esta instancia, no puede hacer que la ventana de herramientas cierre el documento. Sin embargo, al registrarse como marcador de bloqueo de documento en el RDT, el IDE puede llamar a su implementación del método <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> para solicitar un cierre del documento.

## <a name="other-uses-of-the-running-document-table"></a>Otros usos de la tabla de documentos en ejecución
 Otras entidades del IDE usan RDT para obtener información sobre los documentos. Por ejemplo, el administrador de control de código fuente usa RDT para indicar al sistema que vuelva a cargar un documento en el editor, después de obtener la versión más reciente del archivo. Para ello, el administrador de control de código fuente busca los archivos en RDT para ver si alguno de ellos está abierto. Si es así, el administrador de control de código fuente comprueba primero que la jerarquía implemente el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>. Si el proyecto no implementa el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>, el administrador de control de código fuente comprueba directamente si hay una implementación del método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> en el objeto de datos del documento.

 El IDE también usa RDT para resurface (traer al frente) un documento abierto, si un usuario solicita dicho documento. Para obtener más información, vea [Mostrar archivos mediante el comando Abrir archivo](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Para determinar si un archivo está abierto en RDT, realice una de las siguientes acciones.

- Consulte el moniker del documento (es decir, la ruta de acceso completa del documento) para averiguar si el elemento está abierto.

- Use la jerarquía o el identificador de elemento para solicitar al sistema del proyecto la ruta de acceso completa del documento y, a continuación, busque el elemento en el RDT.

## <a name="see-also"></a>Vea también
- [Uso de RDT_ReadLock](../../extensibility/internals/rdt-readlock-usage.md)
- [Persistencia y tabla de documentos en ejecución](../../extensibility/internals/persistence-and-the-running-document-table.md)