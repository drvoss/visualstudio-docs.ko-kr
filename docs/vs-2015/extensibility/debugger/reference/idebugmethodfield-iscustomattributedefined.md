---
title: IDebugMethodField::IsCustomAttributeDefined | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugMethodField::IsCustomAttributeDefined method
ms.assetid: 1b5d95a8-cc87-4acb-9e6a-3928f3632b7c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7fcc496131cd27837dc53fe2ecba05cf6b2c44d3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68162555"
---
# <a name="idebugmethodfieldiscustomattributedefined"></a>IDebugMethodField::IsCustomAttributeDefined
특정 사용자 지정 특성 정의 되었는지 여부를 결정 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT IsCustomAttributeDefined( 
   LPCOLESTR pszCustomAttributeName
);
```

```csharp
int IsCustomAttributeDefined(
   [In] string pszCustomAttributeName
);
```

#### <a name="parameters"></a>매개 변수
 `pszCustomAttributeName`

 [in] 검색할 사용자 지정 특성의 이름을 포함 하는 문자열입니다.

## <a name="return-value"></a>반환 값
 S_ok이 고, 사용자 지정 특성은이 메서드를 정의 하는 경우 그렇지 S_FALSE를 반환 합니다.

## <a name="see-also"></a>관련 항목
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)