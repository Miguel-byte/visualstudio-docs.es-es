---
title: IDebugBinder | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dc00c50e3c340ab0685ab1010c6e924e77a18a09
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431706"
---
# <a name="idebugbinder"></a>IDebugBinder
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión del evaluador de expresiones Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Esta interfaz enlaza a un campo de símbolo, suelen ser devuelto por el proveedor de símbolos, a un contexto de la memoria o el objeto que contiene el valor actual del símbolo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugBinder : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Esta interfaz admite la evaluación de expresión y debe ser implementada por el motor de depuración (DE).  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Esta interfaz se usa en el proceso de evaluación de expresiones y se utiliza normalmente en la implementación de [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) y [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugBinder`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Obtiene el contexto de la memoria o un objeto que contiene el valor actual del símbolo.|  
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Determina el tipo de tiempo de ejecución de un objeto.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Convierte una dirección de memoria o la ubicación del objeto en un contexto de la memoria.|  
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|Obtiene un [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) objeto utilizado para crear parámetros de función.|  
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Obtiene el tipo exacto de una variable.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz devuelve objetos que se usan por el evaluador de expresiones en árboles de análisis. El evaluador de expresiones analiza una expresión utilizando el proveedor de símbolos para convertir los símbolos de la expresión a las instancias de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md), que describen cada símbolo en cuanto a su tipo y la ubicación en el código fuente. El [enlazar](../../../extensibility/debugger/reference/idebugbinder-bind.md) método convierte `IDebugField` objetos [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objetos que se conectan o enlazar un símbolo de tipo a un valor real en la memoria. Estos `IDebugObject` objetos, a continuación, se almacenan en un árbol de análisis para evaluarlos posteriormente.  
  
## <a name="requirements"></a>Requisitos  
 Header: ee.h  
  
 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de evaluación de expresión](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
