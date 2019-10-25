---
title: StackFrameTypeEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 20b0c9dd106e5744a369ddaa6cb870788f7464d3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738546"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
스택 프레임 유형을 지정 합니다.

## <a name="syntax"></a>구문

```C++
enum StackFrameTypeEnum {
    FrameTypeFPO,
    FrameTypeTrap,
    FrameTypeTSS,
    FrameTypeStandard,
    FrameTypeFrameData,
    FrameTypeUnknown = -1
};
```

## <a name="elements"></a>요소
`FrameTypeFPO` 프레임 포인터를 생략 합니다. FPO 정보를 사용할 수 있습니다.

커널 트랩 프레임을 `FrameTypeTrap` 합니다.

커널 트랩 프레임을 `FrameTypeTSS` 합니다.

표준 EBP 스택 프레임을 `FrameTypeStandard` 합니다.

`FrameTypeFrameData` 프레임 포인터를 생략 합니다. 프레임 데이터 정보를 사용할 수 있습니다.

디버그 정보가 없는 `FrameTypeUnknown` 프레임입니다.

## <a name="remarks"></a>주의
이 열거형의 값은 [IDiaStackFrame:: get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md) 메서드를 호출 하 여 반환 됩니다.

## <a name="requirements"></a>요구 사항
헤더: cvconst

## <a name="see-also"></a>참조
- [열거형 및 구조체](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)
