---
title: IDebugComPlusSymbolProvider::GetAddressesInModuleFromPosition | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetAddressesInModuleFromPosition
- IDebugComPlusSymbolProvider::GetAddressesInModuleFromPosition
ms.assetid: f901c66e-f53c-4ea0-8004-d8fcbf46f916
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3000b93a9ce7f3ba56325943d48c5ac686ddde38
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338721"
---
# <a name="idebugcomplussymbolprovidergetaddressesinmodulefromposition"></a>IDebugComPlusSymbolProvider::GetAddressesInModuleFromPosition
디버그 주소 배열에 지정된 된 모듈에 문서 위치를 매핑합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetAddressesInModuleFromPosition(
   ULONG32                  ulAppDomainID,
   GUID                     guidModule,
   IDebugDocumentPosition2* pDocPos,
   BOOL                     fStatmentOnly,
   IEnumDebugAddresses**    ppEnumBegAddresses,
   IEnumDebugAddresses**    ppEnumEndAddresses
);
```

```csharp
int GetAddressesInModuleFromPosition(
   uint                    ulAppDomainID,
   Guid                    guidModule,
   IDebugDocumentPosition2 pDocPos,
   bool                    fStatmentOnly,
   out IEnumDebugAddresses ppEnumBegAddresses,
   out IEnumDebugAddresses ppEnumEndAddresses
);
```

## <a name="parameters"></a>매개 변수
`ulAppDomainID`\
[in] 응용 프로그램 도메인 식별자입니다.

`guidModule`\
[in] 모듈의 고유 식별자입니다.

`pDocPos`\
[in] 문서 위치입니다.

`fStatmentOnly`\
[in] 경우 `TRUE`를 단일 문으로 디버그 주소를 제한 합니다.

`ppEnumBegAddresses`\
[out] 이 문 또는 줄을 사용 하 여 연결 된 시작 디버그 주소에 대 한 열거자를 반환 합니다.

`ppEnumEndAddresses`\
[out] 이 문 또는 줄에 연관 된 끝 디버그 주소에 대 한 열거자를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="example"></a>예제
 다음 예제에서는이 메서드를 구현 하는 방법을 보여 줍니다는 **CDebugSymbolProvider** 노출 하는 개체를 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) 인터페이스입니다.

```cpp
HRESULT CDebugSymbolProvider::GetAddressesInModuleFromPosition(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    IDebugDocumentPosition2* pDocPos,
    BOOL fStatementOnly,
    IEnumDebugAddresses** ppEnumBegAddresses,
    IEnumDebugAddresses** ppEnumEndAddresses
)
{
    GUID guidNULL = {0};

    if (guidNULL == guidModule)
    {
        return GetAddressesInAppDomainFromPosition( ulAppDomainID,
                pDocPos,
                fStatementOnly,
                ppEnumBegAddresses,
                ppEnumEndAddresses );
    }
    else
    {
        return GetAddressesInModuleFromPositionHelper( ulAppDomainID,
                guidModule,
                pDocPos,
                fStatementOnly,
                ppEnumBegAddresses,
                ppEnumEndAddresses );
    }
}

HRESULT CDebugSymbolProvider::GetAddressesInModuleFromPositionHelper(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    IDebugDocumentPosition2* pDocPos,
    BOOL fStatementOnly,
    IEnumDebugAddresses** ppEnumBegAddresses,
    IEnumDebugAddresses** ppEnumEndAddresses
)
{
    HRESULT hr = S_OK;
    CComBSTR bstrFileName;
    TEXT_POSITION posBeg;
    TEXT_POSITION posEnd;
    DWORD dwLine;
    USHORT segRet = 0;
    ULONG offRet = 0;
    CAddrList listAddr;
    CAddrList listAddrEnd;
    CAddrList* plistAddrEnd = NULL;
    bool fFileFound = false;
    Module_ID idModule(ulAppDomainID, guidModule);
    DWORD dwListCount;
    bool fFoundAddresses = false;
    CComPtr<CModule> pmodule;
    DWORD dwBegCol = 0;
    DWORD dwEndCol = 0;

    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));
    ASSERT(IsValidInterfacePtr(pDocPos, IDebugDocumentPosition2));
    ASSERT(IsValidWritePtr(ppEnumBegAddresses, IEnumDebugAddresses*));

    METHOD_ENTRY(CDebugSymbolProvider::GetAddressesInModuleFromPositionHelper);

    // Bail on Invalid Args

    IfFalseGo( pDocPos && ppEnumBegAddresses, E_INVALIDARG );

    *ppEnumBegAddresses = NULL;
    if (ppEnumEndAddresses)
    {
        *ppEnumEndAddresses = NULL;
        plistAddrEnd = &listAddrEnd;
    }

    // Get the Position

    IfFailGo( pDocPos->GetFileName(&bstrFileName) );
    IfFailGo( pDocPos->GetRange(&posBeg, &posEnd) );

    // Iterate over the module list accumulating addresses
    // that match the position

    dwLine = posBeg.dwLine;
    IfFailGo( GetModule( idModule, &pmodule ) );
    dwListCount = listAddr.GetCount();

    if ( fStatementOnly )
    {
        dwBegCol = posBeg.dwColumn;
        dwEndCol = posBeg.dwLine == posEnd.dwLine ? posEnd.dwColumn : DWORD( -1);
    }
    else
    {
        dwBegCol = 0;
        dwEndCol = DWORD( -1);
    }

    while (!fFoundAddresses && dwLine <= posEnd.dwLine )
    {
        hr = pmodule->GetAddressesFromLine( bstrFileName,
                                            dwLine,
                                            posEnd.dwLine,
                                            dwBegCol,
                                            dwEndCol,
                                            &listAddr,
                                            plistAddrEnd );

        dwLine++;
        dwBegCol = 0;
        dwEndCol = dwLine == posEnd.dwLine ? posEnd.dwColumn : DWORD( -1);

        if (hr == E_SH_INVALID_POSITION)
        {
            fFileFound = true;
            break;
        }

        if (FAILED(hr))
        {
            // Move on to the next module
            break;
        }

        fFileFound = true;
        fFoundAddresses = listAddr.GetCount() != dwListCount;
    }

    // Distinguish no file from bad position in the file
    IfFalseGo( fFileFound, E_SH_FILE_NOT_FOUND);

    // If the list is empty the position is bad
    IfFalseGo( listAddr.GetCount(), E_SH_INVALID_POSITION );

    // Create enumerators
    IfFailGo( CreateEnumerator( ppEnumBegAddresses, &listAddr ) );
    if (ppEnumEndAddresses)
    {
        IfFailGo( CreateEnumerator( ppEnumEndAddresses, &listAddrEnd ) );
    }

Error:

    METHOD_EXIT(CDebugSymbolProvider::GetAddressesInModuleFromPositionHelper, hr);

    return hr;
}
```

## <a name="see-also"></a>참고자료
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)