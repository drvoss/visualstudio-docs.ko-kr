---
title: 'IDiaLineNumber:: get_statement | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_statement method
ms.assetid: 22b8ee29-79ef-427f-bd05-00d255ab836b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0a37052944f74e36b488541074a0033f5b8aca9e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743126"
---
# <a name="idialinenumberget_statement"></a>IDiaLineNumber::get_statement
프로그램 소스에서이 줄 정보가 식이 아니라 문의 시작을 설명 함을 나타내는 플래그를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_statement ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

제한이 이 줄 정보가 프로그램 소스에 있는 문의 시작 부분을 설명 하는 경우 `TRUE`를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. 이 속성이 지원 되지 않는 경우 `S_FALSE`를 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>주의
 문은 여러 줄에 걸쳐 있을 수 있습니다. 이 메서드는 연결 된 줄 번호가 이러한 여러 줄 문의 시작을 표시 하는지 여부를 나타냅니다.

## <a name="see-also"></a>참조
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)