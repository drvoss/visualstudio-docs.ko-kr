---
title: 'IDiaSession:: findSymbolsByRVAForAcceleratorPointerTag | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a073cc45-0c7b-417e-b5fc-a3b08beccdbc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb1b24d24de35de30b24937a6cfbf59d12f69482
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741999"
---
# <a name="idiasessionfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSession::findSymbolsByRVAForAcceleratorPointerTag
해당 태그 값이 지정 된 경우이 메서드는 지정 된 상대 가상 주소에서 지정 된 부모 액셀러레이터 키 함수에 포함 된 기호의 열거형을 반환 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT findSymbolsByRVAForAcceleratorPointerTag ( 
   IDiaSymbol*           parent,
   DWORD                 tagValue,
   DWORD                 rva,
   IDiaEnumSymbols**     ppResult
);
```

#### <a name="parameters"></a>매개 변수
 `parent`

진행 검색할 액셀러레이터 스텁 함수에 해당 하는 `IDiaSymbol`입니다.

 `tagValue`

진행 포인터 태그 값입니다.

 `rva`

진행 상대 가상 주소입니다.

 `ppResult`

제한이 결과를 사용 하 여 초기화 되는 `IDiaEnumSymbols` 인터페이스 포인터에 대 한 포인터입니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>주의
 액셀러레이터 키 함수에 해당 하는 `IDiaSymbol` 인터페이스에 대해서만이 메서드를 호출 합니다.

## <a name="see-also"></a>참조
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)