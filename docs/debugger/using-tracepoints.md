---
title: Información de registro con puntos de seguimiento | Microsoft Docs
ms.date: 10/28/2019
ms.topic: conceptual
helpviewer_keywords:
- tracepoints, about tracepoints
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: fcc9f01315d3783af1a1f124785cd74fafb215bf
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2019
ms.locfileid: "73187301"
---
# <a name="log-info-to-the-output-window-using-tracepoints-in-visual-studio"></a>Información de registro en la ventana de salida con puntos de seguimiento en Visual Studio

Los puntos de seguimiento le permiten registrar información en la ventana de salida en condiciones configurables sin modificar o detener el código. Esta característica es compatible con los lenguajes administrados (C#, F#Visual Basic,) y con el código nativo, así como con lenguajes como JavaScript y Python.

## <a name="let39s-take-an-example"></a>Dejar&#39;un ejemplo

El programa de ejemplo siguiente es un bucle de `for` simple con una variable de contador que se incrementa en uno cada vez que el bucle ejecuta otra iteración.

![Ejemplo de contador](../debugger/media/counterexample.png "Ejemplo de contador")

## <a name="set-tracepoints-in-source-code"></a>Establecer puntos de seguimiento en código fuente

Puede establecer los puntos de seguimiento mediante la especificación de una cadena de salida en la casilla **acción** de la ventana **configuración del punto de interrupción** .

1. Para inicializar un punto de seguimiento, primero haga clic en el medianil a la izquierda del número de línea en el que desea establecer el punto de seguimiento.

   ![Inicialización de puntos de interrupción](../debugger/media/breakpointinitialization.png "Inicialización de puntos de interrupción")

2. Mantenga el mouse sobre el círculo rojo y, a continuación, haga clic en el icono de engranaje.
3. Se abrirá la ventana **configuración del punto de interrupción** .

   ![Ventana punto de interrupción](../debugger/media/breakpointwindow.png "Ventana punto de interrupción")

4. Active la casilla **acción** .

   ![Cuadro acciones seleccionadas](../debugger/media/checkedactionsbox.png "Cuadro acciones seleccionadas")

   Observe cómo cambia el círculo rojo a un rombo que indica que ha cambiado de un punto de interrupción a un punto de seguimiento.

5. Escriba el mensaje que desea iniciar sesión en el cuadro de texto **Mostrar un mensaje en el ventana de salida** (para más información, consulte las secciones posteriores de este artículo).

   Ya se ha establecido el punto de seguimiento. Presione el botón &quot; de &quot;Close si todo lo que desea hacer es registrar cierta información en el Ventana de salida.

6. Si desea agregar las condiciones que determinan si se muestra el mensaje, active la casilla **condiciones** .

   ![Cuadro condiciones comprobadas](../debugger/media/checkedconditionsbox.png "Cuadro condiciones comprobadas")

   Tiene tres opciones para las condiciones: **expresión condicional**, **filtro**y **número de llamadas**.

## <a name="actions-menu"></a>Menú acciones

Este menú le permite registrar un mensaje en la ventana de salida. Escriba las cadenas que desea mostrar en el cuadro de mensaje (no se necesitan comillas). Si desea mostrar los valores de las variables, asegúrese de encerrarlo entre llaves.

Por ejemplo, si desea mostrar el valor de la variable `counter` en la consola de salida, escriba {Counter} en el cuadro de texto del mensaje.

![Mensaje de salida del contador](../debugger/media/counteroutputmessage.png "Mensaje de salida del contador")

Si hace clic en **cerrar** y, a continuación, depura el programa (**F5**), verá el siguiente resultado en la ventana salida.

![Mensaje de acciones en Ventana de salida](../debugger/media/actionsmessageinoutputwindow.png "Mensaje de acciones en Ventana de salida")

También puede usar palabras clave especiales para mostrar información más específica. Escriba la palabra clave exactamente como se muestra a continuación (use un "$" delante de cada palabra clave y todos los extremos de la palabra clave en sí).

| Palabra clave | Qué se muestra |
| --- | --- |
| $ADDRESS | Instrucción actual |
| $CALLER | Nombre de la función de llamada |
| $CALLSTACK | Pila de llamadas |
| $FUNCTION | Nombre de la función actual |
| $PID | Id. de proceso |
| $PNAME | Nombre del proceso |
| $TID | Id. de subproceso |
| $TNAME   | Nombre del subproceso |
| $TICK | Recuento de pasos (de Windows GetTickCount) |

## <a name="conditions-menu"></a>Menú condiciones

Las condiciones permiten filtrar los mensajes de salida, por lo que solo se muestran en determinados escenarios. Hay tres tipos principales de condiciones disponibles.

### <a name="conditional-expression"></a>Expresión condicional
En el caso de una expresión condicional, se muestra un mensaje de salida solo cuando se cumplen ciertas condiciones.

En el caso de las expresiones condicionales, puede establecer el punto de seguimiento para que genere un mensaje cuando una condición determinada sea verdadera o cuando haya cambiado. Por ejemplo, si solo desea mostrar el valor del contador durante las iteraciones incluso del bucle `for`, puede seleccionar la opción **es true** y, a continuación, escribir `i%2 == 0` en el cuadro de texto mensaje.

![La expresión condicional es true](../debugger/media/conditionalexpressionistrue.png "La expresión condicional es true")

Si desea imprimir el valor del contador cuando cambie la iteración del bucle `for`, seleccione la opción **al cambiar** y escriba `i` en el cuadro de texto mensaje.

![Expresión condicional cuando se cambia](../debugger/media/conditionalexpressionwhenchanged.png "Expresión condicional cuando se cambia")

El comportamiento de la opción **When Changed** es diferente para los diferentes lenguajes de programación.

- En el caso de código nativo, el depurador no considera la primera evaluación de la condición como un cambio, por lo que no alcanza el punto de seguimiento en la primera evaluación.
- En el caso de código administrado, el depurador alcanza el punto de seguimiento en la primera evaluación después de seleccionar **cuando se cambia** .

Para obtener una visión más completa de las expresiones válidas que se pueden usar mientras se establecen las condiciones, vea [expresiones en el depurador](expressions-in-the-debugger.md).

### <a name="hit-count"></a>Número de llamadas
Una condición de número de llamadas permite enviar la salida solo después de que la línea de código donde se establece el punto de seguimiento se haya ejecutado un número especificado de veces.

En el caso del número de llamadas, puede elegir que se genere un mensaje cuando la línea de código donde se establece el punto de seguimiento haya ejecutado un número de veces igual a, sea un múltiplo de o sea mayor o igual que el valor de número de llamadas especificado. Elija la opción que mejor se adapte a sus necesidades y escriba un valor entero en el campo (por ejemplo, 5) que represente la iteración de interés.

![Número de llamadas de expresiones condicionales](../debugger/media/conditionalexpressionhitcount.png "Número de llamadas de expresiones condicionales")

### <a name="filter"></a>Filtro
Para una condición de filtro, especifique en qué dispositivos, procesos o subprocesos se muestra la salida.

![Filtro de expresión condicional](../debugger/media/conditionalexpressionfilter.png "Filtro de expresión condicional")

Lista de expresiones de filtro:

- MachineName = "name"
- ProcessId = value
- ProcessName = "name"
- ThreadId = value
- ThreadName = "name"

Incluya las cadenas (como nombres) entre comillas dobles. Los valores se pueden escribir sin comillas. Puede combinar cláusulas mediante `&` (`AND`), `||` (`OR`), `!` (`NOT`) y paréntesis.

## <a name="considerations"></a>Consideraciones

Aunque los puntos de seguimiento están diseñados para que la depuración sea una experiencia más limpia y más fluida, hay algunas consideraciones que debe tener en cuenta cuando se trata de usarlas.

A veces, al inspeccionar una propiedad o atributo de un objeto, su valor puede cambiar. Si el valor cambia durante la inspección, no es un error causado por la propia característica de punto de seguimiento. Sin embargo, el uso de puntos de seguimiento para inspeccionar objetos no evita estas modificaciones accidentales.

La forma en que se evalúan las expresiones en el cuadro de mensaje de **acción** puede ser diferente del lenguaje que se usa actualmente para el desarrollo. Por ejemplo, para generar una cadena, no es necesario ajustar un mensaje entre comillas, aunque normalmente se use `Debug.WriteLine()` o `console.log()`. Además, la sintaxis de la llave (`{ }`) en las expresiones de salida también puede ser diferente de la Convención para generar valores en el lenguaje de desarrollo. (Sin embargo, el contenido dentro de las llaves (`{ }`) todavía se debe escribir con la sintaxis del lenguaje de desarrollo.

Si intenta depurar una aplicación activa y busca una característica similar, consulte nuestra característica punto en el Snapshot Debugger. Snapshot Debugger es una herramienta que se usa para investigar problemas en aplicaciones de producción. Puntos también permiten enviar mensajes al Ventana de salida sin tener que modificar el código fuente ni afectar a la aplicación en ejecución. Para obtener más información, consulte [depuración de aplicaciones de Azure en directo](../debugger/debug-live-azure-applications.md).

## <a name="see-also"></a>Vea también

- [¿Qué es la depuración?](../debugger/what-is-debugging.md)
- [Escriba mejor C# código mediante Visual Studio](../debugger/write-better-code-with-visual-studio.md)
- [Primer vistazo a la depuración](../debugger/debugger-feature-tour.md)
- [Expresiones en el depurador](expressions-in-the-debugger.md)
- [Uso de puntos de interrupción](../debugger/using-breakpoints.md)
- [Depuración de aplicaciones de Azure activas](../debugger/debug-live-azure-applications.md)
