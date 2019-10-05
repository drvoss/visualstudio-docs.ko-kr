---
title: SccHistory 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccHistory
helpviewer_keywords:
- SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bad55b0fce5f4bec27ec707a4f9578c627a07363
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353610"
---
# <a name="scchistory-function"></a>SccHistory 함수
이 함수는 지정된 된 파일의 기록을 표시합니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccHistory(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

#### <a name="parameters"></a>매개 변수
 `pvContext`

[in] 원본 제어 플러그 인 상황에 맞는 구조입니다.

 `hWnd`

[in] 소스 제어 플러그 인을 제공 하는 모든 대화 상자에 대 한 부모로 사용할 수 있는 IDE 창 핸들입니다.

 `nFiles`

[in] 에 지정 된 파일 수는 `lpFileName` 배열입니다.

 `lpFileName`

[in] 파일의 정규화 된 이름의 배열입니다.

 `fOptions`

[in] 명령 플래그 (현재 사용 되지 않음)입니다.

 `pvOptions`

[in] 원본 제어 플러그 인에 대 한 옵션입니다.

## <a name="return-value"></a>반환 값
 원본 제어 플러그 인이 함수의 구현은 다음 값 중 하나를 반환 하:

|값|설명|
|-----------|-----------------|
|SCC_OK|버전 기록이 가져왔습니다.|
|SCC_I_RELOADFILE|실제로 소스 제어 시스템 (예를 들어 여는 이전 버전), 기록을 페치하는 동안 디스크에 있는 파일을 수정 하므로 IDE이이 파일을 다시 로드 해야 합니다.|
|SCC_E_FILENOTCONTROLLED|소스 제어를 파일이 없습니다.|
|SCC_E_OPNOTSUPPORTED|소스 제어 시스템에서이 작업을 지원 하지 않습니다.|
|SCC_E_NOTAUTHORIZED|사용자는이 작업을 수행할 수 없습니다.|
|SCC_E_ACCESSFAILURE|소스 제어 시스템에 경합 또는 네트워크 문제로 인해 액세스 문제가 있습니다. 재시도 사용 하는 것이 좋습니다.|
|SCC_E_PROJNOTOPEN|되지 않은 프로젝트가 열립니다.|
|SCC_E_NONSPECIFICERROR|알 수 없는 오류가 발생 했습니다. 파일 히스토리를 가져올 수 없습니다.|

## <a name="remarks"></a>설명
 소스 제어 플러그 인 각 파일의 기록을 표시 하려면 자체 대화 상자를 표시할 수 있습니다 사용 하 여 `hWnd` 부모 창으로 합니다. 또는 선택적 텍스트 출력 콜백 함수를 제공 합니다 [SccOpenProject](../extensibility/sccopenproject-function.md) 지원 되는 경우 사용할 수 있습니다.

 특정 상황에서,이 호출의 실행 하는 동안 검사할 파일이 변경 될 수 있습니다. 예를 들어를 [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] 기록 명령은 사용자 파일의 이전 버전을 가져올 수 있는 기회를 제공 합니다. 이러한 경우에는 소스 제어 플러그 인 반환 `SCC_I_RELOAD` 경고 IDE 파일 다시 로드 해야 합니다.

> [!NOTE]
> 소스 제어 플러그 인 파일의 배열에 대해이 함수를 지원 하지 않으면, 첫 번째 파일에 대 한 파일 히스토리만 표시할 수 있습니다.

## <a name="see-also"></a>참고 항목
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)