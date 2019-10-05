---
title: SccQueryInfo 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 25a4b9b7d07b74047890c4ba56583cc09a394368
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353522"
---
# <a name="sccqueryinfo-function"></a>SccQueryInfo 함수
이 함수는 소스 제어에서 선택한 파일의 집합에 대 한 상태 정보를 얻습니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccQueryInfo(
   LPVOID  pvContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LPLONG  lpStatus
);
```

#### <a name="parameters"></a>매개 변수
 pvContext

[in] 원본 제어 플러그 인 상황에 맞는 구조입니다.

 nFiles

[in] 에 지정 된 파일 수를 `lpFileNames` 배열과의 길이 `lpStatus` 배열입니다.

 lpFileNames

[in] 배열 쿼리할 파일의 이름입니다.

 lpStatus

[out에서] 소스 제어 플러그 인 각 파일에 대 한 상태 플래그를 반환 하는 배열입니다. 자세한 내용은 [파일 상태 코드](../extensibility/file-status-code-enumerator.md)합니다.

## <a name="return-value"></a>반환 값
 원본 제어 플러그 인이 함수의 구현은 다음 값 중 하나를 반환 하:

|값|설명|
|-----------|-----------------|
|SCC_OK|쿼리 성공 했습니다.|
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 발생 한 소스 제어 시스템에 액세스 문제가 있었습니다. 재시도 사용 하는 것이 좋습니다.|
|SCC_E_PROJNOTOPEN|프로젝트 소스 제어에서 열려 있지 않습니다.|
|SCC_E_NONSPECIFICERROR|알 수 없는 오류가 발생 했습니다.|

## <a name="remarks"></a>설명
 경우 `lpFileName` 빈 문자열이 면는 현재 업데이트 상태 정보가 없습니다. 그렇지 않은 경우는 상태 정보를 변경한 파일의 전체 경로 이름입니다.

 반환 배열에는 비트 마스크의 수 `SCC_STATUS_xxxx` 비트입니다. 자세한 내용은 [파일 상태 코드](../extensibility/file-status-code-enumerator.md)합니다. 소스 제어 시스템에 모든 비트 형식을 지원 하지 않습니다. 예를 들어 경우 `SCC_STATUS_OUTOFDATE` , 제공 되지 않습니다 비트가 아니라 합니다.

 이 함수를 사용 하 여 파일을 체크 아웃, 다음을 유의 하십시오. `MSSCCI` 상태 요구 사항:

- `SCC_STATUS_OUTBYUSER` 현재 사용자가 파일을 체크 아웃할 때 설정 됩니다.

- `SCC_STATUS_CHECKEDOUT` 설정할 수 없습니다 `SCC_STATUS_OUTBYUSER` 설정 됩니다.

- `SCC_STATUS_CHECKEDOUT` 때 파일을 체크 아웃 된 지정 된 작업 디렉터리에만 설정 됩니다.

- 경우 파일을 체크 아웃 된 현재 사용자가 작업 디렉터리를 이외의 디렉터리로 `SCC_STATUS_OUTBYUSER` 설정 되어 있지만 `SCC_STATUS_CHECKEDOUT` 아닙니다.

## <a name="see-also"></a>참고 항목
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [파일 상태 코드](../extensibility/file-status-code-enumerator.md)