---
title: 'IDiaDataSource:: loadDataForExe | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataForExe method
ms.assetid: d94a1068-f53f-44b5-b6fb-00dec361a7f2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7a86abb00ebc090c37f03a5533376ae0b9c3e8ae
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744965"
---
# <a name="idiadatasourceloaddataforexe"></a>IDiaDataSource::loadDataForExe
.Exe/.dll 파일과 연결 된 디버그 데이터를 열고 준비 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT loadDataForExe (
   LPCOLESTR executable,
   LPCOLESTR searchPath,
   IUnknown* pCallback
);
```

#### <a name="parameters"></a>매개 변수
executable

진행 .Exe 또는 .dll 파일의 경로입니다.

searchPath

진행 디버그 데이터를 검색할 대체 경로입니다.

pCallback

진행 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md), [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md), [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)및/또는 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) 인터페이스와 같은 디버그 콜백 인터페이스를 지 원하는 개체에 대 한 `IUnknown` 인터페이스입니다.

## <a name="return-value"></a>반환 값
성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다. 다음 표에서는이 메서드에 사용할 수 있는 몇 가지 오류 코드를 보여 줍니다.

|값|설명|
|-----------|-----------------|
|E_PDB_NOT_FOUND|파일을 열지 못했거나 파일의 형식이 잘못 되었습니다.|
|E_PDB_FORMAT|사용 되지 않는 형식으로 파일에 액세스 하려고 했습니다.|
|E_PDB_INVALID_SIG|서명이 일치 하지 않습니다.|
|E_PDB_INVALID_AGE|Age가 일치 하지 않습니다.|
|E_INVALIDARG|잘못된 매개 변수입니다.|
|E_UNEXPECTED|데이터 원본이 이미 준비 되었습니다.|

## <a name="remarks"></a>주의
.Exe/.dll 파일의 debug 헤더는 연결 된 디버그 데이터 위치의 이름을로 합니다.

이 메서드는 디버그 헤더를 읽은 다음 디버그 데이터를 검색 하 고 준비 합니다. 검색 진행률이 선택적으로 보고 되 고 콜백을 통해 제어 될 수 있습니다. 예를 들어, [IDiaLoadCallback:: NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md) 는 `IDiaDataSource::loadDataForExe` 메서드가 디버그 디렉터리를 찾아 처리할 때 호출 됩니다.

[IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) 및 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) 인터페이스를 사용 하 여 클라이언트 응용 프로그램은 표준에서 파일에 직접 액세스할 수 없는 경우 실행 파일에서 데이터를 읽는 대체 메서드를 제공할 수 있습니다. 파일 i/o.

유효성 검사 없이 .pdb 파일을 로드 하려면 [IDiaDataSource:: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) 메서드를 사용 합니다.

특정 조건에 대해 .pdb 파일의 유효성을 검사 하려면 [IDiaDataSource:: loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) 메서드를 사용 합니다.

메모리에서 직접 .pdb 파일을 로드 하려면 [IDiaDataSource:: loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) 메서드를 사용 합니다.

## <a name="example"></a>예제

```C++
class MyCallBack: public IDiaLoadCallback
{
...
};
MyCallBack callback;
...
HRESULT hr = pSource->loadDataForExe( L"myprog.exe", L".\debug", (IUnknown*)&callback);
if (FAILED(hr))
{
    // Report error
}
```

## <a name="see-also"></a>참조
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
- [IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)
- [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)
- [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
