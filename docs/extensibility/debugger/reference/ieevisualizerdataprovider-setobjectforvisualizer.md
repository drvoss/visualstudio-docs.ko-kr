---
title: IEEVisualizerDataProvider::SetObjectForVisualizer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 34fb0e8c4ae8b2b4371234e9cf09d9c21727dfdf
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350193"
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
이 메서드는 시각화 도우미를 나타내는 개체를 변경 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetObjectForVisualizer(
   IDebugObject*  pNewObject,
   BSTR*          error,
   IDebugObject** pException
);
```

```csharp
int SetObjectForVisualizer(
   IDebugObject     pNewObject,
   out string       error,
   out IDebugObject pException
);
```

## <a name="parameters"></a>매개 변수
`pNewObject`\
[in] 개체 집합입니다.

`error`\
[out] 개체를 설정할 때 오류가 발생에 발생 한 경우이 문자열 오류 메시지를 보유 합니다.

`pException`\
[out] 오류가 있는 경우이 개체는 예외 정보를 보유 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 오류 정보 반환 하는 방법을 확인 하려면 구현자는 것입니다. 그러나 것을 알고 있는 예외 개체 반환 된 경우 오류가 발생할 경우이 메서드는 예외 개체를 항상 반환 해야 하므로 오류가 발생 했습니다 일부 호출자 수는 가능 합니다. 오류 문자열을 호출자에 게 확인 하려고 하는 경우에 제공 해야 사용 합니다.

## <a name="see-also"></a>참고자료
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)