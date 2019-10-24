---
title: 'IDiaLineNumber:: get_columnNumber | Microsoft Docs'
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
ms.openlocfilehash: 6ac6eea93daf9b0ef7d8169a4f765c249f3b9ee4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743254"
---
# <a name="idialinenumberget_columnnumber"></a>IDiaLineNumber::get_columnNumber
식 또는 문이 시작 되는 열 번호를 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT get_columnNumber ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

제한이 식 또는 문이 시작 되는 열 번호를 반환 합니다. 값이 0 이면 열 정보가 없습니다.

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. 이 속성이 지원 되지 않는 경우 `S_FALSE`를 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>주의
 이 메서드에서 반환 하는 열 값은 줄의 줄에 있는 문의 첫 번째 문자에 대 한 바이트 오프셋입니다.

## <a name="see-also"></a>참조
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)