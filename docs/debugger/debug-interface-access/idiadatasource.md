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
ms.openlocfilehash: 453be1d77f1d2b1759e3de4433225cf97d026054
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744914"
---
# <a name="idiadatasource"></a>IDiaDataSource
디버깅 기호의 소스에 대 한 액세스를 시작 합니다.

## <a name="syntax"></a>구문

```
IDiaDataSource : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
다음 표에서는 `IDiaDataSource`의 메서드를 보여 줍니다.

|메서드|설명|
|------------|-----------------|
|[IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)|마지막 로드 오류에 대 한 파일 이름을 검색 합니다.|
|[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)|프로그램 데이터베이스 (.pdb) 파일을 열고 디버그 데이터 소스로 준비 합니다.|
|[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)|프로그램 데이터베이스 (.pdb) 파일이 제공 된 서명 정보와 일치 하는지 확인 하 고 확인 합니다. .pdb 파일을 디버그 데이터 소스로 준비 합니다.|
|[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)|.Exe/.dll 파일과 연결 된 디버그 데이터를 열고 준비 합니다.|
|[IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)|메모리 내 데이터 스트림을 통해 액세스 되는 프로그램 데이터베이스 (.pdb) 파일에 저장 된 디버그 데이터를 준비 합니다.|
|[IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)|기호 쿼리를 위한 세션을 엽니다.|

## <a name="remarks"></a>주의
@No__t_0 인터페이스의 load 메서드 중 하나를 호출 하면 기호 소스가 열립니다. [IDiaDataSource:: openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) 메서드를 성공적으로 호출 하면 데이터 소스 쿼리를 지 원하는 [IDiaSession](../../debugger/debug-interface-access/idiasession.md) 인터페이스를 반환 합니다. Load 메서드에서 파일 관련 오류를 반환 하는 경우 [IDiaDataSource:: get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md) 메서드 반환 값에는 오류와 연결 된 파일 이름이 포함 됩니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
이 인터페이스는 클래스 식별자 `CLSID_DiaSource` 및 `IID_IDiaDataSource`의 인터페이스 ID를 사용 하 여 `CoCreateInstance` 함수를 호출 하 여 가져옵니다. 이 예제에서는이 인터페이스를 가져오는 방법을 보여 줍니다.

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
헤더: Dia2

라이브러리: diaguids

DLL: msdia80

## <a name="see-also"></a>참조
- [인터페이스(디버그 인터페이스 액세스 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
