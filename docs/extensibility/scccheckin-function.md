---
title: SccCheckin 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 22264f9882192e05a9812cad4d6ea7f74bfdabfc
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333948"
---
# <a name="scccheckin-function"></a>SccCheckin 함수
이전에 체크 아웃 된 파일이 원본 제어 시스템에 변경 내용을 저장 하 고 새 버전을 만드는이 함수를 확인 합니다. 이 함수는 개수 및 체크 인 파일의 이름 배열을 사용 하 여 호출 됩니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccCheckin (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPSTR*    lpFileNames,
   LPCSTR    lpComment,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>매개 변수
 pvContext

[in] 원본 제어 플러그 인 상황에 맞는 구조입니다.

 hWnd

[in] 플러그 인 SCC 제공 하는 모든 대화 상자에 대 한 부모로 사용할 수 있는 IDE 창 핸들입니다.

 nFiles

[in] 체크 인을 선택 하는 파일 수입니다.

 lpFileNames

[in] 배열 검사할 파일의 정규화 된 로컬 경로 이름입니다.

 lpComment

[in] 각 체크 인 되 고 선택한 파일에 적용할 주석 처리 합니다. 이 매개 변수는 `NULL` 주석에 대 한 소스 제어 플러그 인에서 메시지를 표시 하는 경우.

 fOptions

[in] 명령 플래그, 0 또는 `SCC_KEEP_CHECKEDOUT`합니다.

 pvOptions

[in] SCC 플러그 인에 대 한 옵션입니다.

## <a name="return-value"></a>반환 값
 원본 제어 플러그 인이 함수의 구현은 다음 값 중 하나를 반환 하:

|값|설명|
|-----------|-----------------|
|SCC_OK|파일이는 성공적으로 체크 인 되었습니다.|
|SCC_E_FILENOTCONTROLLED|선택한 파일이 소스 코드 제어 없습니다.|
|SCC_E_ACCESSFAILURE|소스 제어 시스템에 경합 또는 네트워크 문제로 인해 액세스 문제가 있습니다. 재시도 사용 하는 것이 좋습니다.|
|SCC_E_NONSPECIFICERROR|알 수 없는 오류가 발생 했습니다. 파일 체크 인 되었습니다.|
|SCC_E_NOTCHECKEDOUT|사용자가 하지 파일을 체크 아웃, 확인할 수 없습니다.|
|SCC_E_CHECKINCONFLICT|때문에 체크 인을 수행할 수 없습니다.<br /><br /> -다른 사용자가 체크 인 계속 해 서 및 `bAutoReconcile` false입니다.<br /><br /> 또는<br /><br /> (예를 들어 경우 이진 파일이)-자동 병합을 수행할 수 없습니다.|
|SCC_E_VERIFYMERGE|파일 자동 병합 되었지만 사용자 확인이 늦어질 검사 하지 않았습니다.|
|SCC_E_FIXMERGE|파일 자동 병합 되었지만 수동으로 해결 해야 하는 병합 충돌로 인해 검사 하지 않았습니다.|
|SCC_E_NOTAUTHORIZED|사용자는이 작업을 수행할 수 없습니다.|
|SCC_I_OPERATIONCANCELED|작업이 완료 되기 전에 취소 되었습니다.|
|SCC_I_RELOADFILE|파일 또는 프로젝트 다시 로드 해야 합니다.|
|SCC_E_FILENOTEXIST|로컬 파일을 찾을 수 없습니다.|

## <a name="remarks"></a>설명
 메모는 체크 인 모든 파일에 적용 됩니다. 주석 인수 수를 `null` 문자열, 소스 제어 플러그 인에서 각 파일에 대 한 설명 문자열에 대 한 사용자를 입력할 수는 경우.

 합니다 `fOptions` 인수 값이 지정 될 수는 `SCC_KEEP_CHECKEDOUT` 파일을 확인 하 고 다시 체크 아웃 하는 사용자의 의도 나타내기 위해 플래그입니다.

## <a name="see-also"></a>참고자료
- [원본 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)