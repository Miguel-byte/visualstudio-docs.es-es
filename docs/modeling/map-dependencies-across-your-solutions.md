---
title: Mapas de código
ms.date: 05/16/2018
ms.topic: conceptual
f1_keywords:
- vs.progression.codemap
- vs.progression.standardgraphsdialog
helpviewer_keywords:
- DGML
- graph documents
- code visualization [Visual Studio]
- dependencies, visualizing
- dependency graphs
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 45fb9b1a08dc54257f24f469d3a717b82faccf45
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661542"
---
# <a name="map-dependencies-with-code-maps"></a>Asignación de dependencias con mapas de código

Puede visualizar las dependencias en el código mediante la creación de un mapa de código. Los mapas de código ayudan a ver cómo encaja el código sin necesidad de leer archivos y líneas de código.

![Ver las dependencias con mapas de código en Visual Studio](../modeling/media/codemapsmainintro.png)

Para crear y editar mapas de código, necesita Visual Studio Enterprise Edition. En las ediciones Community y Professional de Visual Studio, puede abrir los diagramas que se generaron en Enterprise Edition, pero no puede editarlos.

> [!NOTE]
> Antes de compartir las asignaciones creadas en Visual Studio Enterprise con otras personas que usan Visual Studio Professional, asegúrese de que todos los elementos del mapa (como los elementos ocultos, los grupos expandidos y los vínculos entre grupos) estén visibles.

Puede asignar dependencias para el código en estos lenguajes:

- Visual C# o Visual Basic en una solución o ensamblados ( *. dll* o *. exe*)

- Código C o C++ nativo o administrado en proyectos C++ visuales, archivos de encabezado ( *. h* o `#include`) o binarios

- Proyectos y ensamblados de X++ creados desde módulos de .NET para Microsoft Dynamics AX

> [!NOTE]
> En el caso de C# los proyectos que no sean o Visual Basic, hay menos opciones para iniciar un mapa de código o agregar elementos a un mapa de código existente. Por ejemplo, no podrá hacer clic con el botón secundario en un objeto en el editor de texto de un proyecto de C++ y agregarlo a un mapa de código. Sin embargo, puede arrastrar y colocar elementos de código individuales o archivos de **Explorador de soluciones**, **vista de clases**y **Examinador de objetos**.

## <a name="install-code-map-and-live-dependency-validation"></a>Instalación del mapa de código y la validación de dependencias dinámicas

Para crear un mapa de código en Visual Studio, primero Instale los componentes **mapa de código** y **validación de dependencias dinámicas** :

1. Abra **instalador de Visual Studio**. Puede abrirlo desde el menú Inicio de Windows o en Visual Studio seleccionando **herramientas**  > **obtener herramientas y características**.

1. Seleccione la pestaña **Componentes individuales**.

1. Desplácese hacia abajo hasta la sección **herramientas de código** y seleccione **mapa de código** y **validación de dependencias en vivo**.

   ![Componentes del mapa de código y de la validación de dependencias dinámicas en Instalador de Visual Studio](media/modeling-components.png)

1. Seleccione **Modificar**.

   El **mapa de código** y los componentes de **validación de dependencias en directo** comienzan a instalar. Es posible que se le pida que cierre Visual Studio.

## <a name="add-a-code-map"></a>Agregar un mapa de código

Puede crear un mapa de código vacío y arrastrar los elementos a él, incluidas las referencias de ensamblado, los archivos y las carpetas, o puede generar un mapa de código para todo o parte de la solución.

Para agregar un mapa de código vacío:

1. En el **Explorador de soluciones**, abra el menú contextual del nodo de la solución de nivel superior. Elija **agregar**  > **nuevo elemento**.

2. En el cuadro de diálogo **Agregar nuevo elemento** , en **instalado**, elija la categoría **General** .

3. Elija la plantilla **documento de gráfico dirigido (. DGML)** y, después, seleccione **Agregar**.

   > [!TIP]
   > Es posible que esta plantilla no aparezca alfabéticamente, por tanto, desplácese hacia abajo hasta la parte inferior de la lista de plantillas si no la ve.

   En la carpeta **elementos** de la solución de la solución aparece un mapa en blanco.

Del mismo modo, puede crear un nuevo archivo de mapa de código sin agregarlo a la solución seleccionando **arquitectura**  > **nuevo mapa de código** o **archivo**  > **nuevo** **archivo**de  > .

## <a name="generate-a-code-map-for-your-solution"></a>Generar un mapa de código para la solución

Para ver todas las dependencias de la solución:

