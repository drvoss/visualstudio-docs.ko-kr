---
title: IDebugEngine2::SetException | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetException
helpviewer_keywords:
- IDebugEngine2::SetException
ms.assetid: e6f5ec48-09e8-4b9b-9dc9-55f8d883f1b7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2234c0c0b571e763d3b143b5606fe61c43f25cde
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352539"
---
# <a name="idebugengine2setexception"></a>IDebugEngine2::SetException
디버그 엔진 (DE) 지정 된 예외를 처리 하는 방법을 지정 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetException( 
   EXCEPTION_INFO* pException
);
```

```csharp
int SetException( 
   EXCEPTION_INFO[] pException
);
```

## <a name="parameters"></a>매개 변수
`pException`\
[in] [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) 예외 및 디버깅 하는 방법을 설명 하는 구조입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 첫 번째 기회에 예외를 생성 하는 프로그램을 중지, 기회, 두 번째는 DE 지시할 수 있었습니다 또는 전혀 그렇지 않습니다.

## <a name="see-also"></a>참고자료
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)