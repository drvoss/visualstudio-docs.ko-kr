---
title: IDiaSession::findInlineesByName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 9860336d-f703-4ecb-bfc4-3f5beb175a76
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a7fd74707284e32471bad1da27e288139ea617a1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742174"
---
# <a name="idiasessionfindinlineesbyname"></a>IDiaSession::findInlineesByName
클라이언트에서 지정 된 이름과 일치 하는 인라인 함수의 줄 번호 정보를 반복할 수 있도록 하는 열거형을 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT findInlineesByName ( 
   LPCOLESTR             name,
   DWORD                 option,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>매개 변수
 `name`

진행 비교할 때 사용할 이름을 지정 합니다.

 `option`

진행 이름 검색에 적용 되는 비교 옵션을 지정 합니다. [Namesearchoptions 열거형](../../debugger/debug-interface-access/namesearchoptions.md) 열거형의 값은 단독으로 사용 하거나 함께 사용할 수 있습니다.

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