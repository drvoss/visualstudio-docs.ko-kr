---
title: CV_call_e | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_call_e enumeration
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5deb59d4bbee06e505ba10bf1d4f08b1b06aa62d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745348"
---
# <a name="cv_call_e"></a>CV_call_e
함수에 대 한 호출 규칙을 지정 합니다.

> [!NOTE]
> 가장 일반적인 열거형 값만 여기에 설명 되어 있습니다. 전체 열거형은 cvconst 헤더 파일에서 사용할 수 있습니다.

## <a name="syntax"></a>구문

```C++
typedef enum CV_call_e {
    CV_CALL_NEAR_C    = 0x00,
    CV_CALL_NEAR_FAST = 0x04,
    CV_CALL_NEAR_STD  = 0x07,
    CV_CALL_NEAR_SYS  = 0x09,
    CV_CALL_THISCALL  = 0x0b,
    CV_CALL_CLRCALL   = 0x16
} CV_call_e;
```

## <a name="elements"></a>요소
CV_CALL_NEAR_C는 오른쪽에서 왼쪽으로 가까운 푸시를 사용 하 여 함수 호출 규칙을 지정 합니다. 호출 함수는 스택을 지웁니다.

CV_CALL_NEAR_FAST 레지스터를 사용 하 여 왼쪽에서 오른쪽으로 가까운 푸시를 사용 하 여 함수 호출 규칙을 지정 합니다. 호출 된 함수는 매개 변수 바이트의 합계를 사용 하 여 스택을 지웁니다.

CV_CALL_NEAR_STD는 가까운 표준 호출 (오른쪽에서 왼쪽 푸시)을 사용 하 여 함수 호출 규칙을 지정 합니다.

CV_CALL_NEAR_SYS는 NEAR 시스템 호출을 사용 하 여 함수 호출 규칙을 지정 합니다.

CV_CALL_THISCALL `this` 호출을 사용 하 여 함수 호출 규칙을 지정 합니다 (레지스터에 전달 된 `this` 포인터).

CV_CALL_CLRCALL은 CLR (공용 언어 런타임)에서 사용 하는 함수 호출 규칙을 지정 합니다 (관리 코드 호출 규칙이 라고도 함).

## <a name="remarks"></a>주의
이 열거형의 값은 [IDiaSymbol:: get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) 메서드를 호출 하 여 반환 됩니다.

## <a name="requirements"></a>요구 사항
헤더: cvconst

## <a name="see-also"></a>참조
- [열거형 및 구조체](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)
