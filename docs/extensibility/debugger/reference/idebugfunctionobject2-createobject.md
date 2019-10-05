---
title: IDebugFunctionObject2::CreateObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 87d1c2cd71b57136e26a2bc30004547dc4b8dee5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313419"
---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
평가 플래그 설정 및 제한 시간 값을 지정 하는 생성자를 사용 하는 개체를 만듭니다.

## <a name="syntax"></a>구문

```cpp
HRESULT CreateObject (
   IDebugFunctionObject* pConstructor,
   DWORD                 dwArgs,
   IDebugObject*         pArgs[],
   DWORD                 dwEvalFlags,
   DWORD                 dwTimeout,
   IDebugObject**        ppObject
);
```

```csharp
int CreateObject (
   IDebugFunctionObject pConstructor,
   uint                 dwArgs,
   IDebugObject[]       pArgs,
   uint                 dwEvalFlags,
   uint                 dwTimeout,
   out IDebugObject**   ppObject
);
```

## <a name="parameters"></a>매개 변수
`pConstructor`\
[in] [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 만들려는 개체의 생성자를 나타내는 개체입니다.

`dwArgs`\
[in] 매개 변수 개수는 `pArg` 배열입니다. 생성자에 전달 된 매개 변수의 수를 나타냅니다.

`pArgs`\
[in] 배열을 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 생성자에 전달 된 매개 변수를 나타내는 개체입니다.

`dwEvalFlags`\
[in] 플래그의 조합을 합니다 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) 평가 수행 하는 방법을 지정 하는 열거형입니다.

`dwTimeout`\
[in] 이 메서드에서 반환 되기 전에 대기할 밀리초에서는 최대 시간입니다. 사용 하 여 **무한** 무기한 대기 합니다.

`ppObject`\
[out] 반환 된 **IDebugObject** 새로 만든된 개체를 나타내는입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 클래스 또는 생성자는 매개 변수는 필요한 다른 복합 형식의 인스턴스를 나타내는 개체를 만들려면이 메서드를 호출 합니다.

## <a name="see-also"></a>참고자료
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)