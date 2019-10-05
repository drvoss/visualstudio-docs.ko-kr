---
title: IDebugProgramProvider2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2
helpviewer_keywords:
- IDebugProgramProvider2 interface
ms.assetid: a9ec7b3e-a59c-4069-b2ee-6f45916eeb78
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6f392e823d28440a73a1aaa606351c28c6e9c70
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343353"
---
# <a name="idebugprogramprovider2"></a>IDebugProgramProvider2
이 등록된 인터페이스를 사용 하면 세션 디버그 관리자 (SDM)가 "게시"를 통해 프로그램에 대 한 정보를 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md) 인터페이스입니다.

## <a name="syntax"></a>구문

```
IDebugProgramProvider2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
디버그 엔진 (DE) 디버깅 중인 프로그램에 대 한 정보를 제공 하려면이 인터페이스를 구현 합니다. 이 인터페이스는 메트릭을 사용 하 여 레지스트리 DE 섹션에 등록 되어 `metricProgramProvider`에 설명 된 대로 [디버깅을 위한 SDK 도우미](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)합니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
COM의 호출 `CoCreateInstance` 함수는 `CLSID` 레지스트리에서 가져온 프로그램 공급자의입니다. 예제를 참조 하세요.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드

|메서드|설명|
|------------|-----------------|
|[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)|프로그램 실행, 다양 한 방법으로 필터링 하는 방법에 대 한 정보를 얻습니다.|
|[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)|노드를 가져옵니다. 프로그램에는 특정 프로세스 ID를 지정 합니다.|
|[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)|특정 유형의 프로세스와 관련 된 공급자 이벤트를 조사 하는 콜백을 설정 합니다.|
|[SetLocale](../../../extensibility/debugger/reference/idebugprogramprovider2-setlocale.md)|DE에 필요한 모든 언어 관련 리소스에 대 한 로캘을 설정 합니다.|

## <a name="remarks"></a>설명
일반적으로 프로세스는 해당 프로세스에서 실행 중인 프로그램에 자세히 알아보려면이 인터페이스를 사용 합니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: Microsoft.VisualStudio.Debugger.Interop

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>예제

```cpp
IDebugProgramProvider2 *GetProgramProvider(GUID *pDebugEngineGuid)
{
    // This is typically defined globally. For this example, it is
    // defined here.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";
    IDebugProgramProvider2 *pProvider = NULL;
    if (pDebugEngineGuid != NULL) {
        CLSID clsidProvider = { 0 };
        ::GetMetric(NULL,
                    metrictypeEngine,
                    *pDebugEngineGuid,
                    metricProgramProvider,
                    &clsidProvider,
                    strRegistrationRoot);
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {
            CComPtr<IDebugProgramProvider2> spProgramProvider;
            spProgramProvider.CoCreateInstance(clsidProvider);
            if (spProgramProvider != NULL) {
                pProvider = spProgramProvider.Detach();
            }
        }
    }
    return(pProvider);
}
```

## <a name="see-also"></a>참고자료
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [디버깅을 위한 SDK 도우미](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
