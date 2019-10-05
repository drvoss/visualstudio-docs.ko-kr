---
title: 'Idiaenumlinenumbers:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::Next method
ms.assetid: 363d5b40-1316-4ab8-836f-63637f619e0a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 66abd987e3da4fadaac9d5b2de6664c4ae9e24ac
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62829760"
---
# <a name="idiaenumlinenumbersnext"></a>IDiaEnumLineNumbers::Next
열거형 시퀀스에서 줄 번호의 지정된 된 수를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT Next ( 
   ULONG            celt,
   IDiaLineNumber** rgelt,
   ULONG*           pceltFetched
);
```

#### <a name="parameters"></a>매개 변수
 celt

[in] 검색할 열거자의 줄 번호의 수입니다.

 rgelt

[out] 배열을 반환 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) 원하는 줄 번호를 나타내는 개체입니다.

 pceltFetched

[out] 페치된 열거자의 줄 번호의 수를 반환합니다.

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. 반환 `S_FALSE` 경우 자세한 줄 번호 없음. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="see-also"></a>참고 항목
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)