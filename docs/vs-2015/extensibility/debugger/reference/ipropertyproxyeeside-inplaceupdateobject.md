---
title: IPropertyProxyEESide::InPlaceUpdateObject | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c91497815dd18dc138b2eadc462c43785830a033
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199519"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Actualiza los datos del objeto con el objeto de datos especificado y devuelve un nuevo objeto de datos que representa los datos del objeto nuevo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT InPlaceUpdateObject(  
   [in] IEEDataStorage*   dataIn,  
   [out] IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int InPlaceUpdateObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dataIn`  
 [in] Un [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) objeto que contiene los nuevos datos.  
  
 `dataOut`  
 [out] Devuelve un nuevo `IEEDataStorage` objeto que contiene los datos reemplazados.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método realmente actualiza los datos del objeto. Los datos en el valor devuelto [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) objeto no necesita ser el mismo que los datos de entrada `IEEDataStorage` objeto, pero el objeto devuelto debe reflejar el valor actual de la propiedad.  
  
 El objeto de datos entrantes no se suele implementar mediante lo EE. Sin embargo, el objeto devuelto por este método siempre se implementa mediante EE, lo que permite la implemente EE el `IEEDataStorage` interfaz en cualquier clase es el deseado.  
  
 El [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) método crea un objeto de datos basado en el objeto de datos entrantes, pero no afecta a los datos originales de la propiedad.  
  
## <a name="see-also"></a>Vea también  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)
