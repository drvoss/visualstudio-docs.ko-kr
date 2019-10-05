---
title: IDebugProgramProvider2::GetProviderProcessData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProcessData
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProcessData
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bee54c3876c2de1be0754a74b429e6d24b80b738
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325021"
---
# <a name="idebugprogramprovider2getproviderprocessdata"></a>IDebugProgramProvider2::GetProviderProcessData
지정된 된 프로세스에서 실행 중인 프로그램의 목록을 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetProviderProcessData(
   PROVIDER_FLAGS         Flags,
   IDebugDefaultPort2*    pPort,
   AD_PROCESS_ID          processId,
   CONST_GUID_ARRAY       EngineFilter,
   PROVIDER_PROCESS_DATA* pProcess
);
```

```csharp
int GetProviderProcessData(
   enum_PROVIDER_FLAGS     Flags,
   IDebugDefaultPort2      pPort,
   AD_PROCESS_ID           ProcessId,
   CONST_GUID_ARRAY        EngineFilter,
   PROVIDER_PROCESS_DATA[] pProcess
);
```

## <a name="parameters"></a>매개 변수
`Flags`\
[in] 플래그의 조합 된 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) 열거형입니다. 이 호출에 대 한 일반 플래그는 다음과 같습니다.

|플래그|설명|
|----------|-----------------|
|`PFLAG_REMOTE_PORT`|호출자에 게 원격 컴퓨터에서 실행 됩니다.|
|`PFLAG_DEBUGGEE`|호출자에 게 현재 디버깅 중인 (마샬링 하는 방법에 대 한 자세한 내용은 각 노드에 대해 반환 됩니다).|
|`PFLAG_ATTACHED_TO_DEBUGGEE`|호출자에 연결 되었지만 디버거에서 실행 되지 않습니다.|
|`PFLAG_GET_PROGRAM_NODES`|프로그램 노드 목록을 반환할를 호출자에 게 요청 합니다.|

`pPort`\
[in] 포트는 호출 프로세스에서 실행 됩니다.

`processId`\
[in] [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) 구조에서 해당 프로그램을 포함 하는 프로세스의 ID를 보유 합니다.

`EngineFilter`\
[in] \(이러한 됩니다 필터링에 사용 될 모든 프로그램 반환 됩니다 엔진이 없습니다 지정 된 경우 제공 된 엔진; 지원 되는 내용에 따라 프로그램 실제로 반환 되는)이이 프로세스를 디버깅 하려면 할당 된 디버그 엔진에 대 한 Guid의 배열입니다.

`pProcess`\
[out] A [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) 구조에 필요한 정보를 사용 하 여 입력 됩니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 이 메서드는 일반적으로 해당 프로세스에서 실행 되는 프로그램의 목록을 가져오려면 프로세스에 의해 호출 됩니다. 반환 된 정보는 목록이 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 개체입니다.

## <a name="see-also"></a>참고자료
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)