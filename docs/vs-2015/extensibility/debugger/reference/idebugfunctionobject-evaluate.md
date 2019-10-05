---
title: IDebugFunctionObject::Evaluate | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::Evaluate
helpviewer_keywords:
- IDebugFunctionObject::Evaluate method
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e19baa193bb015056b9e5abde4c7a274f635c0c8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68179419"
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

#### <a name="parameters"></a>매개 변수
 `ppParams`

 [in] 배열을 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 입력된 매개 변수를 나타내는 개체입니다. 중 하나를 사용 하 여 만든 각 매개이 변수에 `Create` 의 메서드를 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 인터페이스입니다.

 `dwParams`

 [in] 매개 변수 개수는 `ppParams` 배열입니다.

 `dwTimeout`

 [in] 이 메서드에서 반환 되기 전에 대기할 밀리초 단위로 최대 시간을 지정 합니다. 사용 하 여 `INFINITE` 무기한 대기 합니다.

 `ppResult`

 [out] 반환 된 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 개체로 함수의 값을 나타내는입니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK를 반환 합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드를 나타내는 함수 호출을 실행 합니다 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 개체입니다.

## <a name="see-also"></a>참고 항목
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)