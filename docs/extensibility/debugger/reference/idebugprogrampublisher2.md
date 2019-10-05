---
title: IDebugProgramPublisher2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2
helpviewer_keywords:
- IDebugProgramPublisher2 interface
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f94e7ea830a49db5b95bae3d0d6c50f73e6d3d64
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343129"
---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
이 인터페이스에는 디버그 엔진 (DE) 또는 디버깅에 대 한 프로그램을 등록 하려면 사용자 지정 포트 공급자 수 있습니다.

## <a name="syntax"></a>구문

```
IDebugProgramPublisher2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
Visual Studio는 여러 프로세스에서 디버깅을 위해 표시 되 게 하려면 디버깅 중인 프로그램을 등록 하려면이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
COM의 호출 `CoCreateInstance` 함수와 `CLSID_ProgramPublisher` 가져오려면이 인터페이스 (예제 참조). DE 또는 사용자 지정 포트 공급자 디버깅 중인 프로그램을 나타내는 프로그램 노드를 등록 하려면이 인터페이스를 사용 합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
이 인터페이스는 다음 메서드를 구현 합니다.

|메서드|설명|
|------------|-----------------|
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|프로그램 노드를 사용할 수 있게 DEs 및 세션 디버그 관리자 (SDM).|
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|더 이상 사용할 수 있도록 프로그램 노드를 제거 합니다.|
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|사용 하면 프로그램이 사용 가능한 DEs SDM을 합니다.|
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|더 이상 사용할 수 있도록 프로그램을 제거 합니다.|
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|디버거 있는지를 나타내는 플래그를 설정 합니다.|

## <a name="remarks"></a>설명
이 인터페이스를 사용 하면 프로그램 및 프로그램 노드에 사용할 수 있습니다 (즉, "게시" 하) DEs 및 세션 디버그 관리자 SDM ()를 사용 합니다. 게시 된 프로그램 및 프로그램 노드에 액세스 하려면 사용 합니다 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) 인터페이스입니다. 이 유일한 방법은 Visual Studio 프로그램이 디버깅 되는 인식할 수 있습니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: Microsoft.VisualStudio.Debugger.Interop

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>예제
이 예제 프로그램 게시자를 인스턴스화하고 프로그램 노드를 등록 하는 방법을 보여 줍니다. 이 자습서에서 가져온 것 [프로그램 노드 게시](https://msdn.microsoft.com/library/d0100e02-4e2b-4e72-9e90-f7bc11777bae)합니다.

```cpp
// This is how m_srpProgramPublisher is defined in the class definition:
// CComPtr<IDebugProgramPublisher2> m_srpProgramPublisher.

void CProgram::Start(IDebugEngine2 * pEngine)
{
    m_spEngine = pEngine;

    HRESULT hr = m_srpProgramPublisher.CoCreateInstance(CLSID_ProgramPublisher);
    if ( FAILED(hr) )
    {
        ATLTRACE("Failed to create the program publisher: 0x%x.", hr);
        return;
    }

    // Register ourselves with the program publisher. Note that
    // CProgram implements the IDebgProgramNode2 interface, hence
    // the static cast on "this".
    hr = m_srpProgramPublisher->PublishProgramNode(
        static_cast<IDebugProgramNode2*>(this));
    if ( FAILED(hr) )
    {
        ATLTRACE("Failed to publish the program node: 0x%x.", hr);
        m_srpProgramPublisher.Release();
        return;
    }

    ATLTRACE("Added program node.\n");
}
```

## <a name="see-also"></a>참고자료
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
