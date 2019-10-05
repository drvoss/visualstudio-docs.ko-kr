---
title: IDiaStackFrame::get_registerValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_registerValue method
ms.assetid: cbe3d8ac-319a-40ac-bc3e-4eb81b2d7807
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a819293863b658f6e12609b2c1cd83c37532e02d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62832107"
---
# <a name="idiastackframegetregistervalue"></a>IDiaStackFrame::get_registerValue
스택 프레임에 저장 된 지정 된 레지스터의 값을 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_registerValue(
   ULONG      registerIndex,
   ULONGLONG *pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 `registerIndex`

[in] 중 하나는 [CV_HREG_e 열거형](../../debugger/debug-interface-access/cv-hreg-e.md) 열거형 값입니다.

 `pRetVal`

[out] 레지스터에 저장 하는 값입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="see-also"></a>참고 항목
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [CV_HREG_e 열거형](../../debugger/debug-interface-access/cv-hreg-e.md)