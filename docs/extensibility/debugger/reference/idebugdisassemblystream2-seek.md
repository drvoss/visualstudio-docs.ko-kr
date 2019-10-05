---
title: IDebugDisassemblyStream2::Seek | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Seek
helpviewer_keywords:
- IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e97da5b4b65b18c9d4c745dea2cb5f0915862731
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310362"
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
디스어셈블리 스트림에 지정된 된 수의 지정 된 위치를 기준으로 지침 읽기 포인터를 이동합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Seek( 
   SEEK_START          dwSeekStart,
   IDebugCodeContext2* pCodeContext,
   UINT64              uCodeLocationId,
   INT64               iInstructions
);
```

```csharp
int Seek( 
   enum_SEEK_START    dwSeekStart,
   IDebugCodeContext2 pCodeContext,
   ulong              uCodeLocationId,
   long               iInstructions
);
```

## <a name="parameters"></a>매개 변수
`dwSeekStart`\
[in] 값을 [SEEK_START](../../../extensibility/debugger/reference/seek-start.md) 검색 프로세스를 시작 하려면 상대 위치를 지정 하는 열거형입니다.

`pCodeContext`\
[in] 합니다 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 기준으로 seek 연산에는 코드 컨텍스트를 나타내는 개체입니다. 경우에이 매개 변수는 `dwSeekStart`  =  `SEEK_START_CODECONTEXT`고, 그렇지 않으면이 매개 변수는 무시 되 고 null 값이 될 수 있습니다.

`uCodeLocationId`\
[in] 코드 위치 식별자를 기준으로 seek 연산입니다. 하는 경우이 매개 변수는 `dwSeekStart`  =  `SEEK_START_CODELOCID`고, 그렇지 않으면이 매개 변수는 무시 되 고 0으로 설정할 수 있습니다. 에 대 한 설명 섹션을 참조 합니다 [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) 코드 위치 식별자에 대 한 메서드.

`iInstructions`\
[in] 에 지정 된 위치를 기준으로 이동 하는 명령 수가 `dwSeekStart`합니다. 이 값은 뒤로 이동 하려면 음수일 수 있습니다.

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. 반환 `S_FALSE` 검색 위치입니다. 사용 가능한 명령의 시점 이후로 목록 되었으면 합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>설명
 목록의 시작 부분 앞에 seek 되었으면 읽기 위치 목록에서 첫 번째 명령으로 설정 됩니다. 참조를 위치로 목록 끝 이후에 읽기 위치 설정 됩니다 마지막 명령 목록에서.

## <a name="see-also"></a>참고자료
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)