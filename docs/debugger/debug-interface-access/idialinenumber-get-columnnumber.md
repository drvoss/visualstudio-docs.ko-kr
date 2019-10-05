---
title: 'Idialinenumber:: Get_columnnumber | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_columnNumber method
ms.assetid: e317f29a-6525-46a7-8421-33985392f8fd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 03d24770c90ebd225fa37dd7f60d794781e79e7e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62828456"
---
# <a name="idialinenumbergetcolumnnumber"></a>IDiaLineNumber::get_columnNumber
식 또는 문이 시작 되는 열 번호를 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT get_columnNumber ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

[out] 식 또는 문이 시작 되는 열 번호를 반환 합니다. 값이 0 이면 다음 열 정보가 나타나지 않습니다.

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. 반환 `S_FALSE` 경우이 속성이 지원 되지 않습니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>설명
 이 메서드에서 반환 된 열 값이 문의 줄에서 첫 번째 문자는 줄에 대 한 바이트 오프셋입니다.

## <a name="see-also"></a>참고 항목
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)