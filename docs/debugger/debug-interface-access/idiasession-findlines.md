---
title: 'Idiasession:: Findlines | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLines method
ms.assetid: d6e84916-fd55-457e-b057-57f97b51fe73
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b127cbc5c9ddc5a2aa2d293d1371bab18d191fdb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839292"
---
# <a name="idiasessionfindlines"></a>IDiaSession::findLines
지정 된 컴파일 대상 및 원본 파일 식별자 내의 줄 번호를 검색합니다.

## <a name="syntax"></a>구문

```C++
HRESULT findLines ( 
   IDiaSymbol*           compiland,
   IDiaSourceFile*       file,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>매개 변수
 `compiland`

[in] [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 컴파일 대상을 나타내는 개체입니다. 줄 번호를 검색 하는 컨텍스트로이 인터페이스를 사용 합니다.

 `file`

[in] [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) 줄 번호를 검색 하는 원본 파일을 나타내는 개체입니다.

 `ppResult`

[out] 반환 된 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) 줄 번호의 목록을 포함 하는 개체 검색 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="see-also"></a>참고 항목
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)