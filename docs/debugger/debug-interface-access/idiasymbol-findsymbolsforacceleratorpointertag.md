---
title: 'IDiaSymbol:: findSymbolsForAcceleratorPointerTag | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: fb66852c-c5f7-4140-b9fe-20cb4e51a9fe
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1544471bd4ff9166d4c8f4c10f48840db6f576f3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741126"
---
# <a name="idiasymbolfindsymbolsforacceleratorpointertag"></a>IDiaSymbol::findSymbolsForAcceleratorPointerTag
C++ AMP 스텁 함수의 액셀러레이터 포인터 태그 수를 반환 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT findSymbolsForAccleratorPointerTag (
   DWORD             tagValue,
   IDiaEnumSymbols** ppResult);
```

#### <a name="parameters"></a>매개 변수
 `tagValue`

진행 Pointee 기호 레코드를 찾을 포인터 태그 값입니다.

 `ppResult`

제한이 결과를 사용 하 여 초기화 되는 `IDiaEnumSymbols` 인터페이스 포인터에 대 한 포인터입니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 `S_FALSE` 또는 오류 코드를 반환 합니다.

## <a name="see-also"></a>참조
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)