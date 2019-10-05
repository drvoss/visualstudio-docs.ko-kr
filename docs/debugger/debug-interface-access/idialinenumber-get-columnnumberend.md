---
title: 'Idialinenumber:: Get_columnnumberend | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_columnNumberEnd method
ms.assetid: 02fa56c1-87b6-405a-adee-3bb6bc62de2d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 567df436093b53432e44e21fb96f0d092b71c81d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839851"
---
# <a name="idialinenumbergetcolumnnumberend"></a>IDiaLineNumber::get_columnNumberEnd
식 또는 문이 끝나는 소스 1부터 시작 열 번호를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_columnNumberEnd ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

[out] 식 또는 문이 끝나는 열 번호를 반환 합니다. 값이 0 이면 다음 열 끝 정보 나타나지 않습니다.

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. 반환 `S_FALSE` 경우이 속성이 지원 되지 않습니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>설명
 이 메서드에서 반환 된 열 값이 문의 줄에서 마지막 문자 뒤의 줄 위치 오프셋 바이트입니다.

## <a name="see-also"></a>참고 항목
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)