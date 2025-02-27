---
title: Función SccWillCreateSccFile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ac7657258b79b2e53bee8138bc5b2728f618eac
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720119"
---
# <a name="sccwillcreatesccfile-function"></a>SccWillCreateSccFile (Función)
Esta función determina si el complemento de control de código fuente admite la creación de MSSCCPRJ. Archivo SCC para cada uno de los archivos especificados.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccWillCreateSccFile(
   LPVOID  pContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LPBOOL  pbSccFiles
);
```

#### <a name="parameters"></a>Parámetros
 pContext

de Puntero de contexto del complemento de control de código fuente.

 N archivos

de El número de nombres de archivo incluidos en la matriz de `lpFileNames`, así como la longitud de la matriz de `pbSccFiles`.

 lpFileNames

de Una matriz de nombres de archivo completos que se van a comprobar (el llamador debe asignar la matriz).

 pbSccFiles

[in, out] Matriz en la que se almacenan los resultados.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|Correcto.|
|SCC_E_INVALIDFILEPATH|Una de las rutas de acceso de la matriz no es válida.|
|SCC_E_NONSPECIFICERROR|Error no específico.|

## <a name="remarks"></a>Comentarios
 Se llama a esta función con una lista de archivos para determinar si el complemento de control de código fuente proporciona compatibilidad en MSSCCPRJ. Archivo SCC para cada uno de los archivos especificados (para obtener más información sobre MSSCCPRJ). Archivo SCC, vea [MSSCCPRJ. Archivo SCC](../extensibility/mssccprj-scc-file.md)). Los complementos de control de código fuente pueden declarar si tienen la capacidad de crear MSSCCPRJ. Archivos SCC declarando `SCC_CAP_SCCFILE` durante la inicialización. El complemento devuelve `TRUE` o `FALSE` por archivo en la matriz de `pbSccFiles` para indicar cuál de los archivos especificados tiene MSSCCPRJ. Compatibilidad con SCC. Si el complemento devuelve un código de éxito de la función, se respetan los valores de la matriz devuelta. En caso de error, se omite la matriz.

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [Archivo MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)