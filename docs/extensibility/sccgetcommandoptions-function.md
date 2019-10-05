---
title: SccGetCommandOptions 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetCommandOptions
helpviewer_keywords:
- SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 13e8bbae6ee16eb81fdb29f526a1f41e905fa504
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351880"
---
# <a name="sccgetcommandoptions-function"></a>SccGetCommandOptions 함수
이 함수는 지정 된 명령에 대 한 고급 옵션에 대 한 라는 메시지입니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccGetCommandOptions(
   LPVOID pvContext,
   HWND hWnd,
   enum SCCCOMMAND iCommand,
   LPCMDOPTS* ppvOptions
);
```

### <a name="parameters"></a>매개 변수
 pvContext

[in] 원본 제어 플러그 인 상황에 맞는 구조입니다.

 hWnd

[in] 소스 제어 플러그 인을 제공 하는 모든 대화 상자에 대 한 부모로 사용할 수 있는 IDE 창 핸들입니다.

 iCommand

[in] 고급 옵션은 요청 되는 명령 (참조 [코드 명령을](../extensibility/command-code-enumerator.md) 가능한 값에 대 한).

 ppvOptions

[in] 옵션 구조 (수도 있습니다 `NULL`).

## <a name="return-value"></a>반환 값
 원본 제어 플러그 인이 함수의 구현은 다음 값 중 하나를 반환 하:

|값|설명|
|-----------|-----------------|
|SCC_OK|명령 실행 성공|
|SCC_I_ADV_SUPPORT|소스 제어 플러그 인 명령에 대 한 고급 옵션을 지원합니다.|
|SCC_I_OPERATIONCANCELED|사용자는 원본 제어 플러그 인의 취소 **옵션** 대화 상자.|
|SCC_E_OPTNOTSUPPORTED|소스 제어 플러그 인이 작업을 지원 하지 않습니다.|
|SCC_E_ISCHECKEDOUT|현재 체크 아웃 된 파일에서이 작업을 수행할 수 없습니다.|
|SCC_E_ACCESSFAILURE|소스 제어 시스템에 경합 또는 네트워크 문제로 인해 액세스 문제가 있습니다. 재시도 사용 하는 것이 좋습니다.|
|SCC_E_NONSPECIFICERROR|알 수 없는 오류가 발생 했습니다.|

## <a name="remarks"></a>설명
 처음 사용 하 여이 함수를 호출 하는 IDE `ppvOptions` = `NULL` 소스 제어 플러그 인 지정된 된 명령에 대 한 고급 옵션 기능을 지원 하는지 확인 하 합니다. 사용자는 고급 옵션을 요청 하면 IDE이이 함수를 다시 호출 플러그 인는 해당 명령에 대 한 기능을 지원 않습니다, (일반적으로 구현 되는 **고급** 대화 상자에서 단추) 에대한NULL이아닌포인터를제공합니다.`ppvOptions` 가리키는 `NULL` 포인터입니다. 플러그 인 private 구조체에서 사용자가 지정한 모든 고급 옵션을 저장 하 고 해당 구조체에 대 한 포인터를 반환 합니다. `ppvOptions`합니다. 이 구조는 후속 호출을 포함 한 후에 대해 알아야 할 다른 모든 원본 제어 플러그 인 API 함수에 전달 된 `SccGetCommandOptions` 함수입니다.

 예제는이 상황을 명확 하 게 하는 데 도움이 됩니다.

 사용자가 선택 하는 **가져오기** 명령과 IDE를 표시를 **가져오기** 대화 상자. IDE 호출을 `SccGetCommandOptions` 함수와 `iCommand` 로 설정 `SCC_COMMAND_GET` 및 `ppvOptions` 로 설정 `NULL`. 질문 플러그 인 소스 컨트롤에 의해 해석 됩니다.이 내용은 "갖춰야 할이 명령에 대 한 고급 옵션" 플러그 인을 반환 하는 경우 `SCC_I_ADV_SUPPORT`, IDE 표시는 **고급** 단추 해당 **가져오기** 대화 상자.

 사용자가 처음을 **고급** 단추를 IDE를 다시 호출를 `SccGetCommandOptions` 함수를 비-를 사용 하 여이 이번`NULL``ppvOptions` 가리키는 `NULL` 포인터. 플러그 인 표시 하는 자체 **옵션 가져오기** 대화 상자에서 해당 정보 자체 구조로 저장 하 고 해당 구조체에 대 한 포인터를 반환 합니다. 정보를 묻는 `ppvOptions`합니다.

 사용자가 **고급** 다시 동일한 대화 상자에서 IDE를 호출 합니다 `SccGetCommandOptions` 함수를 변경 하지 않고 다시 `ppvOptions`구조 플러그 인에 다시 전달 되는 합니다. 이 통해 사용자가 이전에 설정한 값으로 해당 대화 상자를 다시 초기화 하도록 플러그 인. 플러그 인을 반환 하기 전에 내부 구조를 수정합니다.

 마지막으로 클릭할 때 **확인** ide의 **가져오기** 대화 상자에서 IDE 호출 하 여는 [SccGet](../extensibility/sccget-function.md)에서 반환 하는 구조체를 전달 `ppvOptions` 를 포함 하는 고급 옵션입니다.

> [!NOTE]
> 명령을 `SCC_COMMAND_OPTIONS` IDE를 표시 하는 경우 사용 되는 **옵션** 사용자 수 있는 대화 상자에는 통합의 작동 방식을 제어 하는 기본 설정을 합니다. 표시할 수는 소스 제어 플러그 인에서 자체 기본 설정 대화 상자를 제공 하려는 경우는 **고급** IDE의 기본 설정 대화 상자에서 단추입니다. 플러그 인은 책임을 가져오고이 정보를 유지 합니다. IDE 사용 하지 않거나 수정 합니다.

## <a name="see-also"></a>참고자료
- [원본 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [명령 코드](../extensibility/command-code-enumerator.md)