1. En la barra de menús, elija **arquitectura**  > **generar mapa de código para la solución**. Si el código no ha cambiado desde la última vez que lo compiló, puede seleccionar **arquitectura**  > **generar mapa de código para la solución sin generar** en su lugar.

   ![Generar un comando de mapa de código](../modeling/media/codemapsarchitecturemenu.png)

   Se genera un mapa que muestra los ensamblados de nivel superior y los vínculos agregados entre ellos. Cuanto más amplio sea el vínculo agregado, más dependencias representará.

2. Use el botón **Leyenda** situado en la barra de herramientas del mapa de código para mostrar u ocultar la lista de iconos de tipo de proyecto (por ejemplo, proyectos de prueba, web y teléfono), los elementos de código (por ejemplo, clases, métodos y propiedades) y los tipos de relación (por ejemplo, “Se hereda de”, “Implementa” y “Llama a”).

   ![Gráfico de dependencias de ensamblados de nivel superior](../modeling/media/dependencygraph_toplevelassemblies.png)

   Esta solución de ejemplo contiene carpetas de solución (**Pruebas** y **Componentes**), proyectos de prueba, proyectos web y ensamblados. De forma predeterminada, todas las relaciones de contención aparecen como *grupos*que se pueden expandir y contraer. El grupo **Externos** contiene cualquier elemento que esté fuera de la solución, incluidas las dependencias de plataforma. En los ensamblados externos solo se muestran los elementos que están en uso. De forma predeterminada, los tipos base del sistema están ocultos en el mapa para reducir la acumulación de elementos.

3. Para profundizar en el mapa, expanda los grupos que representan proyectos y ensamblados. Puede expandir todo si presiona **CTRL+A** para seleccionar todos los nodos y, después, elige **Grupo**, **Expandir** en el menú contextual.

   ![Expandiendo todos los grupos de un mapa de código](../modeling/media/codemapsexpandallgroups.png)

4. No obstante, puede que esto no resulte útil en el caso de soluciones grandes. De hecho, con soluciones complejas, las limitaciones de memoria pueden impedirle expandir todos los grupos. En su lugar, expanda un nodo individual para explorarlo. Mueva el puntero del mouse sobre el nodo y luego haga clic en el botón de contenido adicional (flecha hacia abajo) cuando aparezca.

   ![Expandir un nodo en un mapa de código](../modeling/media/dependencygraph_containment.png)

   También puede usar el teclado: seleccione el elemento y luego presione la tecla más ( **+** ). Para explorar niveles de código más profundos, haga lo mismo para los espacios de nombres, los tipos y los miembros.

   > [!TIP]
   > Para obtener más información sobre cómo trabajar con mapas de código mediante el mouse, el teclado y el toque, vea [examinar y reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md).

5. Para simplificar el mapa y centrarse en partes individuales, elija **Filtros** en la barra de herramientas del mapa de código y seleccione únicamente los tipos de nodos y los vínculos que le interesan. Por ejemplo, puede ocultar todos los contenedores de la carpeta de soluciones y los ensamblados.

   ![Simplificar el mapa mediante el filtrado de contenedores](../modeling/media/codemapsfilterfoldersassemblies.png)

   Otra manera de simplificar el mapa es ocultar o quitar grupos y elementos individuales, sin que ello afecte al código subyacente de la solución.

6. Para ver las relaciones entre los elementos, selecciónelos en el mapa. Los colores de los vínculos indican los tipos de relación, tal como se muestra en el panel **Leyenda** .

   ![Ver dependencias en las soluciones](../modeling/media/codemapsmainintro.png)

   En este ejemplo, los vínculos de color púrpura son llamadas, los vínculos con puntos son referencias y los vínculos de color azul claro son acceso a campos. Los vínculos verdes pueden ser herencia o pueden ser *vínculos agregados* que indican más de un tipo de relación (o *categoría*).

   > [!TIP]
   > Si ve un vínculo verde, podría no significar únicamente que hay una relación de herencia. También puede haber llamadas de método, ocultas por la relación de herencia. Para ver tipos específicos de vínculos, use las casillas del panel **filtros** para ocultar los tipos que no le interesan.

7. Para más información sobre un elemento o vínculo, mueva el puntero por encima hasta que aparezca información. De este modo se mostrarán los detalles de un elemento de código o las categorías que representa un vínculo.

   ![Mostrar las categorías de una relación](../modeling/media/codemapsshowlinkcatgories.png)

8. Para examinar los elementos y las dependencias representados por un vínculo agregado, primero seleccione el vínculo y luego abra su menú contextual. Elija **Mostrar vínculos de contribución** (o **Mostrar vínculos de contribución en el nuevo mapa de código**). De este modo se expanden los grupos en ambos extremos del vínculo y se muestran solo los elementos y dependencias que participan en el vínculo.

