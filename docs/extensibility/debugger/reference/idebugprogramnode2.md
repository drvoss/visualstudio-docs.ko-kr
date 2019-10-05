---
title: IDebugProgramNode2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2
helpviewer_keywords:
- IDebugProgramNode2 interface
ms.assetid: 80e511d8-9b40-4a85-aa5d-952fa5ee6ae7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6a48f660302d39c9cfa75503ac7ca4a8c526a7f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351076"
---
# <a name="idebugprogramnode2"></a>IDebugProgramNode2
이 인터페이스는 디버깅할 수 있는 프로그램을 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 디버그 엔진 (DE) 또는 사용자 지정 포트 공급 업체를 디버깅할 수 있는 프로그램을 나타내는이 인터페이스를 구현 합니다. 이 인터페이스를 구현 하는 동일한 개체에서 일반적으로 구현 됩니다 합니다 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 인터페이스입니다. 이 인터페이스는 등록 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 호출한 [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)합니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 호출 [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) 이 인터페이스를 반환 합니다. 사용자 지정 포트 공급자 호출을 통해이 인터페이스를 받는 [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)합니다. 호출을 통해이 인터페이스를 수신 하는 DE [연결](../../../extensibility/debugger/reference/idebugengine2-attach.md)합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서의 메서드를 보여 줍니다. `IDebugProgramNode2`합니다.

|메서드|설명|
|------------|-----------------|
|[GetProgramName](../../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)|프로그램의 이름을 가져옵니다.|
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)|프로그램을 호스팅하는 프로세스의 이름을 가져옵니다.|
|[GetHostPid](../../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)|프로그램을 호스트 하는 프로세스에 대 한 시스템 프로세스 식별자를 가져옵니다.|
|[GetHostMachineName_V7](../../../extensibility/debugger/reference/idebugprogramnode2-gethostmachinename-v7.md)|사용 되지 않습니다. 사용 하지 마세요.|
|[Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)|사용 되지 않습니다. 사용 하지 마세요. 참조 된 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) 다른 방법에 대 한 인터페이스입니다.|
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)|이름 및이 프로그램을 실행 하는 DE의 식별자를 가져옵니다.|
|[DetachDebugger_V7](../../../extensibility/debugger/reference/idebugprogramnode2-detachdebugger-v7.md)|사용 되지 않습니다. 사용 하지 마세요.|

## <a name="remarks"></a>설명
 일반적으로 세션 디버그 관리자 SDM ()를 호출 [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) 이 인터페이스를 가져올 수 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: Msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
- [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)
- [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)