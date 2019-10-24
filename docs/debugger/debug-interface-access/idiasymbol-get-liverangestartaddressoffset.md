---
title: 'IDiaSymbol:: get_liveRangeStartAddressOffset | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeStartAddressOffset
ms.assetid: f5b28914-0a14-4b22-8259-59d7f97ee610
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b39bf1e73d8b056c1cfcbfafd41dcbbb464c40ce
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739915"
---
# <a name="idiasymbolget_liverangestartaddressoffset"></a>IDiaSymbol::get_liveRangeStartAddressOffset
로컬 기호가 유효한 범위의 시작 주소에 대 한 오프셋 부분을 반환 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_liveRangeStartAddressOffset ( 
   DWORD* offset
);
```

#### <a name="parameters"></a>매개 변수
 `offset`

제한이 시작 주소 범위의 오프셋 부분을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

> [!NOTE]
> 반환 된 오류 코드는 기호에 라이브 범위 정보가 없음을 의미 합니다.

## <a name="remarks"></a>주의
 섹션과 오프셋으로 구성 된 주소는 기호가 유효한 범위의 시작 부분입니다.

 주소 섹션을 가져오려면 [IDiaSymbol:: get_liveRangeStartAddressSection](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddresssection.md)를 사용 합니다.

## <a name="requirements"></a>요구 사항
 헤더: Dia2

 라이브러리: diaguids

 DLL: msdia100

## <a name="see-also"></a>참조
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)