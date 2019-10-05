---
title: QUERYCHANGESFUNC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- QUERYCHANGESFUNC
helpviewer_keywords:
- QUERYCHANGESFUNC callback function
- QUERYCHANGESDATA structure
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8ac0003d26296a25659debbab3352e4e37cbf2ec
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334405"
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
이에서 사용 하는 콜백 함수는 [SccQueryChanges](../extensibility/sccquerychanges-function.md) 파일 이름의 컬렉션을 열거 하 고 각 파일의 상태를 확인 하는 작업입니다.

 합니다 `SccQueryChanges` 목록을 파일에 대 한 포인터를 지정 하는 함수는 `QUERYCHANGESFUNC` 콜백 합니다. 소스 제어 플러그 인 지정된 된 목록을 열거 하 고 목록에서 각 파일에 대 한 (이 콜백)을 통해 상태를 제공 합니다.

## <a name="signature"></a>서명

```cpp
typedef BOOL (*QUERYCHANGESFUNC)(
   LPVOID pvCallerData,
   QUERYCHANGESDATA * pChangesData
);
```

## <a name="parameters"></a>매개 변수
 pvCallerData

[in] 합니다 `pvCallerData` (IDE) 호출자가 매개 변수 전달 [SccQueryChanges](../extensibility/sccquerychanges-function.md)합니다. 소스 제어 플러그 인이 값의 콘텐츠에 대 한 가정을 하지 확인 해야 합니다.

 pChangesData

[in] 에 대 한 포인터를 [QUERYCHANGESDATA 구조](#LinkQUERYCHANGESDATA) 파일에 변경 내용을 설명 하는 구조입니다.

## <a name="return-value"></a>반환 값
 IDE에는 적절 한 오류 코드를 반환합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|계속 처리 합니다.|
|SCC_I_OPERATIONCANCELED|처리를 중지 합니다.|
|SCC_E_xxx|적절 한 SCC 오류 처리를 중지 해야 합니다.|

## <a name="LinkQUERYCHANGESDATA"></a> QUERYCHANGESDATA 구조
 각 파일에 전달 된 구조체는 다음과 같습니다.

```cpp
struct QUERYCHANGESDATA_A
{
    DWORD  dwSize;
    LPCSTR lpFileName;
    DWORD  dwChangeType;
    LPCSTR lpLatestName;
};

typedef struct QUERYCHANGESDATA_A QUERYCHANGESDATA;

struct QUERYCHANGESDATA_W
{
    DWORD   dwSize;
    LPCWSTR lpFileName;
    DWORD   dwChangeType;
    LPCWSTR lpLatestName;
};
```

 dwSize 바이트 단위로이 구조체의 크기입니다.

 이 항목에 대 한 원래 파일 이름이 lpFileName 합니다.

 dwChangeType 파일의 나타내는 상태 코드:

|코드|설명|
|----------|-----------------|
|`SCC_CHANGE_UNKNOWN`|변경 된 내용을 확인할 수 없습니다.|
|`SCC_CHANGE_UNCHANGED`|이 파일의 이름이 변경 되지 않았습니다.|
|`SCC_CHANGE_DIFFERENT`|다른 id 사용 하 여 파일 이름이 같은 데이터베이스에 존재 하지만 합니다.|
|`SCC_CHANGE_NONEXISTENT`|파일에는 로컬로 또는 데이터베이스에 존재 하지 않습니다.|
|`SCC_CHANGE_DATABASE_DELETED`|데이터베이스에서 삭제 하는 파일입니다.|
|`SCC_CHANGE_LOCAL_DELETED`|파일을 로컬로 삭제 되지만 파일이 데이터베이스에 여전히 존재 합니다. 이 결정할 수 없는 경우 반환 `SCC_CHANGE_DATABASE_ADDED`합니다.|
|`SCC_CHANGE_DATABASE_ADDED`|파일은 데이터베이스에 추가 되지만 로컬로 존재 하지 않습니다.|
|`SCC_CHANGE_LOCAL_ADDED`|파일은 데이터베이스에 존재 하지 않습니다 하 고 새 로컬 파일입니다.|
|`SCC_CHANGE_RENAMED_TO`|파일에서 데이터베이스를 이동 하거나 이름이 바뀐 `lpLatestName`합니다.|
|`SCC_CHANGE_RENAMED_FROM`|파일의 데이터베이스에서 이동 하거나 이름이 바뀐 `lpLatestName`는 경우이 추적 하려면 비용이 너무 많이 반환 다른 플래그와 같은 `SCC_CHANGE_DATABASE_ADDED`합니다.|

 이 항목에 대 한 현재 파일 이름 lpLatestName입니다.

## <a name="see-also"></a>참고자료
- [IDE에 의해 구현 된 콜백 함수](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccQueryChanges](../extensibility/sccquerychanges-function.md)
- [오류 코드](../extensibility/error-codes.md)