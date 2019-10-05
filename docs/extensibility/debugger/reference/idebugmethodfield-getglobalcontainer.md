---
title: IDebugMethodField::GetGlobalContainer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetGlobalContainer
helpviewer_keywords:
- IDebugMethodField::GetGlobalContainer method
ms.assetid: 041ac5aa-0b80-4310-b9ae-b88f8e7e0e5f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 77f3d82beab43b227dd3beb772dd41353d89b6fe
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324182"
---
# <a name="idebugmethodfieldgetglobalcontainer"></a>IDebugMethodField::GetGlobalContainer
메서드의 전역 컨테이너를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetGlobalContainer(
   IDebugClassField** ppClass
);
```

```csharp
int GetGlobalContainer(
   out IDebugClassField ppClass
);
```

## <a name="parameters"></a>매개 변수
`ppClass`\
[out] 반환 된 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) 이 메서드가 정의 되어 있는 모듈을 나타내는입니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK를 반환 합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 반환 된 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) 개체는 전체 모듈 나타내며 인위적인 개체, 즉, 모듈 자체는 실제 클래스 없지만로 나타낼 수 있습니다는 `IDebugClassField` 허용 하는 다양 한 개체 열거 하 고 발견 된 모듈의 요소입니다.

## <a name="see-also"></a>참고자료
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)