---
title: IDebugCodeContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59573736ca3cd0768d3383e5621d96dffdea9746
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338895"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
이 인터페이스는 코드 명령의 시작 위치를 나타냅니다. 대부분의 런타임 아키텍처에 대 한 현재 코드 컨텍스트를 생각할 수 있습니다 프로그램의 실행 스트림에 주소로 합니다.

## <a name="syntax"></a>구문

```
IDebugCodeContext2 : IDebugMemoryContext2
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 디버그 엔진 문서 위치에 코드 명령의 위치를 연결 하려면이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 여러 인터페이스에서 메서드 가장 일반적으로이 인터페이스를 반환 합니다 [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)합니다. 도 함께 사용 하는 광범위 하 게 합니다 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) 중단점 확인 정보와 같이 인터페이스입니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 메서드 외에도 합니다 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 인터페이스에서이 인터페이스는 다음 메서드를 구현 합니다.

|메서드|설명|
|------------|-----------------|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|활성 코드 컨텍스트에 해당 하는 문서 컨텍스트를 가져옵니다.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|이 코드 컨텍스트에 대 한 언어 정보를 가져옵니다.|

## <a name="remarks"></a>설명
 주요 차이점을 `IDebugCodeContext2` 인터페이스 및 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 인터페이스는는 `IDebugCodeContext2` 항상 명령-맞춰집니다. 즉를 `IDebugCodeContext2` 반면, 명령의 시작 부분에 항상 가리키는 `IDebugMemoryContext2` 런타임 아키텍처에서 메모리의 모든 바이트를 가리킬 수 있습니다. `IDebugCodeContext2` 기본 저장소 크기 (일반적으로 바이트) 하는 대신 지침에 따라 증가 합니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)
- [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)
- [다음](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)