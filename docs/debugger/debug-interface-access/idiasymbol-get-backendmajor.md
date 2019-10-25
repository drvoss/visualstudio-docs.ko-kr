---
title: IDiaSymbol::get_backEndMajor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_backEndMajor method
ms.assetid: 900a05dd-c29b-44ad-b46b-f43bda819a66
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bae33cf32bc86ad77fa03fab9f940c9fec25194a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740995"
---
# <a name="idiasymbolget_backendmajor"></a>IDiaSymbol::get_backEndMajor
컴파일러의 백 엔드 주 버전 번호를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_backEndMajor ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

제한이 백 엔드 주 버전 번호를 반환 합니다. 설명 부분을 참조하세요.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 `S_FALSE` 또는 오류 코드를 반환 합니다.

> [!NOTE]
> @No__t_0의 반환 값은 해당 기호에 대해 속성을 사용할 수 없음을 의미 합니다.

## <a name="remarks"></a>주의
 컴파일러는 일반적으로 프런트 엔드 (파서) 라는 두 개의 기본 요소로 구성 되며,이는 소스 코드를 중간 형식으로 구문 분석 하는 작업을 처리 하 고, 백 엔드 (코드 생성기)는 중간 형식을 어셈블리로 변환 합니다. 프런트 엔드에서 백 엔드에서 다른 버전을 갖는 것이 일반적이 지 않습니다.

 프런트 엔드 또는 백 엔드 버전 번호는 \<major > 세 부분으로 구성 됩니다. >를 \<minor 합니다. > \<build \<major >는 주 버전 번호 이며, \<minor >은 부 버전 번호이 고 \<build >는 빌드 번호입니다. 예를 들어 13.10.3077.

## <a name="requirements"></a>요구 사항

|요구 사항|설명|
|-----------------|-----------------|
|헤더:|dia2.h|
|버전:|DIA SDK v7.0|

## <a name="see-also"></a>참조
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)