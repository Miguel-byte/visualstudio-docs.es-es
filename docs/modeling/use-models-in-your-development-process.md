---
title: Usar modelos en el proceso de desarrollo
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UML, using models
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d30efd450f18832caadcc9a0008facc4388cd70a
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986292"
---
# <a name="use-models-in-your-development-process"></a>Usar modelos en el proceso de desarrollo

En Visual Studio puede usar un modelo para que le ayude a comprender y modificar un sistema, aplicación o componente. Un modelo puede ayudarle a visualizar el mundo en el que trabaja el sistema, a clarificar las necesidades de los usuarios, a definir la arquitectura del sistema, a analizar el código y a garantizar que el código satisface los requisitos. Consulte [vídeo de Channel 9: mejora de la arquitectura a través del modelado](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Improving-architecture-through-modeling).

Para ver qué versiones de Visual Studio admite cada tipo de modelo, consulte [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

Los modelos pueden ayudarle de varias maneras:

- Dibujar diagramas de modelado le ayuda a clarificar los conceptos implicados en los requisitos, la arquitectura y el diseño de alto nivel. Para obtener más información, vea [requisitos de usuario de modelo](../modeling/model-user-requirements.md).

- Trabajar con modelos puede servirle de ayuda para poner de manifiesto las incoherencias que pudiera haber en los requisitos.

- La comunicación con modelos le permite transmitir conceptos importantes con una ambigüedad menor que la del lenguaje natural. Para obtener más información, vea [modelar la arquitectura de la aplicación](../modeling/model-your-app-s-architecture.md).

- A veces puede usar modelos para generar código u otros artefactos como documentos o esquemas de base de datos. Por ejemplo, los componentes de modelado de Visual Studio se generan a partir de un modelo. Para obtener más información, vea [generar y configurar la aplicación a partir de modelos](../modeling/generate-and-configure-your-app-from-models.md).

Puede usar modelos en una gran variedad de procesos, desde los extremadamente ágiles hasta los muy elaborados.

## <a name="use-models-to-reduce-ambiguity"></a>Usar modelos para reducir la ambigüedad

El lenguaje de modelos es menos ambiguo que el lenguaje natural y está diseñado para expresar las ideas que suelen emplearse durante el desarrollo de software.

Si el proyecto se compone de un equipo pequeño que busca procesos ágiles, puede usar los modelos para dar mayor claridad a los casos de usuario. En las conversaciones que mantenga con el cliente sobre sus necesidades, disponer de un modelo puede generar preguntas útiles con más rapidez y en relación con un área más amplia del producto que las que surgirían escribiendo una maqueta o prototipo de código.

Si el proyecto es grande y participan equipos que se encuentran en distintas partes del mundo, puede usar modelos que le ayuden a transmitir los requisitos y la arquitectura de forma más eficaz que a través de un documento de texto sin formato.

En ambos casos, la creación de un modelo casi siempre reduce significativamente las incoherencias y las ambigüedades. Los participantes en el proyecto a menudo tienen concepciones distintas del mundo empresarial en el que trabaja el sistema y los desarrolladores suelen tener ideas distintas sobre el funcionamiento del sistema. Cuando se usa un modelo como eje central de una conversación, suelen salir a la luz estas diferencias. Para obtener más información sobre cómo usar un modelo para reducir las incoherencias, vea [requisitos de usuario de modelo](../modeling/model-user-requirements.md).

## <a name="use-models-with-other-artifacts"></a>Usar modelos con otros artefactos

Un modelo no constituye por sí mismo una arquitectura ni una especificación de requisitos. Es una herramienta que permite expresar algunos aspectos de estos elementos con mayor claridad, pero no se pueden expresar todos los conceptos que se requieren durante el diseño de software. Por tanto, los modelos deben usarse junto con otros medios de comunicación, como páginas o párrafos de OneNote, documentos de Microsoft Office, elementos de trabajo en Team Foundation o notas rápidas en la pared de la habitación del proyecto. A excepción de este último, todos estos tipos de objetos pueden vincularse a elementos del modelo.

A continuación se enumeran otros aspectos de especificación que se usan habitualmente con los modelos. En función de la escala y el estilo del proyecto, podrá usar varios o ninguno de estos aspectos:

- Casos de usuario. Un caso de usuario es una descripción breve, que se analiza con los usuarios y demás participantes, de un aspecto del comportamiento del sistema que se proporcionará en una de las iteraciones del proyecto. Un caso de usuario típico comienza "el cliente podrá..." Un caso de usuario puede presentar un grupo de casos de uso, o puede definir extensiones de casos de uso desarrollados previamente. Si se definen o amplían casos de uso, el caso de usuario resulta más claro.

- Solicitudes de cambio. Una solicitud de cambio de un proyecto más formal es muy similar a un caso de usuario en un proyecto más ágil. En el enfoque ágil, todos los requisitos se tratan como modificaciones del trabajo desarrollado en iteraciones anteriores.

- Descripción de casos de uso. Un caso de uso representa un mecanismo mediante el cual un usuario interactúa con el sistema para lograr un objetivo determinado. Una descripción completa incluiría el objetivo, la secuencia de eventos principal y alternativa, y los resultados excepcionales. Con los diagramas de casos de uso, resulta más fácil resumir y proporcionar información general sobre los casos de uso.

- Escenarios. Un escenario es una descripción bastante detallada de una secuencia de eventos que muestran cómo el sistema, los usuarios y otros sistemas trabajan juntos para ofrecer un resultado válido a las partes interesadas. Puede tener la forma de una presentación con diapositivas de la interfaz de usuario o un prototipo de la interfaz de usuario. En un escenario se puede describir un caso de uso o una secuencia de casos de uso.

- Glosario. En el glosario de requisitos del proyecto se describen las palabras con las que los clientes explican su mundo. La interfaz de usuario y los modelos de requisitos también deben usar estos términos. Un diagrama de clases puede ayudar a aclarar las relaciones entre la mayoría de estos términos. Con la creación de los diagramas y el glosario, no solo se reducen los malentendidos entre los usuarios y los desarrolladores, sino que también casi siempre se ponen de manifiesto los malentendidos entre las distintas partes interesadas.

- Reglas de negocio. Muchas reglas de negocio se pueden expresar como restricciones invariables de las asociaciones y atributos del modelo de clases de requisitos y como restricciones de los diagramas de secuencia.

- Diseño de alto nivel. Describe los elementos principales y cómo encajan unos con otros. Los diagramas de componentes, secuencia e interfaces constituyen una parte fundamental de un diseño de alto nivel.

- Modelos de diseño. Describen las reglas de diseño que comparten diferentes elementos del sistema.

- Especificaciones de prueba. Los diagramas de secuencia y los de actividades pueden resultar muy útiles en los scripts de prueba y en los diseños del código de prueba para describir secuencias de pasos de prueba. Las pruebas del sistema deben expresarse en términos del modelo de requisitos para que se puedan modificar fácilmente cuando varíen los requisitos.

- Plan de proyecto. El plan del proyecto o trabajo pendiente establece cuándo se entregará cada característica. Puede definir cada característica estableciendo qué casos de uso y reglas de negocio se implementan o amplían. Puede hacer referencia a los casos de uso y a las reglas de negocio directamente en el plan, o puede definir un conjunto de características en un documento diferente y usar los títulos de estas características en el plan.

## <a name="use-models-in-iteration-planning"></a>Usar modelos en la planeación de iteraciones

Aunque todos los proyectos difieren en su escala y organización, un proyecto normal se planea como una serie de iteraciones de entre dos y seis semanas. Es importante planear iteraciones suficientes, de modo que los comentarios de las iteraciones iniciales puedan usarse para ajustar el ámbito y los planes en iteraciones posteriores.

Las sugerencias que aquí le ofrecemos le resultarán útiles para reconocer las ventajas del modelado en un proyecto iterativo.

### <a name="sharpen-focus-as-each-iteration-approaches"></a>Nitidez del enfoque a medida que se aproxima cada iteración

A medida que se acerca cada iteración, use modelos que le ayuden a definir los resultados que va a entregar al final de la iteración.

- En las iteraciones iniciales no debe modelar todo en detalle. En la primera iteración, cree un diagrama de clases para los elementos primarios del glosario del usuario, dibuje un diagrama de los casos de uso principales y dibuje un diagrama de los componentes principales. No describa estos elementos con mucho detalle porque la información cambiará posteriormente en el proyecto. Use los términos definidos en este modelo para crear una lista de características o casos de usuario principales. Asigne las características a las iteraciones para equilibrar en la medida de lo posible la carga de trabajo calculada a lo largo del proyecto. Estas asignaciones variarán a medida que avance el proyecto.

- Intente implementar versiones simplificadas de todos los casos de uso más importantes en una iteración inicial. Amplíe estos casos de uso en iteraciones posteriores. Con este enfoque, se reduce el riesgo de detectar demasiado tarde un error en los requisitos o en la arquitectura del proyecto.

- Cuando se acerque el final de cada iteración, organice un taller sobre requisitos para definir en detalle los requisitos o casos de usuario que se desarrollarán en la iteración siguiente. Invite a los usuarios y a las partes interesadas del negocio que pueden establecer las prioridades, además de a los desarrolladores y a los evaluadores del sistema. Dedique al menos tres horas para definir los requisitos de una iteración de dos semanas.

- El objetivo del taller es que todos acuerden qué objetivos deben conseguirse al final de la iteración siguiente. Use los modelos como una herramienta más para dejar claros los requisitos. La salida del taller es un trabajo pendiente de iteración: es decir, una lista de tareas de desarrollo en Team Foundation y conjuntos de pruebas en [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)].

