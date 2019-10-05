---
title: IDebugComPlusSymbolProvider::GetAttributedClassesForLanguage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- GetAttributedClassesForLanguage
- IDebugComPlusSymbolProvider::GetAttributedClassesForLanguage
ms.assetid: e5b1b8b6-52a6-4ade-9a36-644abfa9f4b2
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6913214fdde581dba2610e612b23bbf38fe17b74
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68194717"
---
# <a name="idebugcomplussymbolprovidergetattributedclassesforlanguage"></a>IDebugComPlusSymbolProvider::GetAttributedClassesForLanguage
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

지정된 된 프로그래밍 언어에서 구현 되는 지정된 된 특성을 사용 하 여 클래스를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
[C++]  
HRESULT GetAttributedClassesForLanguage (  
   GUID               guidLanguage,  
   LPOLESTR           pstrAttribute,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```  
[C#]  
int GetAttributedClassesForLanguage (  
   Guid                 guidLanguage,  
   string               pstrAttribute,  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `guidLanguage`  
 [in] 언어에 대 한 고유 식별자입니다.  
  
 `pstrAttribute`  
 [in] 특성 문자열입니다.  
  
 `ppEnum`  
 [out] 특성 클래스의 열거형을 반환합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="example"></a>예제  
 다음 예제에서는이 메서드를 구현 하는 방법을 보여 줍니다는 **CDebugSymbolProvider** 노출 하는 개체를 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) 인터페이스입니다.  
  
```cpp#  
HRESULT CDebugSymbolProvider::GetAttributedClassesForLanguage(  
    GUID guidLanguage,  
    __in_z LPOLESTR pstrAttribute,  
    IEnumDebugFields** ppEnum  
)  
{  
    HRESULT hr = S_OK;  
    CFieldList listFields;  
    CModIter ModIter;  
    CModule* pModule; // the iterator owns the reference  
    ULONG cClasses = 0;  
    DWORD iTypeDef = 0;  
    mdTypeDef* rgTypeDefs = NULL;  
    IDebugField** rgFields = NULL;  
    DWORD ctField = 0;  
    CEnumDebugFields* pEnumFields = NULL;  
  
    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));  
    ASSERT(IsValidWritePtr(ppEnum, IEnumDebugFields*));  
  
    METHOD_ENTRY( CDebugSymbolProvider::GetAttributedClassesForLanguage );  
  
    IfFalseGo( ppEnum, E_INVALIDARG );  
    *ppEnum = NULL;  
  
    // For Each Module - call EnumFields  
    IfFailGo( GetModuleIter(&ModIter) );  
  
    // Find the Max number of classes  
    while (ModIter.GetNext(&pModule))  
    {  
        CComPtr<IMetaDataImport> pMetaData;  
        HCORENUM hEnum = 0;  
        ULONG cTypeDefs;  
        ULONG cEnum;  
  
        pModule->GetMetaData( &pMetaData );  
  
        IfFailGo( pMetaData->EnumTypeDefs( &hEnum,  
                                           NULL,  
                                           0,  
                                           &cTypeDefs ) );  
        IfFailGo( pMetaData->CountEnum( hEnum, &cEnum ) );  
        cClasses += cEnum;  
    }  
  
    IfNullGo( rgTypeDefs = new mdTypeDef[cClasses], E_OUTOFMEMORY );  
    IfNullGo( rgFields = new IDebugField * [cClasses], E_OUTOFMEMORY );  
  
    ModIter.Reset();  
  
    // Create the classes  
    while (ModIter.GetNext(&pModule))  
    {  
        CComPtr<IMetaDataImport> pMetaData;  
        HCORENUM hEnum = 0;  
        ULONG cTypeDefs;  
        ULONG cEnum;  
        const void* pUnused;  
        ULONG cbUnused;  
  
        pModule->GetMetaData( &pMetaData );  
  
        IfFailGo( pMetaData->EnumTypeDefs( &hEnum,  
                                           NULL,  
                                           0,  
                                           &cTypeDefs ) );  
        IfFailGo( pMetaData->CountEnum( hEnum, &cEnum ) );  
        IfFailGo( pMetaData->EnumTypeDefs( &hEnum,  
                                           rgTypeDefs,  
                                           cEnum,  
                                           &cTypeDefs ) );  
  
        pMetaData->CloseEnum(hEnum);  
        hEnum = NULL;  
  
        for ( iTypeDef = 0; iTypeDef < cTypeDefs; iTypeDef++)  
        {  
  
            if (pMetaData->GetCustomAttributeByName( rgTypeDefs[iTypeDef],  
                    pstrAttribute,  
                    &pUnused,  
                    &cbUnused ) == S_OK)  
            {  
                // Only return classes implemeted in the correct language  
  
                if (pModule->ClassImplementedInLanguage( rgTypeDefs[iTypeDef],  
                        guidLanguage) )  
                {  
                    if (CreateClassType( pModule->GetID(),  
                                         rgTypeDefs[iTypeDef],  
                                         rgFields + ctField) == S_OK)  
                    {  
                        ctField++;  
                    }  
                    else  
                    {  
                        ASSERT(!"Failed to Create Attributed Class");  
                    }  
                }  
            }  
        }  
    }  
  
    IfNullGo( pEnumFields = new CEnumDebugFields, E_OUTOFMEMORY );  
    IfFailGo( pEnumFields->Initialize(rgFields, ctField) );  
    IfFailGo( pEnumFields->QueryInterface( __uuidof(IEnumDebugFields),  
                                           (void**) ppEnum ) );  
  
Error:  
  
    METHOD_EXIT( CDebugSymbolProvider::GetAttributedClassesForLanguage, hr );  
  
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
  
## <a name="see-also"></a>참고 항목  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
