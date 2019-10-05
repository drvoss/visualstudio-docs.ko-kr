---
title: IDebugProgram2::GetENCUpdate | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetENCUpdate
helpviewer_keywords:
- IDebugProgram2::GetENCUpdate
ms.assetid: 9832aac8-6320-4fd8-91dd-2a0852febb00
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: eb92e7076c308663ddf9ec760d1f2276affd0c87
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66320844"
---
# <a name="idebugprogram2getencupdate"></a>IDebugProgram2::GetENCUpdate
이 메서드는이 프로그램에 대 한 편집 및 계속 (ENC) 업데이트를 가져옵니다. 사용자 지정 디버그 엔진을 항상 반환 `E_NOTIMPL`합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetENCUpdate( 
   IUnknown** ppUpdate
);
```

```csharp
int GetENCUpdate(
   out object ppUpdate
);
```

## <a name="parameters"></a>매개 변수
`ppUpdate`\
[out] 이 프로그램을 업데이트 하는 내부 인터페이스를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

> [!NOTE]
> 사용자 지정 디버그 엔진을 항상 반환 `E_NOTIMPL`합니다.

## <a name="see-also"></a>참고자료
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)