---
title: 'IDiaSymbol:: get_addressSection | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressSection method
ms.assetid: fe80d479-3bb5-4f55-9b62-1bd58d0a60ce
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5a468fe6ee8a8d7d00bb2e6c261d50919a1dd764
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741070"
---
# <a name="idiasymbolget_addresssection"></a>IDiaSymbol::get_addressSection
주소 위치의 섹션 부분을 검색 합니다. [LocationType 열거형](../../debugger/debug-interface-access/locationtype.md) 이 `LocIsStatic`로 설정 된 경우를 사용 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_addressSection ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

제한이 주소 위치의 섹션 부분을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 `S_FALSE` 또는 오류 코드를 반환 합니다.

> [!NOTE]
> @No__t_0의 반환 값은 해당 속성을 기호에 사용할 수 없음을 의미 합니다.

## <a name="remarks"></a>주의
 외부 DLL에 있는 정적 멤버의 경우이 메서드가 반환 하는 섹션은 멤버의 가상 주소를 가져오는 데 의존 하므로 0이 될 수 있습니다. 가상 주소는 [IDiaSession](../../debugger/debug-interface-access/idiasession.md) 인터페이스의 [IDiaSession::P ut_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) 메서드가 DLL의 로드 주소를 지정 하는 0이 아닌 매개 변수를 사용 하 여 호출 된 경우에만 유효 합니다.

 주소의 오프셋 부분을 가져오려면 [IDiaSymbol:: get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md) 메서드를 호출 합니다.

## <a name="requirements"></a>요구 사항

|요구 사항|설명|
|-----------------|-----------------|
|헤더:|dia2.h|
|버전:|DIA SDK v7.0|

## <a name="see-also"></a>참조
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType 열거형](../../debugger/debug-interface-access/locationtype.md)