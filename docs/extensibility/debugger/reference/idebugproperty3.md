---
title: IDebugProperty3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3
helpviewer_keywords:
- IDebugProperty3 interface
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8581e8163ab95eac7d49c5deca70c339804aac64
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348696"
---
# <a name="idebugproperty3"></a>IDebugProperty3
이 인터페이스는에 대 한 지원을 제공 합니다.

- 속성과 연결 된 임의의 긴 문자열을 검색 합니다.

- 속성을 사용 하 여 고유 ID를 연결 합니다.

- 속성에 대 한 사용자 지정 뷰어 목록을 검색합니다.

- 결과 오류를 보고 하는 기능을 사용 하 여 속성의 값을 설정 합니다.

## <a name="syntax"></a>구문

```
IDebugProperty3 : IDebugProperty2
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 디버그 엔진 (DE)를 구현 하는 동일한 개체에서이 인터페이스를 구현 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 긴 문자열, 속성 Id 및 사용자 지정 뷰어에 대 한 지원을 제공 합니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 호출 [QueryInterface](/cpp/atl/queryinterface) 에 `IDebugProperty2` 인터페이스가이 인터페이스를 가져올 수 있습니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 상속 된 메서드 외에도 `IDebugProperty2`, `IDebugProperty3` 인터페이스는 다음 메서드를 노출 합니다.

|메서드|설명|
|------------|-----------------|
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|속성과 연결 된 문자열의 길이 반환 합니다.|
|[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)|사용자가 제공한 버퍼에서 문자열을 반환합니다.|
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|이 속성에 대 한 고유 ID를 만듭니다.|
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|이 속성에 대 한 고유 ID를 제거합니다.|
|[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)|이 속성을 사용 하 여 볼 수 있는 사용자 지정 뷰어를 반환 합니다.|
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|이 속성을 사용 하 여 볼 수 있는 사용자 지정 뷰어 목록을 반환 합니다.|
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|문제가 있는 경우 오류 메시지를 반환 합니다.이 속성의 값을 설정 합니다.|

## <a name="remarks"></a>설명
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) 세션 디버그 관리자 (SDM) 속성의 값을 설정 하는 것이 좋습니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)