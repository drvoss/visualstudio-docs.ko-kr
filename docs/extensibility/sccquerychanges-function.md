---
title: SccQueryChanges 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e2b1e504bef3ec9507afcddf4f75bc5f697e843
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353510"
---
# <a name="sccquerychanges-function"></a>SccQueryChanges 함수
이 함수는 지정 된 콜백 함수를 통해 각 파일에 대 한 이름 변경에 대 한 정보를 제공 하는 파일 목록을 열거 합니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccQueryChanges(
   LPVOID           pContext,
   LONG             nFiles,
   LPCSTR*          lpFileNames,
   QUERYCHANGESFUNC pfnCallback,
   LPVOID           pvCallerData
);
```

#### <a name="parameters"></a>매개 변수
 pContext

[in] 원본 제어 플러그 인 컨텍스트 포인터입니다.

 nFiles

[in] 파일 수가 `lpFileNames` 배열입니다.

 lpFileNames

[in] 정보를 가져올 파일 이름의 배열입니다.

 pfnCallback

[in] 콜백 함수 목록의 각 파일 이름에 대 한 호출 (참조 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) 세부 정보에 대 한).

 pvCallerData

[in] 콜백 함수에 전달 되는 값을 변경 되지 않습니다.

## <a name="return-value"></a>반환 값
 원본 제어 플러그 인이 함수의 구현은 다음 값 중 하나를 반환 하:

|값|설명|
|-----------|-----------------|
|SCC_OK|쿼리 프로세스를 완료 합니다.|
|SCC_E_PROJNOTOPEN|프로젝트 소스 제어에서 열리지 않았습니다.|
|SCC_E_ACCESSFAILURE|소스 제어 시스템에 경합 또는 네트워크 문제로 인해 액세스 문제가 있습니다.|
|SCC_E_NONSPECIFICERROR|지정 되지 않은 또는 일반 오류가 발생 했습니다.|

## <a name="remarks"></a>설명
 네임 스페이스는 변경에 대 한 쿼리 중인: 특히, 이름 바꾸기, 추가 및 파일을 제거 합니다.

## <a name="see-also"></a>참고 항목
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)
- [오류 코드](../extensibility/error-codes.md)