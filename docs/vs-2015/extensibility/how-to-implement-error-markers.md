---
title: Procedimiento Implementar los marcadores de Error | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - error markers
ms.assetid: e8e78514-5720-4fc2-aa43-00b6af482e38
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2af9e0765fb5bc73a35bebfc2f50f5d2a41122d3
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435967"
---
# <a name="how-to-implement-error-markers"></a>Procedimiento Implementar los marcadores de Error
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los marcadores de error (o un subrayado ondulado rojo) es los más difíciles de las personalizaciones del editor de texto para implementar. Sin embargo, las ventajas que ofrecen a los usuarios de su VSPackage pueden con creces el costo de proporcionarlas. Los marcadores de error sutilmente marcan el texto que el analizador de lenguaje se considera incorrecto con una línea roja ondulada o línea ondulada de color. Este indicador ayuda a los programadores visualmente mostrando código incorrecto.  
  
 Utilizar marcadores de texto para implementar un subrayado ondulado rojo. Como norma, servicios de lenguaje agregue un subrayado ondulado rojo al búfer de texto como un paso en segundo plano, en tiempo de inactividad o en un subproceso en segundo plano.  
  
### <a name="to-implement-the-red-wavy-underline-feature"></a>Para implementar la característica de la línea ondulada roja  
  
1. Seleccione el texto bajo el cual desea colocar el subrayado ondulado de color rojo.  
  
2. Crear un marcador del tipo `MARKER_CODESENSE_ERROR`. Para obtener más información, vea [Cómo: Agregar marcadores de texto estándar](../extensibility/how-to-add-standard-text-markers.md).  
  
3. Después de eso, pase un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> puntero de interfaz.  
  
   Este proceso también permite crear texto de sugerencia o un menú contextual especial sobre un marcador determinado. Para obtener más información, vea [Cómo: Agregar marcadores de texto estándar](../extensibility/how-to-add-standard-text-markers.md).  
  
   Los objetos siguientes son necesarios antes de que se pueden mostrar marcadores de error.  
  
- Un analizador.  
  
- Un proveedor de tareas (es decir, una implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2>) que mantiene un registro de cambios en la información de línea con el fin de identificar las líneas para volver a analizar.  
  
- Los eventos de cambio de un filtro de vista de texto que captura el símbolo de intercalación de la vista mediante el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents.OnChangeCaretLine%2A>) método.  
  
  El analizador, el proveedor de tareas y el filtro de proporcionan la infraestructura necesaria para que los marcadores de error posibles. Los pasos siguientes proporcionan el proceso para mostrar marcadores de error.  
  
1. En una vista que se está filtrando, el filtro Obtiene un puntero para el proveedor de tareas asociado con los datos de la vista.  
  
    > [!NOTE]
    > Puede usar el mismo filtro de comando para sugerencias de método, finalización de instrucciones, los marcadores de error y así sucesivamente.  
  
2. Cuando el filtro recibe un evento que indica que han movido a la siguiente línea, se crea una tarea para comprobar si hay errores.  
  
3. El controlador de tareas comprueba si la línea está sucio. Si es así, analiza la línea de errores.  
  
4. Si se detectan errores, el proveedor de tareas crea una instancia de elemento de tarea. Esta instancia crea el marcador de texto que usa el entorno como un marcador de error en la vista de texto.  
  
## <a name="see-also"></a>Vea también  
 [Uso de marcadores de texto con la API heredada](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Cómo: Agregar marcadores de texto estándar](../extensibility/how-to-add-standard-text-markers.md)   
 [Cómo: Crear marcadores de texto personalizado](../extensibility/how-to-create-custom-text-markers.md)   
 [Cómo: Usar marcadores de texto](../extensibility/how-to-use-text-markers.md)
