---
title: IDebugModule2::ReloadSymbols_Deprecated | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2::ReloadSymbols
helpviewer_keywords:
- IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 635e305c0dd88d72017048da6353f813fcc46406
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323954"
---
# <a name="idebugmodule2reloadsymbolsdeprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
사용되지 않습니다. 사용 하지 마세요. 이 모듈의 기호를 다시 로드합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT ReloadSymbols( 
   LPCOLESTR pszUrlToSymbols,
   BSTR*     pbstrDebugMessage
);
```

```csharp
int ReloadSymbols( 
   string     pszUrlToSymbols,
   out string pbstrDebugMessage
);
```

## <a name="parameters"></a>매개 변수
`pszUrlToSymbols`\
[in] 기호 저장소에 대 한 경로입니다.

`pbstrDebugMessage`\
[out] 모듈 창에서 모듈 이름 오른쪽에 표시 되는 상태 또는 오류 메시지와 같은 정보 메시지를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다. 디버그 엔진을 항상 반환 `E_FAIL`합니다.

## <a name="remarks"></a>설명
 이 메서드는 더 이상 지원 합니다. 구현 된 [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md) 메서드 대신 합니다.

## <a name="see-also"></a>참고자료
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)