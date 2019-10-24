---
title: 'IDiaSymbol:: get_isMSILNetmodule | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isMSILNetmodule method
ms.assetid: 593827f3-8437-4a12-ada4-ff715ec95fb2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 322a4ef059c190e3ba73bbce6f80978530270ece
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740194"
---
# <a name="idiasymbolget_ismsilnetmodule"></a>IDiaSymbol::get_isMSILNetmodule
모듈이 .netmodule 인지 여부를 나타내는 플래그를 검색 합니다. 메타 데이터만 포함 하 고 네이티브 기호는 포함 하지 않는 MSIL (Microsoft 중간 언어) 모듈입니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_isMSILNetmodule(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>매개 변수
 `pFlag`

제한이 모듈이 MSIL 이면 `TRUE`을 반환 하 고, 그렇지 않으면 `FALSE`을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 `S_FALSE` 또는 오류 코드를 반환 합니다.

> [!NOTE]
> @No__t_0의 반환 값은 해당 속성을 기호에 사용할 수 없음을 의미 합니다.

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