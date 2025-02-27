---
title: Guardar un documento personalizado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf67335b6a12b966eb148b3f8dcaf16339e2a29f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724086"
---
# <a name="saving-a-custom-document"></a>Guardado de un documento personalizado
El entorno controla los comandos **Guardar**, **Guardar como**y **guardar todo** . Cuando un usuario hace clic en **Guardar**, **Guardar como** **o guardar todo** en el menú **archivo** o cierra la solución, lo que da lugar a guardar todo, se produce el siguiente proceso.

 ![Guardado del editor del cliente](../../extensibility/internals/media/private.gif "Private") Guardar, guardar como y guardar todo el control de comandos para un editor personalizado

 Este proceso se describe en los pasos siguientes:

1. En el caso de los comandos **Guardar** y **Guardar como** , el entorno utiliza el servicio de <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> para determinar la ventana de documento activa y, por tanto, los elementos que se deben guardar. Una vez que se conoce la ventana de documento activa, el entorno busca el puntero de la jerarquía y el identificador de elemento (itemID) del documento en la tabla de documentos en ejecución. Para obtener más información, vea [ejecutar la tabla de documentos](../../extensibility/internals/running-document-table.md).

     En el caso del comando guardar todo, el entorno usa la información de la tabla de documentos en ejecución para compilar la lista de todos los elementos que se van a guardar.

2. Cuando la solución recibe una llamada <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>, recorre en iteración el conjunto de elementos seleccionados (es decir, las selecciones múltiples expuestas por el servicio <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>).

3. En cada elemento de la selección, la solución usa el puntero de jerarquía para llamar al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> para determinar si el comando de menú guardar debe estar habilitado. Si se han modificado uno o más elementos, el comando Guardar está habilitado. Si la jerarquía usa un editor estándar, la jerarquía delega la consulta del estado sucio en el editor llamando al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A>.

4. En cada elemento seleccionado que está sucio, la solución usa el puntero de la jerarquía para llamar al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> en las jerarquías adecuadas.

     En el caso de un editor personalizado, la comunicación entre el objeto de datos del documento y el proyecto es privada. Por lo tanto, los problemas de persistencia especiales se controlan entre estos dos objetos.

    > [!NOTE]
    > Si implementa su propia persistencia, asegúrese de llamar al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> para ahorrar tiempo. Este método realiza una comprobación para asegurarse de que es seguro guardar el archivo (por ejemplo, el archivo no es de solo lectura).

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Apertura y guardado de elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md)