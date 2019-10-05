---
title: 'Idiadatasource:: Loaddatafrompdb | Microsoft Docs'
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
ms.openlocfilehash: fb34098f8d69d3c8618c406eff9666d52eace1f2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62554146"
---
# <a name="idiadatasourceloaddatafrompdb"></a>IDiaDataSource::loadDataFromPdb
페이지를 열고 디버그 데이터 원본으로 프로그램 데이터베이스 (.pdb) 파일을 준비 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT loadDataFromPdb (
   LPCOLESTR pdbPath
);
```

#### <a name="parameters"></a>매개 변수
pdbPath

[in] .Pdb 파일에 대 한 경로입니다.

## <a name="return-value"></a>반환 값
성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다. 다음 표에서이 메서드에 대 한 가능한 반환 값을 보여 줍니다.

|값|설명|
|-----------|-----------------|
|E_PDB_NOT_FOUND|파일을 열지 못했습니다. 또는 파일에 잘못 된 형식이 있는지 확인 합니다.|
|E_PDB_FORMAT|사용 되지 않는 형식으로 파일에 액세스 하려고 했습니다.|
|E_INVALIDARG|잘못된 매개 변수입니다.|
|E_UNEXPECTED|데이터 원본에 이미 준비 합니다.|

## <a name="remarks"></a>설명
이 메서드는.pdb 파일에서 직접 디버그 데이터를 로드합니다.

특정 조건에 대해.pdb 파일의 유효성을 검사 하려면 사용 합니다 [idiadatasource:: Loadandvalidatedatafrompdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) 메서드.

(콜백 메커니즘을)를 통해 데이터 로드 프로세스에 대 한 액세스 권한을 사용 합니다 [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) 메서드.

메모리에서 직접.pdb 파일을 로드 하려면 사용 합니다 [idiadatasource:: Loaddatafromistream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) 메서드.

## <a name="example"></a>예제

```C++
HRESULT hr = pSource->loadDataFromPdb( L"myprog.pdb" );
if (FAILED(hr))
{
    // report error
}
```

## <a name="see-also"></a>참고 항목
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)
- [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
