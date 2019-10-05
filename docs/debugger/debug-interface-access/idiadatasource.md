---
title: IDiaDataSource | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource interface
ms.assetid: 6260ac76-4f9d-4144-ba22-32f8620b32c2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b8618cc3484584430bbe3ae3fde59b6e5d5fc78
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62838521"
---
# <a name="idiadatasource"></a>IDiaDataSource
디버깅 기호가 소스에 액세스를 시작 합니다.

## <a name="syntax"></a>구문

```
IDiaDataSource : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
다음 표에서의 메서드를 보여 줍니다. `IDiaDataSource`합니다.

|메서드|설명|
|------------|-----------------|
|[IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)|마지막 로드 오류에 대 한 파일 이름을 검색합니다.|
|[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)|페이지를 열고 디버그 데이터 원본으로 프로그램 데이터베이스 (.pdb) 파일을 준비 합니다.|
|[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)|열리고 프로그램 데이터베이스 (.pdb) 파일 제공; 서명 정보가 일치 하는지 확인 디버그 데이터 소스로.pdb 파일을 준비합니다.|
|[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)|열리고.exe/.dll 파일과 관련 된 디버그 데이터를 준비 합니다.|
|[IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)|메모리 내 데이터 스트림을 통해 액세스 하 여 프로그램 데이터베이스 (.pdb) 파일에 저장 된 디버그 데이터를 준비 합니다.|
|[IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)|기호를 쿼리 하는 것에 대 한 세션을 엽니다.|

## <a name="remarks"></a>설명
load 메서드 중 하나를 호출 하 여 `IDiaDataSource` 인터페이스 사용 하면 기호 원본이 열립니다. 호출에 성공한를 [idiadatasource:: Opensession](../../debugger/debug-interface-access/idiadatasource-opensession.md) 메서드가 반환 되는 [IDiaSession](../../debugger/debug-interface-access/idiasession.md) 데이터 원본 쿼리를 지 원하는 인터페이스입니다. Load 메서드 파일 관련 오류를 반환 하는 경우 해당 [idiadatasource:: Get_lasterror](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md) 메서드 반환 값은 오류와 관련 된 파일 이름을 포함 합니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
이 인터페이스를 호출 하 여 가져온 합니다 `CoCreateInstance` 클래스 식별자를 사용 하 여 함수 `CLSID_DiaSource` 와의 인터페이스 ID `IID_IDiaDataSource`합니다. 이 인터페이스는 가져오는 방법을 보여 줍니다.

## <a name="example"></a>예제

```C++

      IDiaDataSource* pSource;
HRESULT hr = CoCreateInstance(CLSID_DiaSource,
                              NULL,
                              CLSCTX_INPROC_SERVER,
                              IID_IDiaDataSource,
                              (void**) &pSource);
if (FAILED(hr))
{
    // Report error and exit
}
```

## <a name="requirements"></a>요구 사항
헤더: Dia2.h

라이브러리: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>참고 항목
- [인터페이스(디버그 인터페이스 액세스 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
