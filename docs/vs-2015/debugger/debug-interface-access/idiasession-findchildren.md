---
title: IDiaSession::findChildren | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findChildren method
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf274bb0f572da11a9aa43248da7eaa72a2e73c3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68150425"
---
# <a name="idiasessionfindchildren"></a>IDiaSession::findChildren
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera a todos los elementos secundarios de un identificador de elemento primario especificado que coinciden con el tipo de nombre y el símbolo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT findChildren (   
   IDiaSymbol*       parent,  
   SymTagEnum        symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `parent`  
 [in] Un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objeto que representa el elemento primario. Si este símbolo primario es una función, un módulo o un bloque, a continuación, se devuelven sus elementos secundarios léxicos en `ppResult`. Si el símbolo de elemento primario es un tipo, se devuelven sus elementos secundarios de la clase. Si este parámetro es `NULL`, a continuación, `symtag` debe establecerse en `SymTagExe` o `SymTagNull`, que devuelve el ámbito global (archivo .exe).  
  
 `symtag`  
 [in] Especifica la etiqueta del símbolo de los elementos secundarios van a recuperar. Los valores se toman de la [SymTagEnum (enumeración)](../../debugger/debug-interface-access/symtagenum.md) enumeración. Establecido en `SymTagNull` para recuperar todos los elementos secundarios.  
  
 `name`  
 [in] Especifica el nombre de los elementos secundarios van a recuperar. Establecido en `NULL` todos los elementos secundarios van a recuperar.  
  
 `compareFlags`  
 [in] Especifica las opciones de comparación que se aplica a la coincidencia de nombres. Los valores de la [NameSearchOptions (enumeración)](../../debugger/debug-interface-access/namesearchoptions.md) enumeración puede usarse por sí solo o en combinación.  
  
 `ppResult`  
 [out] Devuelve un [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) recupera el objeto que contiene la lista de símbolos secundarios.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo buscar las variables locales de función `pFunc` ese nombre coincidencia `szVarName`.  
  
```cpp#  
IDiaEnumSymbols* pEnum;  
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );  
```  
  
## <a name="see-also"></a>Vea también  
 [Información general](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeración NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)   
 [Enumeración SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