9. Para centrarse en partes específicas del mapa, puede continuar quitando los elementos que no le interesan. Por ejemplo, para ver los detalles en la vista de clases y miembros, simplemente filtre todos los nodos de espacios de nombres en el panel **Filtros** .

   ![Examinar con detalle los niveles de clase y de miembro](../modeling/media/dependencygraph_expandedselectedgroups_2012.png)

10. Otra manera de centrarse en un mapa de solución compleja consiste en generar un mapa nuevo que contenga los elementos seleccionados en un mapa existente. Mantenga presionada la **tecla Ctrl** mientras selecciona los elementos en los que desea centrarse, abra el menú contextual y elija **nuevo gráfico a partir de selección**.

    ![Mostrar los elementos seleccionados en un nuevo mapa de código](../modeling/media/codemapsshowonnewmap.png)

11. El contexto contenedor se traslada al nuevo mapa. Oculte las carpetas de soluciones y cualquier otro contenedor que no desee ver mediante el panel **filtros** .

    ![Filtrar los contenedores para simplificar la vista](../modeling/media/codemapsexpandnewgroups.png)

12. Expanda los grupos y seleccione elementos en el mapa para ver las relaciones.

    ![Seleccionar elementos para ver sus relaciones](../modeling/media/codemapsviewnewrelationships.png)

Vea también:

