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
ms.openlocfilehash: ec5fea99994b891250dad85cfc43320848df98f9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62555106"
---
# <a name="cvcalle"></a>CV_call_e
함수의 호출 규칙을 지정 합니다.

> [!NOTE]
> 가장 일반적인 열거형 값만 여기에 설명 되어 있습니다. 전체 열거형 cvconst.h 헤더 파일에서 제공 됩니다.

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
CV_CALL_NEAR_C 거의 오른쪽에서 왼쪽 푸시를 사용 하 여 함수 호출 규칙을 지정 합니다. 함수 호출 스택을 지웁니다.

등록 함수 호출 규칙을 사용 하 여 푸시를 거의 왼쪽-오른쪽 CV_CALL_NEAR_FAST 지정 합니다. 호출된 된 함수 매개 변수 바이트의 합계를 사용 하 여 스택을 지웁니다.

CV_CALL_NEAR_STD 거의 표준 호출 (오른쪽에서 왼쪽 밀어넣기)를 사용 하 여 함수 호출 규칙을 지정 합니다.

CV_CALL_NEAR_SYS 지정 거의 시스템을 사용 하 여 함수 호출 규칙을 호출 합니다.

CV_CALL_THISCALL 사용 하 여 함수 호출 규칙 지정 `this` 호출 (`this` 레지스터에 전달 된 포인터).

CV_CALL_CLRCALL에서 언어 런타임 (CLR (공용) (라고도 하며 관리 되는 코드를 호출 규칙)를 사용 하는 함수 호출 규칙을 지정 합니다.

## <a name="remarks"></a>설명
이 열거형의 값에는 호출에서 반환 되는 [idiasymbol:: Get_callingconvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) 메서드.

## <a name="requirements"></a>요구 사항
헤더: cvconst.h

## <a name="see-also"></a>참고 항목
- [열거형 및 구조체](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)
