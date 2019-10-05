---
title: IDebugDocumentPositionOffset2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3793d54249fca1dc867cfe4072326245a67852cb
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333263"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
문자 오프셋으로 소스 파일의 위치를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugDocumentPositionOffset2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 IDE에 의해 구현 되며 디버그 엔진에서 사용 합니다.

## <a name="methods"></a>메서드
 다음 표에서의 메서드를 보여 줍니다. `IDebugDocumentPositionOffset2`합니다.

|메서드|설명|
|------------|-----------------|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|현재 문서 위치에 대 한 범위를 검색합니다.|

## <a name="remarks"></a>설명
 이 동일한 정보를 반환 [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) 하지만 `char` 문서 시작 부분 으로부터의 오프셋입니다. 이 존재 하 고 디스크에, 일반적으로 반환 되는 줄 및 열 정보 대신 문자를 1 차원 배열이 같은 문서를 표시 합니다.

## <a name="requirements"></a>요구 사항
 헤더: Msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)