- [Examinar y reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md)
- [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- Buscar posibles problemas en el código mediante la [ejecución de un analizador](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="view-specific-dependencies-in-a-code-map"></a>Ver dependencias concretas en un mapa de código

Supongamos que tiene una revisión de código para realizar en algunos archivos con cambios pendientes. Para ver las dependencias que hay en esos cambios, cree un mapa de código a partir de dichos archivos.

   ![Mostrar las dependencias específicas en un mapa de código](../modeling/media/codemapsspecificdependenciesintro.png)

1. En **Explorador de soluciones**, seleccione los proyectos, las referencias de ensamblado, las carpetas, los archivos, los tipos o los miembros que desee asignar.

   ![Seleccionar los elementos que se van a incluir en el mapa](../modeling/media/codemapsselectinsolutionexplorer.png)

1. En la barra de herramientas **Explorador de soluciones** , elija el botón **Mostrar en mapa de código** ![Create nuevo gráfico del nodo seleccionado ](../modeling/media/createnewgraphfromselectedbutton.gif). O bien, abra el menú contextual de uno o un grupo de elementos y elija **Mostrar en mapa de código**.

   También puede arrastrar elementos de **Explorador de soluciones**, **vista de clases**o **Examinador de objetos**a un mapa de código [nuevo](#add-a-code-map) o existente. Para incluir la jerarquía primaria de los elementos, mantenga presionada la tecla **Ctrl** mientras arrastra los elementos, o bien use el botón **incluir elementos primarios** de la barra de herramientas del mapa de código para especificar la acción predeterminada. También puede arrastrar archivos de ensamblado desde fuera de Visual Studio, como desde el **Explorador de Windows**.

   > [!NOTE]
   > Cuando se agregan elementos de un proyecto que se comparte entre varias aplicaciones, como Windows Phone o Microsoft Store, esos elementos aparecen en el mapa con el proyecto de aplicación activo actualmente. Si cambia el contexto a otro proyecto de aplicación y agrega más elementos del proyecto compartido, dichos elementos aparecerán ahora con el nuevo proyecto de aplicación activo. Las operaciones que se realizan con un elemento en el mapa solo se aplican a los elementos que comparten el mismo contexto.

3. El mapa muestra los elementos seleccionados dentro de los ensamblados que los contienen.

   ![Los elementos seleccionados se muestran como grupos en el mapa](../modeling/media/codemapsshowitemsfromsolnexplorer.png)

4. Para explorar los elementos, expándalos. Mueva el puntero del mouse sobre un elemento y luego haga clic en el botón de contenido adicional (flecha hacia abajo) cuando aparezca.

   ![Expandir un nodo en un mapa de código](../modeling/media/dependencygraph_containment.png)

   Para expandir todos los elementos, selecciónelos mediante **Ctrl** +**a**, abra el menú contextual del mapa y elija **Grupo**  > **expandir**. Sin embargo, esta opción no está disponible si el hecho de expandir todos los grupos genera un mapa que no se puede usar o problemas de memoria.

5. Continúe expandiendo los elementos que le interesen hasta el nivel de clase y miembro, si es necesario.

   ![Expandir los grupos al nivel de clase y de miembro](../modeling/media/codemapsexpandtoclassandmember.png)

   Para ver los miembros que están en el código pero no aparecen en el mapa, haga clic en el icono volver a **obtener los elementos secundarios** ![Refetch icono de elementos secundarios ](../modeling/media/dependencygraph_deletednodesicon.png) en la esquina superior izquierda de un grupo.

6. Para ver más elementos relacionados con los del mapa, seleccione uno y elija **Mostrar relacionados** en la barra de herramientas del mapa de código, y luego seleccione el tipo de elementos relacionados que se agregarán al mapa. Como alternativa, seleccione uno o más elementos, abra el menú contextual y, a continuación, elija la opción **Mostrar** para el tipo de elementos relacionados que desea agregar al mapa. Por ejemplo:

    Para un **ensamblado**, elija:

    |||
    |-|-|
    |**Mostrar ensamblados a los que este hace referencia**|Agregue los ensamblados a los que este ensamblado hace referencia. Los ensamblados externos aparecen en el grupo **Externos** .|
    |**Mostrar ensamblados que hacen referencia a este**|Agregue los ensamblados de la solución que hacen referencia a este ensamblado.|

    Para un **espacio de nombres**, elija **Mostrar ensamblado contenedor**, si no está visible.

    Para una **clase** o **interfaz**, elija:

    |||
    |-|-|
    |**Mostrar tipos base**|Para una clase, agregue la clase base, así como las interfaces implementadas.<br /><br /> Para una interfaz, agregue las interfaces base.|
    |**Mostrar tipos derivados**|Para una clase, agregue las clases derivadas.<br /><br /> Para una interfaz, agregue las interfaces derivadas y las clases o structs de implementación.|
    |**Mostrar tipos a los que este hace referencia**|Agregue todas las clases y los miembros que esta clase utilice.|
    |**Mostrar tipos que hacen referencia a este**|Agregue todas las clases y los miembros que usan esta clase.|
    |**Mostrar espacio de nombres contenedor**|Agregue el espacio de nombres primario.|
    |**Mostrar espacio de nombres y ensamblado contenedores**|Agregue la jerarquía de contenedores principales.|
    |**Mostrar todos los tipos base**|Agregue la jerarquía de interfaz o de clase base de forma recursiva.|
    |**Mostrar todos los tipos derivados**|Para una clase, agregue todas las clases derivadas de forma recursiva.<br /><br /> Para una interfaz, agregue todas las interfaces derivadas y clases o structs de implementación de forma recursiva.|

     Para un **método**, elija:

    |||
    |-|-|
    |**Mostrar métodos a los que este llama**|Agregue los métodos a los que llama este método.|
    |**Mostrar campos a los que este hace referencia**|Agregue los campos a los que hace referencia este método.|
    |**Mostrar tipo contenedor**|Agregue el tipo primario.|
    |**Mostrar tipo, espacio de nombres y ensamblado contenedores**|Agregue la jerarquía de contenedores principales.|
    |**Mostrar métodos invalidados**|Para obtener un método que invalide otros métodos o que implemente un método de una interfaz, agregue todo el resumen o los métodos virtuales en las clases base invalidadas y, si existe, el método de interfaz implementado.|

     Para un **campo** o **propiedad**, elija:

    |||
    |-|-|
    |**Mostrar tipo contenedor**|Agregue el tipo primario.|
    |**Mostrar tipo, espacio de nombres y ensamblado contenedores**|Agregue la jerarquía de contenedores principales.|

    ![Mostrar los métodos invocados por este miembro](../modeling/media/codemapsshowrelatedmethods.png)

7. El mapa muestra las relaciones. En este ejemplo, el mapa muestra los métodos llamados por el método `Find` y su ubicación en la solución o externamente.

   ![Mostrar las dependencias específicas en un mapa de código](../modeling/media/codemapsspecificdependenciesintro.png)

8. Para simplificar el mapa y centrarse en partes individuales, elija **Filtros** en la barra de herramientas del mapa de código y seleccione únicamente los tipos de nodos y los vínculos que le interesan. Por ejemplo, desactive la visualización de carpetas de soluciones, ensamblados y espacios de nombres.

   ![Utilice el panel Filtro para simplificar la presentación](../modeling/media/almcodemapfilterpane.png)

## <a name="see-also"></a>Vea también

- [Vídeo: Descripción del diseño desde el código con mapas de código de Visual Studio 2015](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)
- [Usar mapas de código para depurar aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md)
- [Asignar métodos en la pila de llamadas durante la depuración](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
- [Buscar posibles problemas mediante analizadores de mapas de código](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Examinar y reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md)
- [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
