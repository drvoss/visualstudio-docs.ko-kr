---
title: SccGetEvents 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c8c3c08311c8dd359acaed18decc046354e7f37
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332039"
---
# <a name="sccgetevents-function"></a>SccGetEvents 함수
이 함수는 큐에 대기 중인된 상태 이벤트를 검색합니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccGetEvents (
   LPVOID pvContext,
   LPSTR  lpFileName,
   LPLONG lpStatus,
   LPLONG pnEventsRemaining
);
```

### <a name="parameters"></a>매개 변수
 pvContext

[in] 원본 제어 플러그 인 상황에 맞는 구조입니다.

 lpFileName

[out에서] 소스 제어 플러그 인 반환된 된 파일 이름 (최대 _max_path(256 자)를 배치 하는 위치는 버퍼입니다.

 lpStatus

[out에서] 상태 코드를 반환 합니다 (참조 [상태 코드를 파일](../extensibility/file-status-code-enumerator.md) 가능한 값에 대 한).

 pnEventsRemaining

[out에서] 이 호출 후 큐에 남아 있는 항목 수를 반환 합니다. 호출자가 호출 하도록 결정할 수 있습니다이 번호 큰 경우 합니다 [SccQueryInfo](../extensibility/sccqueryinfo-function.md) 모든 정보를 한 번에 가져오려고 합니다.

## <a name="return-value"></a>반환 값
 원본 제어 플러그 인이 함수의 구현은 다음 값 중 하나를 반환 하:

|값|설명|
|-----------|-----------------|
|SCC_OK|성공 이벤트를 가져옵니다.|
|SCC_E_OPNOTSUPPORTED|이 함수는 지원되지 않습니다.|
|SCC_E_NONSPECIFICERROR|알 수 없는 오류가 발생 했습니다.|

## <a name="remarks"></a>설명
 이 함수는 원본 제어에서 파일에 대 한 상태 업데이트 되었는지를 확인 하려면 유휴 처리 동안 호출 됩니다. 소스 제어 플러그 인에 대해 알 수 있는 모든 파일의 상태를 유지 하 고 변경 될 때마다 상태를 기록 플러그 인을 상태 및 연결된 된 파일을 큐에 저장 됩니다. 때 `SccGetEvents` 라고, 위쪽 큐의 요소를 검색 하 고 반환 합니다. 이 함수는 이전에 캐시 된 정보만 반환으로 제한 됩니다 하 고 (즉, 디스크의 읽기 또는 소스 제어 시스템 상태에 대 한 요청); 매우 빠른 시간 안에 있어야 합니다. 그렇지 않은 경우 IDE의 성능 저하를 시작할 수 있습니다.

 소스 제어 플러그 인에서 가리키는 버퍼에 빈 문자열을 저장 보고서는 상태 업데이트 되지 경우 `lpFileName`합니다. 그렇지 않으면 플러그 인 저장 파일의 전체 경로 이름에는 상태 정보를 변경 된 적절 한 상태 코드를 반환 합니다 (에 자세히 설명 하는 값 중 하나 [상태 코드를 파일](../extensibility/file-status-code-enumerator.md)).

## <a name="see-also"></a>참고자료
- [원본 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [파일 상태 코드](../extensibility/file-status-code-enumerator.md)