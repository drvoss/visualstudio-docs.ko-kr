---
title: IDebugPortPicker::DisplayPortPicker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 815b44735e36489991da84216e2fcc6db8e6fab4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66308753"
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
사용자가 포트를 선택할 수 있도록 지정 된 대화 상자가 표시 됩니다.

## <a name="syntax"></a>구문

```cpp
HRESULT DisplayPortPicker(
   HWND hwndParentDialog,
   BSTR* pbstrPortId
);
```

```csharp
public int DisplayPortPicker(
   int hwndParentDialog,
   out string pbstrPortId
);
```

## <a name="parameters"></a>매개 변수
`hwndParentDialog`\
[in] 부모 대화 상자에 대 한 핸들입니다.

`pbstrPortId`\
[out] 포트 식별자 문자열입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다. 반환 값 `S_FALSE` (또는 반환 값이 `S_OK` 사용 하 여는 `BSTR` 로 설정 `NULL`) 사용자 클릭 했음을 나타냅니다 **취소**합니다.

## <a name="see-also"></a>참고자료
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)