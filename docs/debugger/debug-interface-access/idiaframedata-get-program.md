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
ms.openlocfilehash: 135f2b0a042dd74b573a0746831a48fb27e7c2a9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743514"
---
# <a name="idiaframedataget_program"></a>IDiaFrameData::get_program
현재 함수를 호출 하기 전에 레지스터 집합을 계산 하는 데 사용 되는 프로그램 문자열을 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_program ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

제한이 프로그램 문자열을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. 이 속성이 지원 되지 않는 경우 `S_FALSE`를 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>주의
 프로그램 문자열은 프롤로그를 설정 하기 위해 해석 되는 매크로의 시퀀스입니다. 예를 들어 일반적인 스택 프레임은 프로그램 문자열 `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="`를 사용할 수 있습니다. 형식은 역방향 폴란드어 표기법입니다. 여기서 연산자는 피연산자를 따릅니다. `T0`는 스택의 임시 변수를 나타냅니다. 이 예에서는 다음 단계를 수행 합니다.

1. 레지스터 `ebp`의 내용을 `T0`로 이동 합니다.

2. @No__t_1 값에 `4`를 추가 하 여 주소를 생성 하 고, 해당 주소에서 값을 가져오고, 등록 `eip`에 값을 저장 합니다.

3. @No__t_0에 저장 된 주소에서 값을 가져오고 해당 값을 등록 `ebp`에 저장 합니다.

4. @No__t_1 값에 `8`을 추가 하 고이 값을 등록 `esp`에 저장 합니다.

   프로그램 문자열은 CPU와 현재 스택 프레임이 나타내는 함수에 대해 설정 된 호출 규칙에 따라 다릅니다.

## <a name="see-also"></a>참조
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)