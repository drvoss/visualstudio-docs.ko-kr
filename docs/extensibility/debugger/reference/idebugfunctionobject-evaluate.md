---
title: IDebugFunctionObject::Evaluate | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::Evaluate
helpviewer_keywords:
- IDebugFunctionObject::Evaluate method
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a3d9ddafe744c2815e3730cd835fb1afe63ffc23
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313502"
---
# <a name="idebugfunctionobjectevaluate"></a>IDebugFunctionObject::Evaluate
함수를 호출 하 고 결과 개체 값을 반환 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Evaluate( 
   IDebugObject** ppParams,
   DWORD          dwParams,
   DWORD          dwTimeout,
   IDebugObject** ppResult
);
```

```csharp
int Evaluate(
   IDebugObject[]   ppParams,
   IntPtr           dwParams,
   uint             dwTimeout,
   out IDebugObject ppResult
);
```

## <a name="parameters"></a>매개 변수
`ppParams`\
[in] 배열을 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 입력된 매개 변수를 나타내는 개체입니다. 중 하나를 사용 하 여 만든 각 매개이 변수에 `Create` 의 메서드를 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 인터페이스입니다.

`dwParams`\
[in] 매개 변수 개수는 `ppParams` 배열입니다.

`dwTimeout`\
[in] 이 메서드에서 반환 되기 전에 대기할 밀리초 단위로 최대 시간을 지정 합니다. 사용 하 여 `INFINITE` 무기한 대기 합니다.

`ppResult`\
[out] 반환 된 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 개체로 함수의 값을 나타내는입니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK를 반환 합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드를 나타내는 함수 호출을 실행 합니다 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 개체입니다.

## <a name="see-also"></a>참고자료
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)