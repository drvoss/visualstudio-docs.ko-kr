---
title: IDebugProperty2::SetValueAsString | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsString
helpviewer_keywords:
- IDebugProperty2::SetValueAsString
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 27b481165cf95a97d7674d52d8553426dfb6417c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66314602"
---
# <a name="idebugproperty2setvalueasstring"></a>IDebugProperty2::SetValueAsString
지정된 된 문자열에서 속성의 값을 설정 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetValueAsString ( 
   LPCOLESTR pszValue,
   UINT      nRadix,
   DWORD     dwTimeout
);
```

```csharp
int SetValueAsString ( 
   string pszValue,
   uint   nRadix,
   uint   dwTimeout
);
```

## <a name="parameters"></a>매개 변수
`pszValue`\
[in] 설정할 값이 들어 있는 string입니다.

`nRadix`\
[in] 모든 숫자 정보를 해석 하는 데 사용할 기 수입니다. 이 0을 기 수를 자동으로 확인 하도록 수 있습니다.

`dwTimeout`\
[in] 이 메서드에서 반환 되기 전에 대기할 밀리초 단위로 최대 시간을 지정 합니다. 사용 하 여 `INFINITE` 무기한 대기 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`; 그렇지 않으면 오류 코드를 반환 합니다. 다음 표에서 가능한 다른 값을 보여 줍니다.

|값|설명|
|-----------|-----------------|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|문자열 속성 값으로 변환할 수 없습니다 또는 속성 값을 설정할 수 없습니다.|
|`E_SETVALUE_VALUE_IS_READONLY`|속성이 읽기 전용입니다.|

## <a name="see-also"></a>참고자료
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)