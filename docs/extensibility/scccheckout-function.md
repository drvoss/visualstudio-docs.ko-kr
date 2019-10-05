---
title: SccCheckout 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e5160a2600a8eb3250702dd0836d812b668a3d1b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333884"
---
# <a name="scccheckout-function"></a>SccCheckout 함수
정규화 된 파일 이름 목록이 들어이 함수 체크 로컬 드라이브에 있습니다. 체크 아웃 되 고 모든 파일에 주석을 적용 됩니다. 주석 인수 수를 `null` 문자열입니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccCheckout (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LPCSTR    lpComment,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>매개 변수
 pvContext

[in] 원본 제어 플러그 인 상황에 맞는 구조입니다.

 hWnd

[in] 소스 제어 플러그 인을 제공 하는 모든 대화 상자에 대 한 부모로 사용할 수 있는 IDE 창 핸들입니다.

 nFiles

[in] 체크 아웃할 수를 선택 하는 파일 수입니다.

 lpFileNames

[in] 체크 아웃할 파일의 정규화 된 로컬 경로 이름 배열입니다.

 lpComment

[in] 각 체크 아웃 되 고 선택한 파일에 적용할 주석 처리 합니다.

 fOptions

[in] 명령 플래그 (참조 [특정 명령에 사용 되는 비트](../extensibility/bitflags-used-by-specific-commands.md)).

 pvOptions

[in] 원본 제어 플러그 인에 대 한 옵션입니다.

## <a name="return-value"></a>반환 값
 원본 제어 플러그 인이 함수의 구현은 다음 값 중 하나를 반환 하:

|값|설명|
|-----------|-----------------|
|SCC_OK|체크 아웃 했습니다.|
|SCC_E_FILENOTCONTROLLED|선택한 파일이 소스 코드 제어 없습니다.|
|SCC_E_ACCESSFAILURE|소스 제어 시스템에 경합 또는 네트워크 문제로 인해 액세스 문제가 있습니다. 재시도 사용 하는 것이 좋습니다.|
|SCC_E_NOTAUTHORIZED|사용자는이 작업을 수행할 수 없습니다.|
|SCC_E_NONSPECIFICERROR|알 수 없는 오류가 발생 했습니다. 파일 체크 아웃 했습니다.|
|SCC_E_ALREADYCHECKEDOUT|사용자가 이미 파일을 체크 아웃 합니다.|
|SCC_E_FILEISLOCKED|새 버전 생성 등의 금지 된 파일이 잠겨 있습니다.|
|SCC_E_FILEOUTEXCLUSIVE|다른 사용자는이 파일에는 단독 체크 아웃을 수행 했습니다.|
|SCC_I_OPERATIONCANCELED|작업이 완료 되기 전에 취소 되었습니다.|

## <a name="see-also"></a>참고자료
- [원본 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [특정 명령에 사용 되는 비트](../extensibility/bitflags-used-by-specific-commands.md)