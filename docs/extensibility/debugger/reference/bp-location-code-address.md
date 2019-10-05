---
title: BP_LOCATION_CODE_ADDRESS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_ADDRESS
helpviewer_keywords:
- BP_LOCATION_CODE_ADDRESS structure
ms.assetid: 83c9da8b-19d9-4be5-b225-854543654901
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 51137b5a5a69c80ecd7129d4c645f63b5805d27d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319126"
---
# <a name="bplocationcodeaddress"></a>BP_LOCATION_CODE_ADDRESS
코드에서 주소 중단점의 위치를 설명 합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct _BP_LOCATION_CODE_ADDRESS {
    BSTR bstrContext;
    BSTR bstrModuleUrl;
    BSTR bstrFunction;
    BSTR bstrAddress;
} BP_LOCATION_CODE_ADDRESS;
```

## <a name="members"></a>멤버
`bstrContext`\
중단점의 컨텍스트에서, 일반적으로 호출 스택에 표시 된 메서드 또는 함수의 이름입니다.

`bstrModuleUrl`\
중단점이 포함 된 모듈의 URL입니다.

`bstrFunction`\
중단점이 포함 된 함수의 이름입니다.

`bstrAddress`\
주소에 바인딩하는 식 계산기에서 구문을 분석 하는 중단점을를 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 개체입니다.

## <a name="remarks"></a>설명
이 구조체의 멤버인 합니다 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) 공용 구조체의 일부로 구조입니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: Microsoft.VisualStudio.Debugger.Interop

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
