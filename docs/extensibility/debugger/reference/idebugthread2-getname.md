---
title: IDebugThread2::GetName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetName
helpviewer_keywords:
- IDebugThread2::GetName
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d6b57aac800027a4a591c3ea683761e19a31462c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66320221"
---
# <a name="idebugthread2getname"></a>IDebugThread2::GetName
스레드의 이름을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetName ( 
   BSTR* pbstrName
);
```

```csharp
int GetName ( 
   out string pbstrName
);
```

## <a name="parameters"></a>매개 변수
`pbstrName`\
[out] 스레드의 이름을 반환합니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 검색 이름은 항상 표시 될 수 있는 이름 및 스레드 하는이 이름에 설명 합니다. 스레드 이름 명명 된 스레드를 지원 하거나 디버그 엔진에서 파생 된 이름 수 있습니다는 런타임 아키텍처를에서 파생 될 수 있습니다. 호출 하 여 스레드의 이름을 설정할 수 있습니다 또는 합니다 [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md) 메서드.

## <a name="see-also"></a>참고자료
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)