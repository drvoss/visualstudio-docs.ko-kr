---
title: SccBackgroundGet 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d0805e91f5386f101917ee988e9e0d23d066f48d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334017"
---
# <a name="sccbackgroundget-function"></a>SccBackgroundGet 함수
이 함수는 소스 제어에서 각 지정된 된 파일의 사용자 상호 작용 없이 가져옵니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccBackgroundGet(
   LPVOID  pContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LONG    dwFlags,
   LONG    dwBackgroundOperationID
);
```

### <a name="parameters"></a>매개 변수
 pContext

[in] 원본 제어 플러그 인 컨텍스트 포인터입니다.

 nFiles

[in] 에 지정 된 파일 수는 `lpFileNames` 배열입니다.

 lpFileNames

[out에서] 검색할 파일의 이름 배열입니다.

> [!NOTE]
> 이름을 정규화 된 로컬 파일 이름 이어야 합니다.

 dwFlags

[in] 명령 플래그 (`SCC_GET_ALL`, `SCC_GET_RECURSIVE`).

 dwBackgroundOperationID

[in] 이 작업과 연결 하는 고유 값입니다.

## <a name="return-value"></a>반환 값
 원본 제어 플러그 인이 함수의 구현은 다음 값 중 하나를 반환 하:

|값|설명|
|-----------|-----------------|
|SCC_OK|작업이 완료 되었습니다.|
|SCC_E_BACKGROUNDGETINPROGRESS|백그라운드 검색을 이미 진행 (소스 제어 플러그 인 반환 해야이 동시 일괄 처리 작업을 지원 하지 않는 경우에).|
|SCC_I_OPERATIONCANCELED|작업이 완료 전에 취소 되었습니다.|

## <a name="remarks"></a>설명
 이 함수는 항상 소스 제어 플러그 인을 로드 하는 것과에서 다른 스레드에서 호출 됩니다. 이 함수는 그; 될 때까지 반환 되지 않습니다. 그러나이 호출할 수 있습니다 여러 번 동시에 모든 파일의 여러 목록을 사용 하 여.

 사용 된 `dwFlags` 인수는 동일 합니다 [SccGet](../extensibility/sccget-function.md)합니다.

## <a name="see-also"></a>참고자료
- [원본 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [SccGet](../extensibility/sccget-function.md)