---
title: IDiaSymbol::get_offset | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_offset method
ms.assetid: 8292bb08-4dc8-4663-beb4-258f5d5a448d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2f99a9cef4266be9a3373d20f09fca8c64e5a33b
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/12/2019
ms.locfileid: "64809662"
---
# <a name="idiasymbolgetoffset"></a>IDiaSymbol::get_offset
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera el desplazamiento de la posición del símbolo. Cuando utilice el [LocationType (enumeración)](../../debugger/debug-interface-access/locationtype.md) es `LocIsRegRel` o `LocIsBitField`.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT get_offset (   
   LONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 [out] Devuelve el desplazamiento en bytes de la posición del símbolo.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
> Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## <a name="remarks"></a>Comentarios  
 El desplazamiento es desde algún punto conocido determinado previamente. Por ejemplo, el desplazamiento para un `LocIsBitField` tipo de ubicación es normalmente desde el principio de la clase contenedora.  
  
## <a name="requirements"></a>Requisitos  
  
|Requisito|DESCRIPCIÓN|  
|-----------------|-----------------|  
|Encabezado:|dia2.h|  
|Versión:|SDK de DIA v7.0|  
  
## <a name="see-also"></a>Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeración LocationType](../../debugger/debug-interface-access/locationtype.md)
