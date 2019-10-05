---
title: IDebugDocumentContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2
helpviewer_keywords:
- IDebugDocumentContext2
ms.assetid: 2a446c71-8100-4c09-a1cc-fd446bd74030
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe54a6d3e97fc40f915c42c4aa5397165416b073
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326634"
---
# <a name="idebugdocumentcontext2"></a>IDebugDocumentContext2
이 인터페이스는 소스 파일 문서의 위치를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugDocumentContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 디버그 엔진 (DE) 소스 코드 수준 디버깅에 대 한 지원의 일부로이 인터페이스를 구현합니다. 소스 코드의 위치, 외에도이 인터페이스는 컨텍스트를 비교 하 고 소스 코드 문서를 탐색 하는 메서드를 제공 합니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 메서드를 여러 인터페이스를 가장 일반적으로 [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) 하 고 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) 인터페이스는이 인터페이스를 반환 합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서의 메서드를 보여 줍니다. `IDebugDocumentContext2`합니다.

|메서드|설명|
|------------|-----------------|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)|이 문서 컨텍스트를 포함 하는 문서를 가져옵니다.|
|[GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)|이 문서 컨텍스트를 포함 하는 문서의 표시할 수 있는 이름을 가져옵니다.|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)|이 문서 컨텍스트와 연결 된 모든 코드 컨텍스트 목록을 검색 합니다.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugdocumentcontext2-getlanguageinfo.md)|이 문서 컨텍스트와 연결 된 언어를 가져옵니다.|
|[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|이 문서 컨텍스트의 파일 문의 범위를 가져옵니다.|
|[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)|이 문서 컨텍스트의 파일 소스 범위를 가져옵니다.|
|[Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)|문서 컨텍스트를 지정 된 배열에이 문서 컨텍스트를 비교합니다.|
|[Seek](../../../extensibility/debugger/reference/idebugdocumentcontext2-seek.md)|문이나 줄의 지정된 된 수 만큼 문서 컨텍스트를 이동합니다.|

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)