- En el taller de requisitos, analice el diseño solo en la medida en que necesite determinar las estimaciones de las tareas de desarrollo. De lo contrario, restrinja la conversación al comportamiento del sistema que los usuarios pueden experimentar directamente. Mantenga el modelo de requisitos separado del modelo de arquitectura.

- Con un poco de ayuda por su parte, el personal no técnico que participa en el proyecto no tendrá problemas para comprender los diagramas de UML.

### <a name="link-model-to-work-items"></a>Vincular modelo a elementos de trabajo

Después del taller de requisitos, elabore los detalles del modelo de requisitos y vincule el modelo a las tareas de desarrollo. Para ello, puede vincular los elementos de trabajo de Team Foundation a los elementos del modelo.

Puede vincular cualquier elemento a los elementos de trabajo, pero los elementos más útiles son estos:

- Comentarios en los que se describan reglas de negocio o requisitos de calidad de servicio. Para obtener más información, vea [requisitos de usuario de modelo](../modeling/model-user-requirements.md).

### <a name="link-model-to-tests"></a>Vincular el modelo a las pruebas

Use el modelo de requisitos para dirigir el diseño de las pruebas de aceptación. Cree estas pruebas al mismo tiempo que el trabajo de desarrollo.

Para obtener más información sobre esta técnica, vea [desarrollar pruebas a partir de un modelo](../modeling/develop-tests-from-a-model.md).

