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
ms.openlocfilehash: d270b9b177367c9a15c2b64f6f8bc5607c5a459d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741618"
---
# <a name="idiastackframeget_registervalue"></a>IDiaStackFrame::get_registerValue
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

진행 [CV_HREG_e 열거형](../../debugger/debug-interface-access/cv-hreg-e.md) 열거형 값 중 하나입니다.

 `pRetVal`

제한이 레지스터에 저장 된 값입니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="see-also"></a>참조
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [CV_HREG_e 열거형](../../debugger/debug-interface-access/cv-hreg-e.md)