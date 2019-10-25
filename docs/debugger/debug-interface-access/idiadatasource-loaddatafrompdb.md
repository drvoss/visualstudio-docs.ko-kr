---
title: 'IDiaDataSource:: loadDataFromPdb | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromPdb method
ms.assetid: 02159073-8144-47f8-a0b0-aa0edcb92b5b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7526ba6e62c9df22a2338adc80f5d56578502cdb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744933"
---
# <a name="idiadatasourceloaddatafrompdb"></a>IDiaDataSource::loadDataFromPdb
프로그램 데이터베이스 (.pdb) 파일을 열고 디버그 데이터 소스로 준비 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT loadDataFromPdb (
   LPCOLESTR pdbPath
);
```

#### <a name="parameters"></a>매개 변수
pdbPath

진행 .Pdb 파일의 경로입니다.

## <a name="return-value"></a>반환 값
성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다. 다음 표에서는이 메서드에 사용할 수 있는 반환 값을 보여 줍니다.

|값|설명|
|-----------|-----------------|
|E_PDB_NOT_FOUND|파일을 열지 못했거나 파일의 형식이 잘못 되었음을 확인 했습니다.|
|E_PDB_FORMAT|사용 되지 않는 형식으로 파일에 액세스 하려고 했습니다.|
|E_INVALIDARG|잘못된 매개 변수입니다.|
|E_UNEXPECTED|데이터 원본이 이미 준비 되었습니다.|

## <a name="remarks"></a>주의
이 메서드는 .pdb 파일에서 디버그 데이터를 직접 로드 합니다.

특정 조건에 대해 .pdb 파일의 유효성을 검사 하려면 [IDiaDataSource:: loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) 메서드를 사용 합니다.

콜백 메커니즘을 통해 데이터 로드 프로세스에 대 한 액세스 권한을 얻으려면 [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) 메서드를 사용 합니다.

메모리에서 직접 .pdb 파일을 로드 하려면 [IDiaDataSource:: loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) 메서드를 사용 합니다.

## <a name="example"></a>예제

```C++
HRESULT hr = pSource->loadDataFromPdb( L"myprog.pdb" );
if (FAILED(hr))
{
    // report error
}
```

## <a name="see-also"></a>참조
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)
- [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