### <a name="estimate-remaining-work"></a>Calcular el trabajo restante

Un modelo de requisitos puede ayudar a calcular el tamaño total del proyecto frente al tamaño de cada iteración. Evaluar el número y la complejidad de los casos de uso y las clases puede ayudar a calcular el trabajo de desarrollo que será necesario. Después de completar las primeras iteraciones, una comparación de los requisitos cubiertos y de los requisitos que quedan por cubrir puede proporcionar una idea aproximada del costo y el ámbito del resto del proyecto.

Cuando se acerque el final de cada iteración, revise la asignación de requisitos a futuras iteraciones. Quizás le resulte útil representar el estado del software al final de cada iteración como un subsistema en un diagrama de casos de uso. En las conversaciones, puede mover los casos de uso y las extensiones de casos de uso de estos subsistemas a otros.

## <a name="levels-of-abstraction"></a>Niveles de abstracción

El nivel de abstracción de los modelos varía en función del software. Los modelos más concretos representan directamente el código del programa y los modelos más abstractos representan conceptos del negocio que pueden o no estar representados en el código.

Un modelo puede verse a través de distintos tipos de diagramas. Para obtener información sobre los modelos y los diagramas, vea [crear modelos para la aplicación](../modeling/create-models-for-your-app.md).

Los distintos tipos de diagramas resultan útiles para describir el diseño con diferentes niveles de abstracción. Muchos de los tipos de diagramas resultan útiles para varios niveles. En esta tabla se muestra cómo puede usar cada tipo de diagrama.

