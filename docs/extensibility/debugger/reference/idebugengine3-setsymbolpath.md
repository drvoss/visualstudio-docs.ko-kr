---
title: IDebugEngine3::SetSymbolPath | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: da2318e9e2e30ea4cf0dce4bef6abd03aef2b0d0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352467"
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
디버깅 기호가 검색 하는 경로 경로 설정 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetSymbolPath (
   LPOLESTR            szSymbolSearchPath,
   LPOLESTR            szSymbolCachePath,
   LOAD_SYMBOLS_FLAGS  Flags
);
```

```csharp
int SetSymbolPath(
   string                    szSymbolSearchPath,
   string                    szSymbolCachePath,
   enum_LOAD_SYMBOLS_FLAGS   Flags
);
```

## <a name="parameters"></a>매개 변수

`szSymbolSearchPath`\
[in] 기호 검색 경로 또는 경로 포함 하는 문자열입니다. 자세한 내용은 "주의"를 참조 하십시오. null일 수 없습니다.

`szSymbolCachePath`\
[in] 기호를 캐시할 수 있는 로컬 경로 포함 하는 문자열입니다. null일 수 없습니다.

`Flags`\
[in] 사용 되지 않습니다. 항상 0으로 설정 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK를 반환 합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 문자열 `szSymbolSearchPath` 은 하나 이상의 경로, 기호를 검색할 세미콜론으로 구분 된 목록입니다. 이러한 경로 로컬 경로, 스타일 UNC 경로 또는 URL 수 있습니다. 이러한 경로 서로 다른 유형의 혼합 될 수도 있습니다. 경로가 UNC 경로인 경우 (예를 들어 \\\Symserver\Symbols), 경로 기호 서버에 이며 지정 된 경로에서 캐시 하는 서버에서 기호를 로드할 수 있어야 하는 경우 디버그 엔진을 결정 하는 다음 `szSymbolCachePath`합니다.

 기호 경로는 캐시 위치를 하나 이상 포함할 수도 있습니다. 캐시를 먼저 가장 높은 우선 순위 캐시를 사용 하 여 우선 순위 순서로 나열 되 고 구분 하 여 * 기호. 예를 들어:

```
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*http://msdl.microsoft.com
```

 합니다 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) 메서드 기호의 실제 로드를 수행 합니다.

## <a name="see-also"></a>참고자료
- [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)