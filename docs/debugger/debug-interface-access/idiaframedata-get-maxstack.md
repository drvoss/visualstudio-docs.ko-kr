---
title: 'Idiaframedata:: Get_maxstack | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_maxStack method
ms.assetid: 2585e13c-c0f3-49fe-9a84-08adb0dbeaa4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b609ba9357e96d8e7ece4459e33991a599b47ee7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839968"
---
# <a name="idiaframedatagetmaxstack"></a>IDiaFrameData::get_maxStack
프레임의 스택에 바이트의 최대 수를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_maxStack ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

[out] 스택에 푸시된 바이트의 최대 수를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. 반환 `S_FALSE` 경우이 속성이 지원 되지 않습니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>설명
 이 메서드에서 반환 되는 값은 프로그램 문자열의 해석에 일반적으로 사용 됩니다 (참조를 [idiaframedata:: Get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) 프로그램 문자열로의 정의 대 한 메서드).

## <a name="see-also"></a>참고 항목
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)