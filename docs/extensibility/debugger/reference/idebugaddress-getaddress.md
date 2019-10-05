---
title: IDebugAddress::GetAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f787f041c6c39b8120a768f9288efe86649bb227
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318001"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
개체 및 해당 범위 또는 컨테이너 내에서 해당 위치를 설명 하는 구조체를 반환 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetAddress (
   DEBUG_ADDRESS * pAddress
);
```

```csharp
int GetAddress(
   DEBUG_ADDRESS[] pAddress
);
```

## <a name="parameters"></a>매개 변수
`pAddress`\
[out에서] A [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 구조는이 메서드에 의해 채워집니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK를 반환 합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 합니다 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 구조는 다음 적절 한 정보로 채우는이 메서드에 전달 됩니다. 이 정보를 해석 하는 방법을 반환 되는 정보 및 자체 기호 처리기의 종류에 따라 달라 집니다. 참조 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 대 한 자세한 내용은 합니다.

## <a name="see-also"></a>참고자료
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)