---
title: IDebugDocumentPosition2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2
helpviewer_keywords:
- IDebugDocumentPosition2 interface
ms.assetid: 0e838ced-12bb-4efc-b811-2b7c034b77b0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 36c2fbce0154a5ebefd04ea3614d16db16799510
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333429"
---
# <a name="idebugdocumentposition2"></a>IDebugDocumentPosition2
이 인터페이스는 소스 파일에서 추상 위치를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugDocumentPosition2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 Visual Studio는 일반적으로이 인터페이스를 구현합니다. 디버그 엔진 (DE)는 자체 소스 코드를 제공 해야 하는 경우에이 인터페이스를 구현 (DE를 구현 하는 경우로 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) 인터페이스).

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 이 인터페이스에 인수로 전달 됩니다 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)합니다. 일부로 제공 됩니다는 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) union (특히를 [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) 구조) 이것은 부분에는 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 구조 보류 중인 중단점 만들기에 사용 되는 합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서의 메서드를 보여 줍니다. `IDebugDocumentPosition2`합니다.

|메서드|설명|
|------------|-----------------|
|[GetFileName](../../../extensibility/debugger/reference/idebugdocumentposition2-getfilename.md)|이 문서 위치를 포함 하는 소스 파일의 파일 이름을 가져옵니다.|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)|포함 하는 문서를 가져옵니다.|
|[IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)|이 위치는 지정한 문서에 포함 된 경우를 결정 합니다.|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)|이 문서에 대 한 범위를 가져옵니다.|

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)