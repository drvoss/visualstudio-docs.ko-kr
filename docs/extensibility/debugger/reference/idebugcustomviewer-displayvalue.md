---
title: IDebugCustomViewer::DisplayValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer::DisplayValue
helpviewer_keywords:
- IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9d6ff987e12e70a9d3dd443cfafc45d2698469b8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335698"
---
# <a name="idebugcustomviewerdisplayvalue"></a>IDebugCustomViewer::DisplayValue
이 메서드는 지정 된 값을 표시 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT DisplayValue(
   HWND             hwnd,
   DWORD            dwID,
   IUnknown *       pHostServices,
   IDebugProperty3* pDebugProperty);
);
```

```csharp
int DisplayValue(
   IntPtr          hwnd,
   uint            dwID,
   object          pHostServices,
   IDebugProperty3 pDebugProperty
);
```

## <a name="parameters"></a>매개 변수
`hwnd`\
[in] 부모 창

`dwID`\
[in] 둘 이상의 유형을 지 원하는 사용자 지정 뷰어에서의 ID입니다.

`pHostServices`\
[in] 예약되어 있습니다. 항상 설정 null로 합니다.

`pDebugProperty`\
[in] 표시할 값을 검색할 수 있는 인터페이스입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`; 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 표시는 "modal"이이 메서드는 필요한 창을 만들, 값 표시, 입력을 대기 하 고 호출자에 게 반환 하기 전에 모든 창을 닫습니다. 즉, 메서드 제거 창에 사용자 입력을 기다리는를 출력용 창 만들기에서 속성의 값을 표시 하는 모든 측면을 처리 해야 합니다.

 대 한 값을 변경할 수는 지정 된 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 개체를 사용할 수는 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) 메서드-문자열로 값을 표현할 수 있는 경우. 사용자 지정 인터페이스를 만드는 데 필요한 것이 고, 그렇지-이 구현 하는 식 계산기를 단독 `DisplayValue` 메서드-구현 하는 동일한 개체에는 `IDebugProperty3` 인터페이스입니다. 이 사용자 지정 인터페이스는 임의 크기 또는 복잡성의 데이터를 변경 하기 위한 메서드 제공 하는 것입니다.

## <a name="see-also"></a>참고자료
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)