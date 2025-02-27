---
title: IDebugComPlusSymbolProvider::GetAttributedClassesinModule | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider::GetAttributedClassesinModule
- GetAttributedClassesinModule
ms.assetid: d8b087f3-1d32-4570-9eb0-7e0f7b051bc8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 48fece294145b2cea3a288b8a0480b59a123b62c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68194736"
---
# <a name="idebugcomplussymbolprovidergetattributedclassesinmodule"></a>IDebugComPlusSymbolProvider::GetAttributedClassesinModule
Recupera las clases con el atributo especificado en un módulo determinado.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetAttributedClassesinModule (
    ULONG32            ulAppDomainID,
    GUID               guidModule,
    LPOLESTR           pstrAttribute,
    IEnumDebugFields** ppEnum
);
```

```csharp
int GetAttributedClassesinModule (
    uint                 ulAppDomainID,
    Guid                 guidModule,
    string               pstrAttribute,
    out IEnumDebugFields ppEnum
);
```

#### <a name="parameters"></a>Parámetros
`ulAppDomainID`

 [in] Identificador del dominio de aplicación.

`guidModule`

 [in] Identificador único del módulo.

`pstrAttribute`

 [in] La cadena de atributo.

`ppEnum`

 [out] Devuelve una enumeración de las clases con atributos.

## <a name="return-value"></a>Valor devuelto
Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="example"></a>Ejemplo
El ejemplo siguiente muestra cómo implementar este método para un **CDebugSymbolProvider** objeto que expone el [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interfaz.

```cpp
HRESULT CDebugSymbolProvider::GetAttributedClassesinModule(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    __in_z LPOLESTR pstrAttribute,
    IEnumDebugFields** ppEnum
)
{
    HRESULT hr = S_OK;
    CComPtr<CModule> pModule;
    CComPtr<IMetaDataImport> pMetaData;
    Module_ID idModule(ulAppDomainID, guidModule);
    const void* pUnused;
    ULONG cbUnused;
    HCORENUM hEnum = 0;
    ULONG cTypeDefs = 0;
    ULONG cEnum;
    DWORD iTypeDef = 0;
    mdTypeDef* rgTypeDefs = NULL;
    IDebugField** rgFields = NULL;
    DWORD ctField = 0;
    CEnumDebugFields* pEnumFields = NULL;

    METHOD_ENTRY( CDebugSymbolProvider::GetAttributedClassesinModule );

    IfFalseGo( pstrAttribute && ppEnum , E_INVALIDARG );
    IfFailGo( GetModule( idModule, &pModule ) );
    pModule->GetMetaData( &pMetaData );

    IfFailGo( pMetaData->EnumTypeDefs( &hEnum,
                                       NULL,
                                       0,
                                       &cTypeDefs ) );

    IfFailGo( pMetaData->CountEnum( hEnum, &cEnum ) );
    pMetaData->CloseEnum(hEnum);
    hEnum = NULL;

    IfNullGo( rgTypeDefs = new mdTypeDef[cEnum], E_OUTOFMEMORY );
    IfNullGo( rgFields = new IDebugField * [cEnum], E_OUTOFMEMORY );

    IfFailGo( pMetaData->EnumTypeDefs( &hEnum,
                                       rgTypeDefs,
                                       cEnum,
                                       &cTypeDefs ) );

    for ( iTypeDef = 0; iTypeDef < cTypeDefs; iTypeDef++)
    {

        if (pMetaData->GetCustomAttributeByName( rgTypeDefs[iTypeDef],
                pstrAttribute,
                &pUnused,
                &cbUnused ) == S_OK)
        {
            if (CreateClassType( idModule, rgTypeDefs[iTypeDef], rgFields + ctField) == S_OK)
            {
                ctField++;
            }
            else
            {
                ASSERT(!"Failed to Create Attributed Class");
            }
        }
    }

    IfNullGo( pEnumFields = new CEnumDebugFields, E_OUTOFMEMORY );
    IfFailGo( pEnumFields->Initialize(rgFields, ctField) );
    IfFailGo( pEnumFields->QueryInterface( __uuidof(IEnumDebugFields),
                                           (void**) ppEnum ) );

Error:

    METHOD_EXIT( CDebugSymbolProvider::GetAttributedClassesinModule, hr );

    DELETERG( rgTypeDefs );

    for ( iTypeDef = 0; iTypeDef < ctField; iTypeDef++)
    {
        RELEASE( rgFields[iTypeDef] );
    }

    DELETERG( rgFields );
    RELEASE( pEnumFields );

    return hr;
}
```

## <a name="see-also"></a>Vea también
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
