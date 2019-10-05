---
title: IDebugBinder3::FindAlias | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8387a3302395d6e25c2b00dd360286e533531168
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344417"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
이 메서드는 이름이 지정 된 별칭을 찾습니다. 이 프로그램에서 모든 별칭을 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT FindAlias(
   LPCOLESTR     pcstrName,
   IDebugAlias** ppAlias
);
```

```csharp
int FindAlias(
   string          pcstrName,
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>매개 변수
`pcstrName`\
[in] 검색할 별칭의 이름입니다.

`ppAlias`\
[out] 별칭이 (있는 경우)를 검색 하 여 표시 합니다 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) 인터페이스입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`이 고, 그렇지 않으면 반환 `S_FALSE` (별칭 없는 경우) 또는 오류 코드입니다.

## <a name="remarks"></a>설명
 이 메서드를; 호출 하기 전에 null 대상 개체를 초기화합니다. 그런 다음 별칭을 찾을 수 있는지 여부를 확인 하려면 나중에 null 값을 테스트 합니다.

## <a name="see-also"></a>참고자료
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)