---
title: SccIsMultiCheckoutEnabled 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 93cbefe716b46b3dd3fe481447612c5c7f65daa3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353579"
---
# <a name="sccismulticheckoutenabled-function"></a>SccIsMultiCheckoutEnabled 함수
이 함수는 소스 제어 플러그 인 파일에서 여러 체크 아웃을 허용 하는지 여부를 확인 합니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccIsMultiCheckoutEnabled(
   LPVOID pContext,
   LPBOOL pbMultiCheckout
);
```

#### <a name="parameters"></a>매개 변수
 pContext

[in] 원본 제어 플러그 인 상황에 맞는 구조입니다.

 pbMultiCheckout

[out] 이 프로젝트 (여러 체크 아웃 지원 되는 0이 아닌 의미)에 대 한 여러 체크 아웃 사용 되는지 여부를 지정 합니다.

## <a name="return-value"></a>반환 값
 원본 제어 플러그 인이 함수의 구현은 다음 값 중 하나를 반환 하:

|값|설명|
|-----------|-----------------|
|SCC_OK|검사가 성공 했습니다.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|알 수 없는 오류가 발생 했습니다.|

## <a name="remarks"></a>설명
 IDE에는 두 개의 검사를 하는 경우 파일 체크 아웃할 수 동시에 둘 이상의 사용자가 결정할 수 있습니다. 첫째, 소스 제어 시스템 다중 체크 아웃을 지원 해야 합니다. 소스 제어 플러그 인을 지정 하 여 초기화 하는 동안이 기능에 지정할 수는 `SCC_CAP_MULTICHECKOUT`합니다. 그런 다음 두 번째 확인을 IDE 현재 프로젝트에서 여러 체크 아웃 지원 여부를 결정 하는이 함수를 호출 합니다. 플러그 인은 성공 반환 코드 및 설정 하는 여러 체크 아웃은 선택한 프로젝트에 대 한 지원 `pbMultiCheckout` 에 0이 아닌 값 (`TRUE`) 또는 `FALSE`합니다.

## <a name="see-also"></a>참고 항목
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)