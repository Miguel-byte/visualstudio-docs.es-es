---
title: EndTrackingContext | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
api_name:
- EndTrackingContext
api_location:
- filetracker.dll
api_type:
- COM
helpviewer_keywords:
- EndTrackingContext
ms.assetid: c2c5d794-8dc8-4594-8717-70dc79a0e75d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 641c67c4830f4d882d2d81cb2f00599825ae5d9f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196558"
---
# <a name="endtrackingcontext"></a>EndTrackingContext
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Finaliza el contexto de seguimiento actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT WINAPI EndTrackingContext();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Una ([HRESULT]<!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->) con el ([correcto]<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->) conjunto de bits si se terminó el contexto de seguimiento.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado**: FileTracker.h  
  
## <a name="see-also"></a>Vea también  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)
