---
title: IDebugProcessEx2::AddImplicitProgramNodes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b75ef50107b44de8de6f65c5c4c9c6827e13426e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309496"
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
이 메서드는 지정 된 각 디버그 엔진 (DE)에 대 한 프로그램 노드를 추가 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT AddImplicitProgramNodes(
   REFGUID guidLaunchingEngine,
   GUID*   rgguidSpecificEngines,
   DWORD   celtSpecificEngines
);
```

```csharp
int AddImplicitProgramNodes(
   ref Guid guidLaunchingEngine,
   Guid[]   rgguidSpecificEngines,
   uint     celtSpecificEngines
);
```

## <a name="parameters"></a>매개 변수
`guidLaunchingEngine`\
[in] `GUID` 프로그램을 시작 하는 데는 (및 자체 프로그램 노드를 추가 하려면 가정)는 DE입니다.

`rgguidSpecificEngines`\
[in] 배열을 `GUID`의프로그램에 대 한 노드를 추가할 수는 DEs입니다.

`celtSpecificEngines`\
[in] 수가 `GUID`의 `rgguidSpecificEngines` 배열입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
- [노드 프로그램](../../../extensibility/debugger/program-nodes.md) 에 나열 된 각 DE 예정 `rgguidSpecificEngines`-시작 엔진 제외 하 고 (에 지정 된 대로 `guidLaunchingEngine`), 프로그램을 시작할 때 자체 프로그램 노드를 추가 하려면 가정 된 합니다.

## <a name="see-also"></a>참고자료
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
- [프로그램 노드](../../../extensibility/debugger/program-nodes.md)