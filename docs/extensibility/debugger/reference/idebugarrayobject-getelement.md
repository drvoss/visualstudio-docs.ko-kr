---
title: IDebugArrayObject::GetElement | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 527302a2e6d6fc2884107e3773402adc56b881c7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322214"
---
# <a name="idebugarrayobjectgetelement"></a>IDebugArrayObject::GetElement
배열의 요소를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetElement( 
   DWORD          dwIndex,
   IDebugObject** ppElement
);
```

```csharp
int GetElement(
   [In] uint dwIndex,
   out IDebugObject ppElement
);
```

## <a name="parameters"></a>매개 변수
`dwIndex`\
[in] 요소의 인덱스입니다.

`ppElement`\
[out] 반환 된 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 요소를 나타내는 인터페이스입니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK를 반환 합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드는 배열 개체는 다차원 배열 하는 경우에 모든 배열 개체 요소의 1 차원 배열에으로 간주 합니다. 예를 들어, 배열의 지정 된 `myarray[3][2][6]` 및 `dwIndex` 20의 매개 변수를이 메서드는 반환 요소 `myarray[1][1][2]`, 및 `dwIndex` 21의 매개 변수에서 요소 반환 `myarray[1][1][3]`합니다. 사용 된 [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) 배열에 있는 요소의 총 수를 확인 하는 방법입니다.

## <a name="see-also"></a>참고자료
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)