---
title: IDiaFrameData::get_program | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_program method
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e6b893a40172bfd806130bef663da8676b513042
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62832840"
---
# <a name="idiaframedatagetprogram"></a>IDiaFrameData::get_program
현재 함수를 호출 하기 전에 설정 하는 레지스터를 계산 하는 데 사용 되는 프로그램 문자열을 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_program ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

[out] 프로그램 문자열을 반환합니다.

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. 반환 `S_FALSE` 경우이 속성이 지원 되지 않습니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>설명
 프로그램 문자열이 프롤로그를 설정 하기 위해 해석 되는 매크로의 시퀀스입니다. 일반적인 스택 프레임 수 프로그램 문자열을 사용 하는 예를 들어 `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="`합니다. 형식은 역방향 폴란드어 표기법으로 연산자는 피연산자를 수행 하는 위치입니다. `T0` 스택에 있는 임시 변수를 나타냅니다. 이 예제에서는 다음 단계를 수행합니다.

1. 레지스터의 내용을 이동 `ebp` 에 `T0`입니다.

2. 추가 `4` 에 값 `T0` 주소를 생성 하 고 해당 주소에서 값을 얻으려면 레지스터에 값을 저장 하려면 `eip`합니다.

3. 에 저장 된 주소의 값을 얻으려면 `T0` 레지스터에 값을 저장 하 고 `ebp`입니다.

4. 추가 `8` 에 값 `T0` 레지스터에 값을 저장 하 고 `esp`입니다.

   프로그램 문자열이 현재 스택 프레임을 나타내는 함수에 대 한 설정 호출 규칙 CPU에 관련 된 참고 합니다.

## <a name="see-also"></a>참고 항목
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)