---
title: SccGetExtendedCapabilities 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa6a067a0b9e8358f503228dbc53e20586b84468
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353663"
---
# <a name="sccgetextendedcapabilities-function"></a>SccGetExtendedCapabilities 함수
이 함수는 소스 제어 플러그 인에서 지 원하는 추가 기능을 반환 합니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccGetExtendedCapabilities(
   LPVOID pContext,
   LONG lSccExCaps,
   LPBOOL pbSupported
);
```

### <a name="parameters"></a>매개 변수
 pContext

[in] 원본 제어 플러그 인 컨텍스트 포인터입니다.

 lSccExCaps

[in] 테스트 하려는 확장된 기능을 지정 하는 플래그 (의 확장 기능 코드 표를 참조 [기능 플래그](../extensibility/capability-flags.md) 가능한 플래그에 대 한).

 pbSupported

[out] 0이 아닌 값을 반환 합니다 (`TRUE`) 지정 된 기능 지원 되 면 그렇지 않은 경우 0을 반환 합니다 (`FALSE`).

## <a name="return-value"></a>반환 값
 원본 제어 플러그 인이 함수의 구현은 다음 값 중 하나를 반환 하:

|값|설명|
|-----------|-----------------|
|SCC_OK|Get 기능 작업을 완료 했습니다.|
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|알 수 없거나 지정 되지 않은 오류가 발생 했습니다.|

## <a name="remarks"></a>설명
 이 메서드는 주문형; 호출 즉, 기능을 테스트 해야 하는 경우이 메서드는 여부를 확인 하려면 기능이 지원 되는 합니다. 한 번에 하나만 플래그 지정 됩니다.

## <a name="see-also"></a>참고자료
- [원본 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [오류 코드](../extensibility/error-codes.md)
- [기능 플래그](../extensibility/capability-flags.md)