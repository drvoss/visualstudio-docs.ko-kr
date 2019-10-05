---
title: IDebugDocumentText2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 43716ce3b01464d2937fd75ce90ec5028679ef47
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66330638"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
이 인터페이스는 텍스트 문서를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugDocumentText2 : IDebugDocument2
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 디버그 엔진 (DE)을 제공 하는 데 필요한 소스 코드를 텍스트 형식에 있으면이 인터페이스를 구현 합니다. 이므로 가장 일반적인 경우는 DE 구현 하는 경우는 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) 인터페이스에도 구현 해야 합니다 `IDebugDocumentText2` 인터페이스입니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 사용 된 `QueryInterface` 에서이 인터페이스를 가져올 방법은 `IDebugDocument2` 인터페이스.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 메서드 외에도 `IDebugDocument2` 인터페이스에서이 인터페이스는 다음 메서드를 구현 합니다.

|메서드|설명|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|문서의이 위치에서 텍스트의 크기를 검색합니다.|
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|문서의 지정된 된 위치에서 텍스트를 검색합니다.|

## <a name="remarks"></a>설명
 이 인터페이스를 구현 하는 개체도 구현 해야 합니다는 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> 인터페이스를 제공 합니다 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> 에 대 한 인터페이스는 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) 개체입니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)