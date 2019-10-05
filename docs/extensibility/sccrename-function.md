---
title: SccRename 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRename
helpviewer_keywords:
- SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1329f847f7f961bf4c792cbdf7f40f8f04b1694c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338724"
---
# <a name="sccrename-function"></a>SccRename 함수
이 함수에는 소스 제어 시스템에서 파일을 이름을 바꿉니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccRename(
   LPVOID pvContext,
   HWND   hWnd,
   LPCSTR lpFileName,
   LPCSTR lpNewName
);
```

#### <a name="parameters"></a>매개 변수
 pvContext

[in] 원본 제어 플러그 인 상황에 맞는 구조입니다.

 hWnd

[in] 소스 제어 플러그 인을 제공 하는 모든 대화 상자에 대 한 부모로 사용할 수 있는 IDE 창 핸들입니다.

 lpFileName

[in] 이름을 바꿀 파일의 정규화 된 파일 이름입니다.

 lpNewName

[in] 정규화 된 새 이름입니다. 디렉터리 경로 다른 경우 다음 파일이 이동 한 하위 디렉터리에서 다른 합니다.

## <a name="return-value"></a>반환 값
 원본 제어 플러그 인이 함수의 구현은 다음 값 중 하나를 반환 하:

|값|설명|
|-----------|-----------------|
|SCC_OK|이름 바꾸기 작업을 완료 했습니다.|
|SCC_E_PROJNOTOPEN|프로젝트 소스 제어에서 열려 있지 않습니다.|
|SCC_E_FILENOTCONTROLLED|소스 제어를 파일이 없습니다.|
|SCC_E_ACCESSFAILURE|소스 제어 시스템에 경합 또는 네트워크 문제로 인해 액세스 문제가 있습니다.|
|SCC_E_NOTAUTHORIZED|사용자는이 작업을 완료할 권한이 없습니다.|
|SCC_E_COULDNOTCREATEPROJECT|이름 바꾸기 프로세스의 일부로 프로젝트를 만들 수 없습니다.|
|SCC_E_OPNOTPERFORMED|작업을 수행 하지 않았습니다.|
|SCC_E_NONSPECIFICERROR|지정 되지 않은 또는 일반 오류가 발생 했습니다.|

## <a name="remarks"></a>설명
 파일 이름 바꾸기 또는 이동 한 위치에서 다른 소스 제어 시스템에서이 함수를 사용할 수 있습니다. 소스 제어 플러그 인 디스크에 있는 파일에 액세스 하지 않아야 합니다. 이 값은 로컬 파일의 이름을 바꾸려면 IDE의 책임입니다.

## <a name="see-also"></a>참고 항목
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)