---
title: 'IDiaSymbol:: get_isHotpatchable | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isHotpatchable method
ms.assetid: b7b6f490-1cf2-4a68-9237-b152dac84d3c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 27218a2814e14e0a1ec30bd7fb4dc4840589251c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740223"
---
# <a name="idiasymbolget_ishotpatchable"></a>IDiaSymbol::get_isHotpatchable
모듈이 [/hotpatch (핫 패치 가능 이미지 만들기)](/cpp/build/reference/hotpatch-create-hotpatchable-image) 컴파일러 스위치를 사용 하 여 컴파일 되었는지 여부를 나타내는 플래그를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_isHotpatchable(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>매개 변수
 `pFlag`

제한이 모듈이 핫 패치 가능한 경우 `TRUE`를 반환 합니다. 그렇지 않으면 `FALSE`을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 `S_FALSE` 또는 오류 코드를 반환 합니다.

> [!NOTE]
> @No__t_0의 반환 값은 해당 기호에 대해 속성을 사용할 수 없음을 의미 합니다.

## <a name="remarks"></a>주의
 이 속성은 `SymTagCompilandDetails` 기호 형식에서 사용할 수 있습니다 ( [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)참조).

## <a name="requirements"></a>요구 사항

|요구 사항|설명|
|-----------------|-----------------|
|헤더:|dia2.h|
|버전:|DIA SDK v8.0|

## <a name="see-also"></a>참조
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)