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
ms.openlocfilehash: 0a2cfdf5a617352d7ba0c2db00e7705343f1eb5e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720866"
---
# <a name="sccpopulatelist-function"></a>SccPopulateList 함수
이 함수는 특정 소스 제어 명령에 대 한 파일 목록을 업데이트 하 고 지정 된 모든 파일에 대 한 소스 제어 상태를 제공 합니다.

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

진행 소스 제어 플러그 인 컨텍스트 구조입니다.

 n

진행 @No__t_0 배열의 모든 파일에 적용 되는 소스 제어 명령입니다. 가능한 명령 목록은 [명령 코드](../extensibility/command-code-enumerator.md) 를 참조 하세요.

 n

진행 @No__t_0 배열에 있는 파일 수입니다.

 lpFileNames 이름

진행 IDE에 알려진 파일 이름 배열입니다.

 pfnPopulate

진행 파일 추가 및 제거를 위해 호출할 IDE 콜백 함수입니다 (자세한 내용은 [POPLISTFUNC](../extensibility/poplistfunc.md) 참조).

 pvCallerData

진행 변경 되지 않은 상태로 콜백 함수로 전달 되는 값입니다.

 lpStatus

[in, out] 각 파일에 대 한 상태 플래그를 반환 하는 소스 제어 플러그 인에 대 한 배열입니다.

 fOptions

진행 명령 플래그 (세부 정보는 [특정 명령에 사용 되는 Bitflags](../extensibility/bitflags-used-by-specific-commands.md) 의 "PopulateList flag" 섹션 참조).

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환 해야 합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|성공할.|
|SCC_E_NONSPECIFICERROR|일반 오류입니다.|

## <a name="remarks"></a>주의
 이 함수는 파일 목록을 검사 하 여 현재 상태를 검사 합니다. 이 메서드는 `pfnPopulate` 콜백 함수를 사용 하 여 파일이 `nCommand`의 조건과 일치 하지 않는 경우 호출자에 게 알립니다. 예를 들어 명령이 `SCC_COMMAND_CHECKIN` 되 고 목록의 파일이 체크 아웃 되지 않으면 콜백이 호출자에 게 알리는 데 사용 됩니다. 경우에 따라 소스 제어 플러그 인은 명령의 일부일 수 있는 다른 파일을 찾아 추가할 수도 있습니다. 이렇게 하면 예를 들어 Visual Basic 사용자가 프로젝트에서 사용 하는 .bmp 파일을 체크 아웃 하지만 Visual Basic 프로젝트 파일에는 표시 되지 않습니다. 사용자가 IDE에서 **Get** 명령을 선택 합니다. IDE는 사용자가 가져올 수 있다고 생각 하는 모든 파일의 목록을 표시 하지만 목록이 표시 되기 전에 `SccPopulateList` 함수를 호출 하 여 표시할 목록이 최신 상태 인지 확인 합니다.

## <a name="example"></a>예제
 IDE는 사용자가 가져올 수 있다고 생각 하는 파일 목록을 작성 합니다. 이 목록을 표시 하기 전에 `SccPopulateList` 함수를 호출 하 여 소스 제어 플러그 인이 목록에서 파일을 추가 하 고 삭제할 수 있는 기회를 제공 합니다. 플러그 인은 지정 된 콜백 함수를 호출 하 여 목록을 수정 합니다 (자세한 내용은 [POPLISTFUNC](../extensibility/poplistfunc.md) 참조).

 플러그 인은 작업이 완료 된 후 `SccPopulateList` 함수에서 반환 될 때까지 파일을 추가 및 삭제 하는 `pfnPopulate` 함수를 계속 호출 합니다. 그러면 IDE에서 목록을 표시할 수 있습니다. @No__t_0 배열은 IDE에 의해 전달 된 원래 목록의 모든 파일을 나타냅니다. 플러그 인은 콜백 함수를 사용 하는 것 외에도 이러한 모든 파일의 상태를 채웁니다.

> [!NOTE]
> 소스 제어 플러그 인에는 항상이 함수에서 바로 반환 하는 옵션이 있습니다 .이 옵션을 선택 하면 목록이 그대로 유지 됩니다. 플러그 인이이 함수를 구현 하는 경우 [Sccinitialize](../extensibility/sccinitialize-function.md)에 대 한 첫 번째 호출에서 `SCC_CAP_POPULATELIST` 기능 조합이를 설정 하 여이를 나타낼 수 있습니다. 기본적으로 플러그 인은 항상 전달 되는 모든 항목이 파일 이라고 가정 합니다. 그러나 IDE에서 `fOptions` 매개 변수에 `SCC_PL_DIR` 플래그를 설정 하는 경우 전달 되는 모든 항목은 디렉터리로 간주 됩니다. 플러그 인은 디렉터리에 있는 모든 파일을 추가 해야 합니다. IDE는 파일 및 디렉터리를 혼합 하 여 전달 하지 않습니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
- [특정 명령에 사용되는 Bitflag](../extensibility/bitflags-used-by-specific-commands.md)
- [명령 코드](../extensibility/command-code-enumerator.md)