---
title: Contexto de evaluación de expresiones | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 377609cb9f971b667872c198a53b45a6288f2c15
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68152781"
---
# <a name="expression-evaluation-context"></a>Contexto de evaluación de expresiones
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] depuración, un **contexto de evaluación de expresión**:  
  
- Representa un contexto de evaluación de expresiones. Por lo general, un contexto de evaluación corresponde al ámbito léxico en el que se va a evaluar las variables, parámetros, funciones y métodos. Por ejemplo, un contexto de evaluación de expresión asociado a un marco de pila proporcionará el contexto para evaluar las variables locales, parámetros de método y los miembros de clase (si procede).  
  
- Se produce cuando un programa se ha detenido en un punto de interrupción. La expresión es una estructura de datos que representa una expresión analizada que está lista para enlace y evaluar en el contexto especificado.  
  
     Con más detalle, las expresiones se crean mediante el [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) método. Cuando se evalúa una expresión, genera una cadena imprimible que contiene el nombre y tipo de variable o argumento y su valor. Esta cadena se muestra en la ventana Inspección o en la ventana variables locales del IDE.  
  
     Dado un `BSTR` y un [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaz, puede crear un motor de depuración (DE) un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaz mediante el análisis de una expresión. Dado un `IDebugExpression2` interfaz, la DE puede obtener un valor a través de la evaluación de expresiones sincrónicas o asincrónicas. Este valor, junto con el nombre y tipo de la variable o argumento, se envía en el IDE para su presentación.  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de evaluación de expresión](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)
