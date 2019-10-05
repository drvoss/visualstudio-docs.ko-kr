---
title: SccUncheckout 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4d50b321f96b6759d95a6d923222e5e0a92b2ee3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338468"
---
# <a name="sccuncheckout-function"></a>SccUncheckout 함수
이 함수에는 선택한 하나 이상의 파일의 콘텐츠를 체크 아웃 하기 전의 상태로 복원 이전 체크 아웃 작업을 실행 취소 합니다. 체크 아웃 이후에 파일에 대 한 모든 변경 내용이 손실 됩니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccUncheckout (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

#### <a name="parameters"></a>매개 변수
 pvContext

[in] 원본 제어 플러그 인 상황에 맞는 구조입니다.

 hWnd

[in] 소스 제어 플러그 인을 제공 하는 모든 대화 상자에 대 한 부모로 사용할 수 있는 IDE 창 핸들입니다.

 nFiles

[in] 에 지정 된 파일 수는 `lpFileNames` 배열입니다.

 lpFileNames

[in] 체크 아웃을 취소 하려는 파일의 정규화 된 로컬 경로 이름 배열입니다.

 fOptions

[in] 명령 플래그 (사용 되지 않음)입니다.

 pvOptions

[in] 원본 제어 플러그 인에 대 한 옵션입니다.

## <a name="return-value"></a>반환 값
 원본 제어 플러그 인이 함수의 구현은 다음 값 중 하나를 반환 하:

|값|설명|
|-----------|-----------------|
|SCC_OK|체크 아웃을 취소 했습니다.|
|SCC_E_FILENOTCONTROLLED|선택한 파일이 소스 코드 제어 없습니다.|
|SCC_E_ACCESSFAILURE|소스 제어 시스템에 경합 또는 네트워크 문제로 인해 액세스 문제가 있습니다. 재시도 사용 하는 것이 좋습니다.|
|SCC_E_NONSPECIFICERROR|알 수 없는 오류가 발생 했습니다. 실행 취소 체크 아웃 하지 못했습니다.|
|SCC_E_NOTCHECKEDOUT|사용자 파일을 체크 아웃 없습니다.|
|SCC_E_NOTAUTHORIZED|사용자는이 작업을 수행할 수 없습니다.|
|SCC_E_PROJNOTOPEN|프로젝트 소스 제어에서 열리지 않았습니다.|
|SCC_I_OPERATIONCANCELED|작업이 완료 되기 전에 취소 되었습니다.|

## <a name="remarks"></a>설명
 이 작업이 끝나면 합니다 `SCC_STATUS_CHECKEDOUT` 및 `SCC_STATUS_MODIFIED` 플래그는 모두 지워집니다 체크 아웃을 취소를 수행 하는 파일에 대 한 합니다.

## <a name="see-also"></a>참고 항목
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)