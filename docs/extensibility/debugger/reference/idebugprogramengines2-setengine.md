---
title: IDebugProgramEngines2::SetEngine | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::SetEngine
helpviewer_keywords:
- IDebugProgramEngines2::SetEngine
ms.assetid: c05857ee-89cf-455e-8f1e-300cce4a2eab
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1a8c48de1a068300bb514d10528592cc518004db
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343443"
---
# <a name="idebugprogramengines2setengine"></a>IDebugProgramEngines2::SetEngine
프로그램 또는 프로그램 노드는 디버그 엔진 (DE)이이 프로그램을 디버깅 하는 데 알려 줍니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetEngine( 
   REFGUID guidEngine
);
```

```csharp
int SetEngine( 
   ref Guid guidEngine
);
```

## <a name="parameters"></a>매개 변수
`guidEngine`\
[in] GUID는 DE입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="see-also"></a>참고자료
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)