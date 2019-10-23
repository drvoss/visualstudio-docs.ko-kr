---
title: IDiaSymbol::findChildrenExByVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenExByVA
ms.assetid: 29080009-36e4-4697-acd7-50f2e3e1bf1b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d9cc9f540b200ff6fdf4736b6a0bf64175a5ee3e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741240"
---
# <a name="idiasymbolfindchildrenexbyva"></a>IDiaSymbol::findChildrenExByVA
지정 된 가상 주소에서 유효한 기호 자식을 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT findChildrenExByVA ( 
   enum SymTagEnum   symtag,
   LPCOLESTR         name,
   DWORD             compareFlags,
   DWORD             address,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>매개 변수
 `symtag`

진행 [SymTagEnum 열거](../../debugger/debug-interface-access/symtagenum.md)에 정의 된 대로 검색할 자식의 기호 태그를 지정 합니다. 모든 자식 항목을 검색 하려면 `SymTagNull`로 설정 합니다.

 `name`

진행 검색할 자식의 이름을 지정 합니다. 모든 자식 항목을 검색 하려면 `NULL`로 설정 합니다.

 `compareFlags`

진행 이름 일치에 적용할 비교 옵션을 지정 합니다. [Namesearchoptions 열거형](../../debugger/debug-interface-access/namesearchoptions.md) 열거형의 값은 단독으로 사용 하거나 함께 사용할 수 있습니다.

 `address`

진행 가상 주소를 지정 합니다.

 `ppResult`

제한이 검색 된 자식 기호의 목록을 포함 하는 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 기호의 자식이 하나 이상 발견 되 면 `S_OK`을 반환 하 고, 자식 항목이 없으면 `S_FALSE`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>주의
 반환 되는 로컬 기호는 라이브 범위 정보를 포함 합니다.

## <a name="requirements"></a>요구 사항
 헤더: Dia2

 라이브러리: diaguids

 DLL: msdia100

## <a name="see-also"></a>참조
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [NameSearchOptions 열거형](../../debugger/debug-interface-access/namesearchoptions.md)