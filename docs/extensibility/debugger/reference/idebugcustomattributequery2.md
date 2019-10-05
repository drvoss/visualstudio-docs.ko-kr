---
title: IDebugCustomAttributeQuery2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
- IDebugCustomAttributeQuery2 interface
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 00220574ac9c16bdab9abd64adde1877ee0fd9f2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335799"
---
# <a name="idebugcustomattributequery2"></a>IDebugCustomAttributeQuery2
이 필드에 대 한 사용자 지정 특성의 존재를 확인 하 고 있는 경우에 특성 정보를 반환 합니다.

## <a name="syntax"></a>구문

```
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 기호 공급자를 구현 하는 동일한 개체에서이 인터페이스를 구현 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 사용자 지정 특성을 지원 하기 위해.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 사용 하 여 [QueryInterface](/cpp/atl/queryinterface) 에서이 인터페이스를 가져올 수 합니다 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 인터페이스입니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에의 메서드를 **IDebugCustomAttributeQuery** 인터페이스입니다.

|메서드|설명|
|------------|-----------------|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|사용자 지정 특성을 이름별 있는지 여부를 결정 합니다.|
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)|지정된 된 사용자 지정 특성에 대 한 특성 정보를 가져옵니다.|

 외에 **IDebugCustomAttributeQuery** 메서드를 `IDebugCustomAttributeQuery2` 다음 메서드를 구현 합니다.

|메서드|설명|
|------------|-----------------|
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|이 필드에 연결 하는 모든 사용자 지정 특성에 대 한 열거자를 가져옵니다.|

## <a name="remarks"></a>설명
 합니다 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) 메서드는이 필드에 대해 정의 된 모든 사용자 지정 특성에 대 한 열거자를 반환할 수 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: sh.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)