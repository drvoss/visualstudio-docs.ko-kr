---
title: MODULE_SYMBOL_SEARCH_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c521ebe321813013b83a951d4d2aa5f60fd1646d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346623"
---
# <a name="modulesymbolsearchinfo"></a>MODULE_SYMBOL_SEARCH_INFO

에 대 한 검색이 있는 기호 검색 경로 대 한 상태 정보를 포함 합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct _tagSYMBOL_SEARCH_INFO
{
    SYMBOL_SEARCH_INFO_FIELDS dwValidFields;
    BSTR                      bstrVerboseSearchInfo;
} MODULE_SYMBOL_SEARCH_INFO;
```

```csharp
public struct MODULE_SYMBOL_SEARCH_INFO {
    public uint   dwValidFields;
    public string bstrVerboseSearchInfo;
}
```

## <a name="members"></a>멤버

`dwValidFields`\
플래그의 조합 된 [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) 이 구조에서 설명한 검색 정보의 종류를 지정 하는 열거형입니다.

`bstrVerboseSearchInfo`\
검색 경로 및 단일 문자열로 연결 하는 결과입니다.

## <a name="remarks"></a>설명

이 구조에 대 한 호출에서 반환 되는 [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) 메서드.

경우는 `bstrVerboseSearchInfo` 필드가 비어 있지 않으면 다음 검색 경로 및 해당 검색 결과의 목록을 포함 합니다. 목록 결과 뒤에 ("..."), 줄임표 뒤에 경로 형식은입니다. 둘 이상의 경로 결과 쌍의 경우 각 쌍은 "\r\n" (캐리지 리턴/줄 바꿈) 쌍으로 구분 됩니다. 패턴은 다음과 같습니다.

\<path>...\<result>\r\n\<path>...\<result>\r\n\<path>...\<result>

마지막 항목 \r\n 순서 없는 참고 합니다.

다음은 가능한 `bstrVerboseSearchInfo` 를 표준 출력으로 전송 된 문자열입니다.

`c:\symbols\user32.pdb... File not found.`

`c:\winnt\symbols\user32.pdb... Version does not match.`

`\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`

## <a name="requirements"></a>요구 사항

헤더: msdbg.h

네임스페이스: Microsoft.VisualStudio.Debugger.Interop

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료

- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)