---
title: IDebugProperty2::SetValueAsReference | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsReference
helpviewer_keywords:
- IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f9e98465f16f58f734ef6fd58b66494b4aaf0b65
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66314616"
---
# <a name="idebugproperty2setvalueasreference"></a>IDebugProperty2::SetValueAsReference
지정한 참조의 값이 속성의 값을 설정 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetValueAsReference(
   IDebugReference2** rgpArgs,
   DWORD              dwArgCount,
   IDebugReference2*  pValue,
   DWORD              dwTimeout
);
```

```csharp
int SetValueAsReference(
   IDebugReference2[] rgpArgs,
   uint               dwArgCount,
   IDebugReference2   pValue,
   uint               dwTimeout
);
```

## <a name="parameters"></a>매개 변수
`rgpArgs`\
[in] 관리 되는 코드 속성 setter에 전달할 인수 배열입니다. 속성 setter 인수를 사용 하지 않는 경우 또는 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 개체는 이러한 속성 setter를 나타내지 않습니다 `rgpArgs` null 값 이어야 합니다. 이 매개 변수는 일반적으로 null 값입니다.

`dwArgCount`\
[in] 인수 개수는 `rgpArgs` 배열입니다.

`pValue`\
[in] 형식의 참조는 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 개체를 사용 하 여이 속성을 설정할 값입니다.

`dwTimeout`\
[in] 기간 밀리초에서 값을 설정 하는 데 있습니다. 일반적인 값은 `INFINITE`합니다. 이 가능한 모든 계산을 사용할 수 있는 시간에 영향을 줍니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`; 그렇지 않으면 오류 반환 코드, 일반적으로 다음 중 하나:

|Error|설명|
|-----------|-----------------|
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|참조에서 값을 설정 하는 것은 지원 되지 않습니다.|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|이 속성 메서드를 참조 하는 대로 값을 설정할 수 없습니다.|
|`E_SETVALUE_VALUE_IS_READONLY`|값을 읽기 전용 이며 설정할 수 없습니다.|
|`E_NOTIMPL`|메서드가 구현 되지 않았습니다.|

## <a name="see-also"></a>참고자료
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)