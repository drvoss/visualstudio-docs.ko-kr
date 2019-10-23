---
title: 'IDiaLineNumber:: get_length | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_length method
ms.assetid: 2c55a6f7-4ef5-45fb-9fd1-d72deaaa2829
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2f803fac1439d384133f0819859f2917072a8790
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743192"
---
# <a name="idialinenumberget_length"></a>IDiaLineNumber::get_length
블록의 바이트 수를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_length ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

제한이 블록의 바이트 수를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. 이 속성이 지원 되지 않는 경우 `S_FALSE`를 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>주의
 블록은 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) 개체로 표시 되는 줄의 소스 코드 길이입니다.

## <a name="see-also"></a>참조
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)