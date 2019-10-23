---
title: IDiaSymbol::findChildrenEx | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenEx
ms.assetid: 6e045045-da8c-4338-9423-81a1ca20c405
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26fdced012baada390cdd0a112856b592d3c923e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741263"
---
# <a name="idiasymbolfindchildrenex"></a>IDiaSymbol::findChildrenEx
기호의 자식을 검색 합니다. 프로그램이에서 최적화를 사용 하 여 컴파일되는 경우 반환 되는 로컬 기호에는 라이브 범위 정보가 포함 됩니다.

## <a name="syntax"></a>구문

```C++
HRESULT findChildrenEx ( 
   enum SymTagEnum   symtag,
   LPCOLESTR         name,
   DWORD             compareFlags,
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

 `ppResult`

제한이 검색 된 자식 기호의 목록을 포함 하는 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 기호의 자식이 하나 이상 발견 되 면 `S_OK`을 반환 하 고, 자식 항목이 없으면 `S_FALSE`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>주의
 이 메서드는 [IDiaSymbol:: findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)의 확장 된 버전입니다.

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