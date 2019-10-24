---
title: 'IDiaSession:: findLines | Microsoft Docs'
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
ms.openlocfilehash: d6082bfe8a3eee00d425441ff44a6eadd1c36e27
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742132"
---
# <a name="idiasessionfindlines"></a>IDiaSession::findLines
지정 된 compiland 및 소스 파일 식별자 내의 줄 번호를 검색 합니다.

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

진행 Compiland를 나타내는 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 개체입니다. 이 인터페이스는 줄 번호를 검색할 컨텍스트로 사용 합니다.

 `file`

진행 줄 번호를 검색할 소스 파일을 나타내는 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) 개체입니다.

 `ppResult`

제한이 검색 된 줄 번호의 목록을 포함 하는 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="see-also"></a>참조
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)