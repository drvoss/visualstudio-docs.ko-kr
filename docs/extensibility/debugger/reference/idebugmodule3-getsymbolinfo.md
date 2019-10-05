---
title: IDebugModule3::GetSymbolInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::GetSymbolInfo
helpviewer_keywords:
- GetSymbolInfo method
- IDebugModule3::GetSymbolInfo method
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bd952242db8b7394fa8915319686ac431b84947d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323944"
---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
각 경로 검색 한 결과 뿐만 아니라 기호에 대 한 검색 하는 경로의 목록을 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetSymbolInfo(
    SYMBOL_SEARCH_INFO_FIELDS  dwFields,
    MODULE_SYMBOL_SEARCH_INFO* pInfo
);
```

```csharp
int GetSymbolInfo(
    enum_SYMBOL_SEARCH_INFO_FIELDS dwFields,
    MODULE_SYMBOL_SEARCH_INFO[]    pinfo
);
```

## <a name="parameters"></a>매개 변수
`dwFields`\
[in] 플래그의 조합 된 [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) 의 필드를 지정 하는 열거형 `pInfo` 작성 해야 할 합니다.

`pInfo`\
[out] A [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) 멤버가 지정 된 정보로 채워질 구조체입니다. 이 경우 null 값이이 메서드가 반환 `E_INVALIDARG`합니다.

## <a name="return-value"></a>반환 값
메서드가 성공 하는 경우 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

> [!NOTE]
> 반환된 된 문자열 (에 `MODULE_SYMBOL_SEARCH_INFO` 구조) 비워 둘 수 없습니다 경우에 `S_OK` 반환 됩니다. 이 경우에 반환할 검색 정보가 없습니다.

## <a name="remarks"></a>설명
경우는 `bstrVerboseSearchInfo` 필드는 `MODULE_SYMBOL_SEARCH_INFO` 구조체가 비어 있는 경우를 검색 하는 경로 및 해당 검색 결과의 목록을 포함 합니다. 목록 결과 뒤에 ("..."), 줄임표 뒤에 경로 형식은입니다. 둘 이상의 경로 결과 쌍의 경우 각 쌍은 "\r\n" (캐리지 리턴/줄 바꿈) 쌍으로 구분 됩니다. 패턴은 다음과 같습니다.

\<path>...\<result>\r\n\<path>...\<result>\r\n\<path>...\<result>

마지막 항목 \r\n 순서 없는 참고 합니다.

## <a name="example"></a>예제
이 예제에서는이 메서드는 세 개의 다른 검색 결과 사용 하 여 세 개의 경로 반환합니다. 각 줄은 캐리지 리턴/줄 바꿈 쌍으로 종료 됩니다. 이 예제의 출력을 단일 문자열로 검색 결과 출력 합니다.

> [!NOTE]
> 상태 결과 바로 다음에 "..." 줄의 끝까지 전부입니다.

```cpp
void ShowSymbolSearchResults(IDebugModule3 *pIDebugModule3)
{
    MODULE_SYMBOL_SEARCH_INFO ssi = { 0 };
    HRESULT hr;
    hr = pIDebugModule3->GetSymbolInfo(SSIF_VERBOSE_SEARCH_INFO,&ssi);
    if (SUCCEEDED(hr)) {
        CComBSTR searchInfo = ssi.bstrVerboseSearchInfo;
        if (searchInfo.Length() != 0) {
            std::wcout << (wchar_t *)(BSTR)searchInfo;
            std::wcout << std::endl;
        }
    }
}
```

**c:\symbols\user32.pdb... 파일을 찾을 수 없습니다.** 
**c:\winnt\symbols\user32.pdb... 버전이 일치 하지 않습니다.** 
 **\\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... 기호를 로드 합니다.**

## <a name="see-also"></a>참고자료

- [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)
- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
