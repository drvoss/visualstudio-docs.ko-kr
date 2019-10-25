---
title: 'IDiaFrameData:: get_allocatesBasePointer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_allocatesBasePointer method
ms.assetid: 8a33db5d-008c-4fe5-b64f-210c9b77f686
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 283ef71b32c186956804cb3afe121af53a99abfc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743649"
---
# <a name="idiaframedataget_allocatesbasepointer"></a>IDiaFrameData::get_allocatesBasePointer
이 주소 범위의 코드에 대해 기본 포인터가 할당 되었는지 여부를 나타내는 플래그를 검색 합니다. 이 메서드는 사용 되지 않습니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_allocatesBasePointer ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

제한이 기본 포인터가 할당 된 경우 `TRUE`를 반환 합니다. 그렇지 않으면 `FALSE`을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. 이 속성이 지원 되지 않는 경우 `S_FALSE`를 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>주의
 이 속성은 이전에 FPO_DATA에 액세스 한 코드 또는 [IDiaFrameData:: get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) 메서드에서 반환 된 프로그램 문자열이 `NULL` 경우에만 사용 해야 합니다. 그렇지 않으면 프로그램 문자열에 이전 레지스터 값을 계산 하는 데 필요한 모든 정보가 포함 됩니다.

## <a name="see-also"></a>참조
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)