---
title: IDebugStackFrame2::GetPhysicalStackRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2cf0db9fa776116f1536ae137444160385a8b6a1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347708"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
스택 프레임과 연결 된 물리적 주소 범위의 컴퓨터 종속 표현을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetPhysicalStackRange ( 
   UINT64* paddrMin,
   UINT64* paddrMax
);
```

```csharp
int GetPhysicalStackRange ( 
   out ulong paddrMin,
   out ulong paddrMax
);
```

## <a name="parameters"></a>매개 변수
`paddrMin`\
[out] 이 스택 프레임과 연결 된 가장 낮은 물리적 주소를 반환 합니다.

`paddrMax`\
[out] 이 스택 프레임과 연결 된 가장 높은 물리적 주소를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 이 메서드에서 반환 되는 정보는 스택 프레임을 정렬 하려면 세션 디버그 관리자 SDM ()가 사용 됩니다.

 호출 스택, 즉 증가, 점점 더 낮은 메모리 주소를 새 스택 프레임 추가 되어 있는지 간주 됩니다. 런타임 아키텍처는이 가정을 일치 하는 실제 스택에 범위를 제공 해야 합니다.

## <a name="see-also"></a>참고자료
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)