|Nivel de diseño|Tipos de diagramas|
|-|-|
|Proceso de negocio<br /><br /> Conocer el contexto en el que se va a usar el sistema le ayuda a comprender qué es lo que el usuario necesita de este sistema.|-Los diagramas de clases conceptuales describen los conceptos empresariales utilizados en el proceso empresarial.|
|Requisitos de los usuarios<br /><br /> Definición de lo que los usuarios necesitan del sistema.|-Las reglas de negocios y los requisitos de calidad de servicio se pueden describir en documentos independientes.|
|Diseño de alto nivel<br /><br /> Estructura general del sistema: sus componentes principales y cómo se acoplan.|-Los diagramas de dependencia describen cómo se estructura el sistema en partes interdependientes. Puede validar el código de programa con los diagramas de dependencia para asegurarse de que se adhiere a la arquitectura.|
|Análisis de código<br /><br /> Los diagramas se pueden generar a partir del código.|-Los diagramas de dependencia muestran las dependencias entre las clases. El código actualizado se puede validar con un diagrama de dependencia.<br />-Los diagramas de clases muestran las clases del código.|

## <a name="external-resources"></a>Recursos externos

|**Categoría**|**Links**|
|-|-|
|**Vídeos**|![vínculo a vídeo](../data-tools/media/playvideo.gif) [vídeos de procedimientos de MSDN: Cómo crear y usar modelos y diagramas UML (Visual Studio 2010 Ultimate)](/previous-versions/visualstudio/visual-studio-2010/dd831853(v=vs.100))<br /><br /> ![vínculo al vídeo](../data-tools/media/playvideo.gif) [Channel 9: UML con Visual Studio 2010](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-1-brainstorming-a-project)<br /><br /> ![vínculo a vídeo](../data-tools/media/playvideo.gif) [la serie de procedimientos de MSDN: herramientas y extensibilidad UML (Visual Studio 2010 Ultimate)](/previous-versions/visualstudio/visual-studio-2010/dd831853(v=vs.100))|
|**Foros**|- [Herramientas de visualización y modelado de Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />- [SDK de visualización y modelado de Visual Studio (Herramientas ADSL)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|
|**Blogs**|[Microsoft DevOps](https://devblogs.microsoft.com/devops/)|
|**Artículos y diarios técnicos**|[Centro de arquitectura - MSDN](/previous-versions/dn630665(v=msdn.10))<br /><br /> [Orientación para las herramientas de arquitectura de Visual Studio](../modeling/visual-studio-architecture-tooling-guidance.md)|

## <a name="see-also"></a>Vea también

- [Usar modelos en el desarrollo ágil](https://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f)
- [Crear modelos para la aplicación](../modeling/create-models-for-your-app.md)
- [Requisitos del usuario de modelos](../modeling/model-user-requirements.md)
- [Modelar la arquitectura de la aplicación](../modeling/model-your-app-s-architecture.md)
- [Desarrollar pruebas a partir de un modelo](../modeling/develop-tests-from-a-model.md)
- [Estructurar la solución de modelado](../modeling/structure-your-modeling-solution.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
