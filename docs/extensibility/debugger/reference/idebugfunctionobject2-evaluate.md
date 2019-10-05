---
title: IDebugFunctionObject2::Evaluate | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::Evaluate
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a830dadd9d24f5ecb815db5a89342c5acd281a9c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313402"
---
# <a name="idebugfunctionobject2evaluate"></a>IDebugFunctionObject2::Evaluate
함수를 호출 하 고 결과 개체 값을 반환 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Evaluate (
   IDebugObject** ppParams,
   DWORD          dwParams,
   DWORD          dwEvalFlags,
   DWORD          dwTimeout,
   IDebugObject** ppResult
);
```

```csharp
int Evaluate (
   IDebugObject     ppParams,
   uint             dwParams,
   uint             dwEvalFlags,
   uint             dwTimeout,
   out IDebugObject ppResult
);
```

## <a name="parameters"></a>매개 변수
`ppParams`\
[in] 배열을 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 입력된 매개 변수를 나타내는 개체입니다. 이러한 각 매개이 변수에이 인터페이스에서 만들기 방법 중 하나를 사용 하 여 만들어졌습니다.

`dwParams`\
[in] 매개 변수 개수는 `ppParams` 배열입니다.

`dwEvalFlags`\
[in] 플래그의 조합을 합니다 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) 평가 수행 하는 방법을 지정 하는 열거형입니다.

`dwTimeout`\
[in] 이 메서드에서 반환 되기 전에 대기할 밀리초 단위로 최대 시간을 지정 합니다. 사용 하 여 **무한** 무기한 대기 합니다.

`ppResult`\
[out] 반환 된 **IDebugObject** 개체로 함수의 값을 나타내는입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="see-also"></a>참고자료
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)