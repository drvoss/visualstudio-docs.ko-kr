---
title: SccPopulateList 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 64bcf6d443d1f96d650bde7fb92f69bbb12c5327
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353536"
---
# <a name="sccpopulatelist-function"></a>SccPopulateList 함수
이 함수는 특정 원본 제어 명령 위한 파일의 목록을 업데이트 하 고 모든 지정 된 파일에 소스 제어 상태를 제공 합니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccPopulateList (
   LPVOID          pvContext,
   enum SCCCOMMAND nCommand,
   LONG            nFiles,
   LPCSTR*         lpFileNames,
   POPLISTFUNC     pfnPopulate,
   LPVOID          pvCallerData,
   LPLONG          lpStatus,
   LONG            fOptions
);
```

#### <a name="parameters"></a>매개 변수
 pvContext

[in] 원본 제어 플러그 인 상황에 맞는 구조입니다.

 된 명령

[in] 모든 파일에 적용 될 원본 제어 명령을 합니다 `lpFileNames` 배열 (참조 [명령 코드](../extensibility/command-code-enumerator.md) 가능한 명령 목록에 대 한).

 nFiles

[in] 에 있는 파일 수는 `lpFileNames` 배열입니다.

 lpFileNames

[in] IDE에 알려진 파일 이름의 배열입니다.

 pfnPopulate

[in] 파일 추가 및 제거 하기 위해 호출할 IDE 콜백 함수 (참조 [POPLISTFUNC](../extensibility/poplistfunc.md) 세부 정보에 대 한).

 pvCallerData

[in] 콜백 함수에 전달할 값을 변경 되지 않습니다.

 lpStatus

[out에서] 각 파일에 대 한 상태 플래그를 반환 하는 플러그 인 소스 제어에 대 한 배열입니다.

 fOptions

[in] 명령 플래그 ("PopulateList 플래그" 섹션을 참조 하세요 [비트는 특정 명령에 사용](../extensibility/bitflags-used-by-specific-commands.md) 세부 정보에 대 한).

## <a name="return-value"></a>반환 값
 원본 제어 플러그 인이 함수의 구현은 다음 값 중 하나를 반환 하:

|값|설명|
|-----------|-----------------|
|SCC_OK|명령 실행 성공|
|SCC_E_NONSPECIFICERROR|알 수 없는 오류가 발생 했습니다.|

## <a name="remarks"></a>설명
 이 함수는 현재 상태에 대 한 파일 목록을 검사합니다. 사용 된 `pfnPopulate` 파일에 대 한 조건과 일치 하지 않는 경우 호출자에 알리기 위해 콜백 함수는 `nCommand`합니다. 예를 들어, 명령이 실행 되 면 `SCC_COMMAND_CHECKIN` 목록에서 파일을 체크 아웃 되지 않습니다 하 고 콜백을 호출자를 알리는 데 사용 됩니다. 경우에 따라 소스 제어 플러그 인에 추가 하 고 명령의 일부를 수 있는 다른 파일을 찾을 수 있습니다. 이 사용 하면 예를 들어, Visual Basic 사용자가 자신의 프로젝트에 사용 되는 Visual Basic 프로젝트 파일에 나타나지 않으면.bmp 파일을 체크 아웃 합니다. 사용자가 선택 하는 **가져올** IDE에서 명령을 합니다. IDE를 가져올 수는 모든 파일 목록이 표시 됩니다 목록 표시 되며, 전에 `SccPopulateList` 함수가 호출 되어 표시할 목록이 최신 상태 인지 확인 합니다.

## <a name="example"></a>예제
 IDE를 가져올 수는 파일의 목록을 작성 합니다. 이 목록에 표시 하기 전에 호출 된 `SccPopulateList` 함수를 추가 하 고 목록에서 파일을 삭제 합니다. 소스 제어 플러그 인 기회를 제공 합니다. 지정된 된 콜백 함수를 호출 하 여 플러그 인 수정 목록 (참조 [POPLISTFUNC](../extensibility/poplistfunc.md) 자세한).

 플러그 인을 계속 호출 하는 `pfnPopulate` 함수를 추가 하 고 완료 되 고 다음에서 반환 될 때까지 파일을 삭제 합니다 `SccPopulateList` 함수입니다. 그런 다음 IDE 목록을 표시할 수 있습니다. `lpStatus` 배열 IDE에 의해 전달 된 원래 목록의 모든 파일을 나타냅니다. 상황을 위해 이러한 파일 뿐만 아니라 모든의 플러그 인 채우기 콜백 함수를 사용 합니다.

> [!NOTE]
> 항상 소스 제어 플러그 인 이므로 목록 두면이 함수에서 바로 반환 하는 옵션을 가집니다. 플러그 인이 함수를 구현,이 설정 하 여 나타낼 수 있습니다 합니다 `SCC_CAP_POPULATELIST` 첫 번째 호출에서 기능 비트 플래그를 [SccInitialize](../extensibility/sccinitialize-function.md)합니다. 기본적으로 플러그 인 항상 가정해 야 모든 항목에 전달 되는 파일입니다. 그러나 IDE 설정 하는 경우는 `SCC_PL_DIR` 플래그를 `fOptions` 디렉터리 간주 되기 위해 매개 변수에 전달 되는 모든 항목은입니다. 플러그 인는 디렉터리에 속하는 모든 파일을 추가 해야 합니다. IDE 전달 하지는 않지만 파일 및 디렉터리의 혼합입니다.

## <a name="see-also"></a>참고 항목
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
- [특정 명령에 사용되는 Bitflag](../extensibility/bitflags-used-by-specific-commands.md)
- [명령 코드](../extensibility/command-code-enumerator.md)