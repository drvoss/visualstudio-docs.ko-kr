---
title: IDiaStackWalkHelper::get_registerValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::get_registerValue method
ms.assetid: 46ac5eee-73a3-44a1-8635-6c58ba193cb6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 275941aaf3a1eb2cab6554b18c6d9aa66605121a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62831834"
---
# <a name="idiastackwalkhelpergetregistervalue"></a>IDiaStackWalkHelper::get_registerValue
레지스터의 값을 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_registerValue ( 
   DWORD      index,
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 `index`

[in] 값을 [CV_HREG_e 열거형](../../debugger/debug-interface-access/cv-hreg-e.md) 를에서 값을 얻기 위해 등록 하는 지정 하는 열거형입니다.

 `pRetVal`

[out] 등록의 현재 값을 반환합니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 크기에도 불구 하 고는 `pRetVal` 매개 변수를 구현만 무엇입니까 레지스터 일반적으로 보유 저장 해야 합니다. 예를 들어는 8 비트 레지스터만 가장 낮은 8-의 비트를 지정된 된 값을 보유합니다. 이 8 비트 값이 메서드에서 반환 하는 경우 64 비트로 확장 됩니다.

## <a name="see-also"></a>참고 항목
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [CV_HREG_e 열거형](../../debugger/debug-interface-access/cv-hreg-e.md)