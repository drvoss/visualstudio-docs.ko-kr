---
title: IDiaSymbol::get_isLTCG | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isLTCG method
ms.assetid: 5f7f05b8-6b71-4958-9e1e-e4924ef9c59b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4f5fe47d8575c47756cce8fd1580ced5f3036766
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/12/2019
ms.locfileid: "64785723"
---
# <a name="idiasymbolgetisltcg"></a>IDiaSymbol::get_isLTCG
지정 하는 플래그를 검색 하는지 여부를 [Compiland](../../debugger/debug-interface-access/compiland.md) 링커 스위치를 사용 하 여 연결 되었습니다 [/LTCG (링크 타임 코드 생성)](/cpp/build/reference/ltcg-link-time-code-generation), 전체 프로그램 최적화 하는 데는 도움이 합니다. 이 스위치는 관리 되는 코드에만 적용 됩니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_iSLTCG(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>매개 변수
 pFlag

[out] 반환 `TRUE` 경우는 `compiland` /LTCG 링커 스위치를 사용 하 여 연결 된 그렇지 않으면 반환 `FALSE`합니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`이 고, 그렇지 않으면 반환 `S_FALSE` 또는 오류 코드입니다.

> [!NOTE]
> 반환 값이 `S_FALSE` 속성 기호에 사용할 수 없다는 것을 의미 합니다.

## <a name="requirements"></a>요구 사항

|요구 사항|Description|
|-----------------|-----------------|
|헤더:|dia2.h|
|버전:|DIA SDK v8.0|

## <a name="see-also"></a>참고 항목
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)