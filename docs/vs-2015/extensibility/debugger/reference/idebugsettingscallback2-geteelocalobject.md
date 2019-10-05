---
title: IDebugSettingsCallback2::GetEELocalObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetEELocalObject
ms.assetid: e69a3469-a049-420c-b918-c48a1e7b9baf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e6bf186d8b4bf660cc4a22e962754e859378674
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68202475"
---
# <a name="idebugsettingscallback2geteelocalobject"></a>IDebugSettingsCallback2::GetEELocalObject
메트릭 이름을 지정 하는 식 계산기 로컬 개체를 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetEELocalObject(
   REFGUID     guidLang,
   REFGUID     guidVendor,
   LPCWSTR     pszMetric,
   IUnknown ** ppUnk
);
```

```csharp
private int GetEELocalObject(
   ref Guid          guidLang,
   ref Guid          guidVendor,
   string            pszMetric,
   out System.Object ppUnk
);
```

#### <a name="parameters"></a>매개 변수
 `guidLang`

 [in] 프로그래밍 언어의 고유 식별자입니다.

 `guidVendor`

 [in] 공급 업체의 고유 식별자입니다.

 `pszMetric`

 [in] 메트릭의 이름입니다.

 `ppUnk`

 [out] 반환 식 계산기 로컬 개체입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="see-also"></a>참고 항목
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)