---
title: IDebugComPlusSymbolProvider2::LoadSymbolsFromCallback | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- LoadSymbolsFromCallback
- IDebugComPlusSymbolProvider2::LoadSymbolsFromCallback
ms.assetid: 905315ba-8e9b-4889-b9da-98e1441950ad
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 108d50788992eb8316811bb5d9c7d327c3d62eda
ms.sourcegitcommit: 0cd282a7584b9bfd4df7882f8fdf3ad8a270e219
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2019
ms.locfileid: "62540603"
---
# <a name="idebugcomplussymbolprovider2loadsymbolsfromcallback"></a>IDebugComPlusSymbolProvider2::LoadSymbolsFromCallback
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cargas de depuración de símbolos mediante el método de devolución de llamada especificadas.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT LoadSymbolsFromCallback(  
   ULONG32   ulAppDomainID,  
   GUID      guidModule,  
   IUnknown* pUnkMetadataImport,  
   IUnknown* pUnkCorDebugModule,  
   BSTR      bstrModuleName,  
   BSTR      bstrSymSearchPath,  
   IUnknown* pCallback  
);  
```  
  
```csharp  
int LoadSymbolsFromCallback(  
   uint   ulAppDomainID,  
   Guid   guidModule,  
   object pUnkMetadataImport,  
   object pUnkCorDebugModule,  
   string bstrModuleName,  
   string bstrSymSearchPath,  
   object pCallback  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ulAppDomainID`  
 [in] Identificador del dominio de aplicación.  
  
 `guidModule`  
 [in] Identificador único del módulo.  
  
 `pUnkMetadataImport`  
 [in] Objeto que contiene los metadatos de símbolos.  
  
 `pUnkCorDebugModule`  
 [in] Objeto que implementa el [ICorDebugModule (interfaz)](/dotnet/framework/unmanaged-api/debugging/icordebugmodule-interface).  
  
 `bstrModuleName`  
 [in] Nombre del módulo.  
  
 `bstrSymSearchPath`  
 [in] Ruta de acceso para buscar el archivo de símbolos.  
  
 `pCallback`  
 [in] Objeto que representa el método de devolución de llamada.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra cómo implementar este método para un **CDebugSymbolProvider** objeto que expone el [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md) interfaz.  
  
```cpp#  
HRESULT CDebugSymbolProvider::LoadSymbolsFromCallback(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    IUnknown *pMetadataImport,  
    IUnknown * _pCorModule,  
    BSTR bstrModule,  
    BSTR bstrSearchPath,  
    IUnknown *pCallback)  
{  
    EMIT_TICK_COUNT("Entry -- Loading symbols for the following target:");  
    USES_CONVERSION;  
    EmitTickCount(W2A(bstrModule));  
  
    CAutoLock Lock(this);  
  
    HRESULT hr = S_OK;  
    CComPtr<IMetaDataImport> pMetadata;  
    CComPtr<ICorDebugModule> pCorModule;  
  
    CModule* pmodule = NULL;  
    CModule* pmoduleNew = NULL;  
    bool fAlreadyLoaded = false;  
    Module_ID idModule(ulAppDomainID, guidModule);  
    bool fSymbolsLoaded = false;  
    DWORD dwCurrentState = 0;  
  
    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));  
    ASSERT(IsValidInterfacePtr(pMetadataImport, IUnknown));  
  
    METHOD_ENTRY( CDebugSymbolProvider::LoadSymbol );  
  
    IfFalseGo( pMetadataImport, E_INVALIDARG );  
    IfFalseGo( _pCorModule, E_INVALIDARG );  
  
    IfFailGo( pMetadataImport->QueryInterface( IID_IMetaDataImport,  
              (void**)&pMetadata) );  
  
    IfFailGo( _pCorModule->QueryInterface( IID_ICorDebugModule,  
                                           (void**)&pCorModule) );  
  
    ASSERT(guidModule != GUID_NULL);  
  
    fAlreadyLoaded = GetModule( idModule, &pmodule ) == S_OK;  
  
    IfNullGo( pmoduleNew = new CModule, E_OUTOFMEMORY );  
  
    //  
    //  We are now allowing modules to be created that do not have SymReaders.  
    //  It is likely there are a number of corner cases being ignored  
    //  that will require knowledge of the hr result below.  
    //  
    dwCurrentState = m_pSymProvGroup ? m_pSymProvGroup->GetCurrentState() : 0;  
    HRESULT hrLoad = pmoduleNew->Create( idModule,  
                                         dwCurrentState,  
                                         pMetadata,  
                                         pCorModule,  
                                         bstrModule,  
                                         bstrSearchPath,  
                                         pCallback );  
  
    if (hrLoad == S_OK)  
    {  
        fSymbolsLoaded = true;  
    }  
  
    // Remove the old module  
    if (fAlreadyLoaded)  
    {  
        IfFailGo(pmoduleNew->AddEquivalentModulesFrom(pmodule));  
        RemoveModule( pmodule );  
    }  
  
    IfFailGo( AddModule( pmoduleNew ) );  
  
Error:  
  
    RELEASE (pmodule);  
    RELEASE (pmoduleNew);  
  
    if (SUCCEEDED(hr) && !fSymbolsLoaded)  
    {  
        hr = hrLoad;  
    }  
  
    METHOD_EXIT( CDebugSymbolProvider::LoadSymbol, hr );  
    EMIT_TICK_COUNT("Exit");  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)
