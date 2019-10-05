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
ms.openlocfilehash: 44f715c4f74d9b120b324e2d68417a24c9b42684
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62854824"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
스택 프레임 형식을 지정합니다.

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
`FrameTypeFPO` 프레임 포인터 생략 합니다. FPO 정보를 사용할 수 있습니다.

`FrameTypeTrap` 커널 트랩 프레임입니다.

`FrameTypeTSS` 커널 트랩 프레임입니다.

`FrameTypeStandard` 표준 EBP 스택 프레임입니다.

`FrameTypeFrameData` 프레임 포인터 생략 합니다. 프레임 데이터 정보를 사용할 수 있습니다.

`FrameTypeUnknown` 모든 디버그 정보가 없는 프레임입니다.

## <a name="remarks"></a>설명
이 열거형의 값에는 호출에서 반환 되는 [idiastackframe:: Get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md) 메서드.

## <a name="requirements"></a>요구 사항
헤더: cvconst.h

## <a name="see-also"></a>참고 항목
- [열거형 및 구조체](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)
