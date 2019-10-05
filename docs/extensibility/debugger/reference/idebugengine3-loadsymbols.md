---
title: IDebugEngine3::LoadSymbols | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::LoadSymbols
helpviewer_keywords:
- IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 72c4fce5a7e8dd53093e21db2771d2176462e67c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352518"
---
# <a name="idebugengine3loadsymbols"></a>IDebugEngine3::LoadSymbols
이 디버깅 엔진으로 디버깅 중인 모든 모듈에 대 한 기호 (필요한 경우)으로 로드 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT LoadSymbols();
```

```csharp
int LoadSymbols();
```

## <a name="parameters"></a>매개 변수
 없음

## <a name="return-value"></a>반환 값
 성공 하면 S_OK를 반환 합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이이 디버깅 엔진에 의해 참조 되는 모든 모듈에 대 한 디버깅 기호를 로드 합니다. 기호는 이미 아직 로드 되지 않은 경우에 로드 됩니다. 기호를 호출 하 여 설정 경로에서 검색 됩니다 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)합니다.

## <a name="see-also"></a>참고자료
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)