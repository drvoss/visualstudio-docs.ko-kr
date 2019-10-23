---
title: 'IDiaFrameData:: get_maxStack | Microsoft Docs'
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
ms.openlocfilehash: fc5eaa20c5167897ccb19d5e142656ed314a91e6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743536"
---
# <a name="idiaframedataget_maxstack"></a>IDiaFrameData::get_maxStack
프레임의 스택에 푸시되는 최대 바이트 수를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_maxStack ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

제한이 스택에 푸시되는 최대 바이트 수를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. 이 속성이 지원 되지 않는 경우 `S_FALSE`를 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>주의
 이 메서드에서 반환 되는 값은 일반적으로 프로그램 문자열을 해석 하는 데 사용 됩니다. 프로그램 문자열 정의는 [IDiaFrameData:: get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) 메서드를 참조 하세요.

## <a name="see-also"></a>참조
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)