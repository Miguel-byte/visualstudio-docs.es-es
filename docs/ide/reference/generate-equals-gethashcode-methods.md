---
title: Generar invalidaciones de los métodos Equals y GetHashCode de C#
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e70593bc04b576237a7f9f0f51ae6c3d37e40a88
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660039"
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-visual-studio"></a>Generación de invalidaciones de los métodos Equals y GetHashCode en Visual Studio

Esta generación de código se aplica a:

- C#

**Qué:** Permite generar métodos **Equals** y **GetHashCode**.

**Cuándo:** Genera estas invalidaciones cuando se tiene un tipo que debe compararse por uno o más campos, en lugar de por la ubicación del objeto en la memoria.

**Por qué:**

- Si implementa un tipo de valor, considere la posibilidad de invalidar el método **Equals** para obtener un mayor rendimiento a través de la implementación predeterminada del método Equals en ValueType.

- Si está implementando un tipo de referencia, considere la posibilidad de invalidar el método **Equals** si su tipo es similar a un tipo base, como Point, String, BigNumber, etc.

- Invalide el método **GetHashCode** para permitir que un tipo funcione correctamente en una tabla hash. Obtenga más información sobre los [operadores de igualdad](/dotnet/standard/design-guidelines/equality-operators).

## <a name="how-to"></a>Procedimiento

1. Coloque el cursor en algún lugar de la línea de la declaración de tipos.

   ![Código resaltado](media/overrides-highlight-cs.png)

   > [!TIP]
   > No haga doble para seleccionar el nombre del tipo o la opción de menú no estará disponible. Simplemente coloque el cursor en algún lugar de la línea.

1. A continuación, realice alguno de los siguientes procedimientos:

   - Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.

   - Haga clic con el botón derecho y seleccione el menú **Acciones rápidas y refactorizaciones**.

   - Haga clic en el botón ![icono de destornillador](../media/screwdriver-icon.png) que aparece en el margen izquierdo.

   ![Vista previa de la generación de invalidaciones](media/overrides-preview-cs.png)

1. Seleccione **Generar Equals(object)** o **Generar Equals y GetHashCode** en el menú desplegable.

1. En el cuadro de diálogo **Seleccionar miembros**, seleccione los miembros para los que quiere generar los métodos:

    ![Cuadro de diálogo de generación de invalidaciones](media/overrides-dialog-cs.png)

    > [!TIP]
    > También puede generar operadores desde este cuadro de diálogo con las casillas de verificación de la parte inferior del mismo.

   Los métodos `Equals` y `GetHashCode` se generan con implementaciones predeterminadas.

   ![Resultado de la generación de método](media/overrides-result-cs.png)

## <a name="see-also"></a>Vea también

- [Generación de código](../code-generation-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)