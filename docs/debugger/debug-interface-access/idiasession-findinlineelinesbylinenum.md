---
title: 'IDiaSession:: findInlineeLinesByLinenum | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: cf32ae7c-a0c8-4800-bc8f-d64fdd15fb06
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe238f3bc66d6a7c5978c5d7cbebcd185fcd43d2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742219"
---
# <a name="idiasessionfindinlineelinesbylinenum"></a>IDiaSession::findInlineeLinesByLinenum
클라이언트에서 지정 된 소스 파일 및 줄 번호에 직접 또는 간접적으로 인라인 된 모든 함수의 줄 번호 정보를 반복할 수 있도록 하는 열거형을 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT findInlineeLinesByVA ( 
   IDiaSymbol*           compiland,
   IDiaSourceFile*       file,
   DWORD                 linenum,
   DWORD                 column,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>매개 변수
 `compiland`

진행 줄 번호를 검색할 compiland를 나타내는 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 개체입니다. 이 매개 변수를 `NULL` 수 없습니다.

 `file`

진행 검색할 원본 파일을 나타내는 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) 개체입니다. 이 매개 변수를 `NULL` 수 없습니다.

 `linenum`

진행 1부터 줄 번호를 지정 합니다.

> [!NOTE]
> 모든 줄을 지정 하는 데 0을 사용할 수 없습니다. [IDiaSession:: findlines](../../debugger/debug-interface-access/idiasession-findlines.md) 메서드를 사용 하 여 모든 줄을 찾습니다.

 `column`

진행 열 번호를 지정 합니다. 모든 열을 지정 하려면 0을 사용 합니다. 열은 선으로의 바이트 오프셋입니다.

 `ppResult`

제한이 검색 된 줄 번호의 목록을 포함 하는 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="see-also"></a>참조
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)