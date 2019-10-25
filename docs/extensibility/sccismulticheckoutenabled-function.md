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
ms.openlocfilehash: dd8fb5439ac68200ba1a3bbf3af665595528173e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721077"
---
# <a name="sccismulticheckoutenabled-function"></a>SccIsMultiCheckoutEnabled 함수
이 함수는 소스 제어 플러그 인에서 파일에 대해 여러 체크 아웃을 허용 하는지 여부를 확인 합니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccIsMultiCheckoutEnabled(
   LPVOID pContext,
   LPBOOL pbMultiCheckout
);
```

#### <a name="parameters"></a>매개 변수
 pContext

진행 소스 제어 플러그 인 컨텍스트 구조입니다.

 pbMultiCheckout

제한이 이 프로젝트에 대해 여러 체크 아웃을 사용할 수 있는지 여부를 지정 합니다 (0이 아닌 경우 여러 체크 아웃이 지원 됨).

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환 해야 합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|확인이 완료 되었습니다.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|일반 오류입니다.|

## <a name="remarks"></a>주의
 IDE는 두 명 이상의 사용자가 동시에 파일을 체크 아웃할 수 있는지 여부를 확인 하는 두 가지 검사를 수행 합니다. 먼저 원본 제어 시스템에서 여러 체크 아웃을 지원 해야 합니다. 원본 제어 플러그 인은 `SCC_CAP_MULTICHECKOUT`를 지정 하 여 초기화 하는 동안이 기능을 지정할 수 있습니다. 그런 다음 두 번째 검사로, IDE는이 함수를 호출 하 여 현재 프로젝트가 여러 체크 아웃을 지원 하는지 여부를 확인 합니다. 선택한 프로젝트에 대해 여러 체크 아웃이 지원 되 면 플러그 인에서 성공 코드를 반환 하 고 `pbMultiCheckout`를 0이 아닌 (`TRUE`) 또는 `FALSE`로 설정 합니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)