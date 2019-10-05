---
title: IDebugProgram2::GetDebugProperty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 109e3ac1267afb4097429aafc9264416f3c2dbf1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319363"
---
# <a name="idebugprogram2getdebugproperty"></a>IDebugProgram2::GetDebugProperty
프로그램의 속성을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetDebugProperty( 
   IDebugProperty2** ppProperty
);
```

```csharp
int GetDebugProperty( 
   out IDebugProperty2 ppProperty
);
```

## <a name="parameters"></a>매개 변수
`ppProperty`\
[out] 반환 된 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 프로그램의 속성을 나타내는 개체입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 이 메서드에서 반환 되는 속성 프로그램에 적용 됩니다. 프로그램을 둘 이상의 속성을 반환 해야 하는 경우 해당 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 이 메서드에서 반환 된 개체는 추가 속성 및 호출의 컨테이너는 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) 메서드가 반환 되는 모든 속성 목록입니다.

 모든 숫자 및 추가 속성을 통해 기술 할 수 있는 형식의 프로그램 노출 될 수 있습니다는 `IDebugProperty2` 인터페이스입니다. IDE는 일반 속성 브라우저 사용자 인터페이스를 통해 추가 프로그램 속성을 표시할 수 있습니다.

## <a name="see-also"></a>참고자료
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)