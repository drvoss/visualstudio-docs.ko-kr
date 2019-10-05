---
title: IDiaSession::findInlineeLinesByLinenum | Microsoft Docs
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
ms.openlocfilehash: 493e1a2f6df57019183f36daf246ef69e8f1a4d6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63402604"
---
# <a name="idiasessionfindinlineelinesbylinenum"></a>IDiaSession::findInlineeLinesByLinenum
클라이언트가 모든 함수에에서 있지 않은 인라인을 직접 또는 간접적으로 지정 된 소스 파일과 줄 번호의 줄 번호 정보를 반복 하는 데 사용 하는 열거형을 검색 합니다.

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

[in] [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 컴파일 대상 줄 번호에 대 한 검색을 나타내는 개체입니다. 이 매개 변수 수 없습니다 `NULL`합니다.

 `file`

[in] [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) 검색 하는 소스 파일을 나타내는 개체입니다. 이 매개 변수 수 없습니다 `NULL`합니다.

 `linenum`

[in] 1부터 시작 줄 번호를 지정합니다.

> [!NOTE]
> 모든 선을 지정 하려면 0을 사용할 수 없습니다 (사용 된 [idiasession:: Findlines](../../debugger/debug-interface-access/idiasession-findlines.md) 모든 줄 찾기 방법).

 `column`

[in] 열 번호를 지정합니다. 모든 열을 지정 하려면 0을 사용 합니다. 열이 줄에 대 한 바이트 오프셋입니다.

 `ppResult`

[out] 반환 된 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) 검색 된 줄 번호의 목록을 포함 하는 개체입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="see-also"></a>참고 항목
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)