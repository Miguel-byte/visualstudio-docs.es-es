---
title: 'Cómo: cambiar el espacio de nombres de un lenguaje específico de dominio'
ms.date: 10/31/2018
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, namespace
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b64a61c02f44db0ce70b758331d0d70f7bb8014d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653770"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Cómo: cambiar el espacio de nombres de un lenguaje específico de dominio

Puede cambiar el espacio de nombres de un lenguaje específico de dominio. Realice el cambio en el **Explorador de DSL**, en las propiedades del proyecto de paquete DSL y en la información de ensamblado.

## <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Para cambiar el espacio de nombres de un lenguaje específico de dominio

1. En el **Explorador de DSL**, seleccione el nodo **DSL** .

2. En la ventana **propiedades** , cambie la propiedad **espacio de nombres** .

3. Guarde la solución y transforme las plantillas.

4. En el menú **proyecto** , elija **propiedades de DSL**.

   Aparecen las propiedades del proyecto.

5. Seleccione la pestaña **aplicación** .

6. Cambie la propiedad **espacio de nombres predeterminado** al nuevo nombre del espacio de nombres.

7. Si también desea cambiar el nombre del ensamblado, cambie la **propiedad nombre del ensamblado.**

8. Si ha cambiado el nombre del ensamblado, abra DslPackage\Package.tt y actualice esta línea:

   `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. Si ha escrito código personalizado, asegúrese de cambiar las referencias de espacio de nombres y clase en los archivos de código.

10. Restablezca la instancia experimental de Visual Studio.

    1. Elimine **\users \\** _{su nombre}_ **\AppData\Local\Microsoft\VisualStudio \\ \*Exp**.

    2. En el menú **Inicio** de Windows, elija **todos los programas**  > **Microsoft Visual Studio 2010 SDK**  > **Tools**  > **restablecer la instancia experimental**.

11. En el menú **compilar** , elija **recompilar solución**.

## <a name="see-also"></a>Vea también

[Glosario de herramientas de lenguajes específicos de dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)