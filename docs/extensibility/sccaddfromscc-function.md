---
title: SccAddFromScc 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAddFromScc
helpviewer_keywords:
- SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e8f37ce82630b72d5a01c66c8848431e8f6c2891
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334041"
---
# <a name="sccaddfromscc-function"></a>SccAddFromScc 함수
이 함수는 이미 소스 제어 시스템에 있는 파일을 찾을 수 있도록 하 고 이후에 현재 프로젝트의 일부인 이러한 파일을 확인 합니다. 예를 들어이 함수 파일을 복사 하지 않고 현재 프로젝트에 공통 헤더 파일을 가져올 수 있습니다. 파일의 반환 배열 `lplpFileNames`, IDE 프로젝트에 추가 하는 사용자가 파일의 목록을 포함 합니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccAddFromScc (
   LPVOID   pvContext,
   HWND     hWnd,
   LPLONG   lpnFiles,
   LPCSTR** lplpFileNames
);
```

### <a name="parameters"></a>매개 변수
 pvContext

[in] 원본 제어 플러그 인 상황에 맞는 구조입니다.

 hWnd

[in] 소스 제어 플러그 인을 제공 하는 모든 대화 상자에 대 한 부모로 사용할 수 있는 IDE 창 핸들입니다.

 lpnFiles

[out에서] 파일에 추가 되는 개수에 대 한 버퍼입니다. (이것이 `NULL` 가리키는 메모리 경우 `lplpFileNames` 해제 하는 것입니다. 자세한 내용은 참조 설명 합니다.)

 lplpFileNames

[out에서] 디렉터리 경로 없이 모든 파일 이름에 대 한 포인터의 배열입니다. 이 배열 할당 되 고 소스 제어 플러그 인에서 해제 합니다. 하는 경우 `lpnFiles` = 1 및 `lplpFileNames` 아닙니다 `NULL`를 가리키는 배열에서 첫 번째 이름 `lplpFileNames` 대상 폴더를 포함 합니다.

## <a name="return-value"></a>반환 값
 원본 제어 플러그 인이 함수의 구현은 다음 값 중 하나를 반환 하:

|값|설명|
|-----------|-----------------|
|SCC_OK|성공적으로 파일이 있으며 프로젝트에 추가 되었습니다.|
|SCC_I_OPERATIONCANCELED|아무런 영향을 미치지 작업이 취소 되었습니다.|
|SCC_I_RELOADFILE|파일 또는 프로젝트 다시 로드 해야 합니다.|

## <a name="remarks"></a>설명
 IDE는이 함수를 호출합니다. 소스 제어 플러그 인에서는 로컬 대상 폴더를 지정 하는 경우 IDE 전달 `lpnFiles` = 1 및를 로컬 폴더 이름을 전달 `lplpFileNames`합니다.

 경우에 대 한 호출을 `SccAddFromScc` 플러그 인에 값을 할당, 함수 반환 `lpnFiles` 및 `lplpFileNames`, 필요에 따라 파일 이름 배열에 대 한 메모리를 할당 (이 할당에 대 한 포인터를 대체 `lplpFileNames`). 소스 제어 플러그 인는 사용자의 디렉터리 또는 지정 된 대상 폴더에 모든 파일을 배치 하는 일을 담당 합니다. 그런 다음 IDE IDE 프로젝트에 파일을 추가합니다.

 마지막으로, IDE 호출이 함수를 두 번째로 전달 `NULL` 에 대 한 `lpnFiles`합니다. 이것은 특수 한 신호를 소스 제어에서 파일 이름 배열에 대 한 할당 된 메모리를 해제 하려면 플러그 인 `lplpFileNames``.`

 `lplpFileNames` 가 `char ***` 포인터입니다. 소스 제어 플러그 인이 API에 대 한 표준 방식에서 목록을 전달 하므로 파일 이름에 대 한 포인터의 배열에 대 한 포인터를 배치 합니다.

> [!NOTE]
> VSSCI API의 초기 버전에 추가 된 파일에 대 한 대상 프로젝트를 표시 하는 방법을 제공 하지 않았습니다. 이의 의미 체계에 맞게는 `lplpFIleNames` 매개 변수는 출력 매개 변수 보다는 입/출력 매개 변수를 확인 하려면 향상 되었습니다. 단일 파일을 지정 하는 경우 즉, 값을 가리키는 `lpnFiles` = 1 이면 첫 번째 요소 `lplpFileNames` 대상 폴더를 포함 합니다. 이러한 새로운 의미 체계를 호출 하 여 IDE 사용 하는 `SccSetOption` 함수를 사용 합니다 `nOption`매개 변수 설정 `SCC_OPT_SHARESUBPROJ`합니다. 경우에 소스 제어 플러그 인 의미 체계를 지원 하지 않습니다, 반환 `SCC_E_OPTNOTSUPPORTED`합니다. 따라서 사용 하지 않도록 설정 사용을 수행 하는 **소스 제어에서 추가** 기능입니다. 경우 플러그 인을 지원 합니다 **소스 제어에서 추가** 기능 (`SCC_CAP_ADDFROMSCC`), 새로운 의미 체계를 지원 하 고 반환 하는 다음 `SCC_I_SHARESUBPROJOK`합니다.

## <a name="see-also"></a>참고자료
- [원본 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)