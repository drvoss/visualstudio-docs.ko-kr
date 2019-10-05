---
title: 'Idiadatasource:: Loaddatafromistream | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromIStream method
ms.assetid: 8fe33eea-1457-4b8c-ae19-f1ede5578483
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb9b218935085b04ae1a9931733aeca34766aa5f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62833688"
---
# <a name="idiadatasourceloaddatafromistream"></a>IDiaDataSource::loadDataFromIStream
메모리 내 데이터 스트림을 통해 액세스 하 여 프로그램 데이터베이스 (.pdb) 파일에 저장 된 디버그 데이터를 준비 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT loadDataFromIStream ( 
   IStream* pIStream
);
```

#### <a name="parameters"></a>매개 변수
 pIStream

[in] <xref:IStream> 를 사용 하 여 데이터 스트림을 나타내는 개체입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다. 다음 표에서이 메서드에 대 한 가능한 반환 값을 보여 줍니다.

|값|설명|
|-----------|-----------------|
|E_PDB_FORMAT|사용 되지 않는 형식으로 파일에 액세스 하려고 했습니다.|
|E_INVALIDARG|잘못된 매개 변수입니다.|
|E_UNEXPECTED|데이터 원본에 이미 준비 합니다.|

## <a name="remarks"></a>설명
 이 메서드는 실행 파일을 통해 메모리를 얻을 수에 대 한 디버그 데이터를 사용 하면는 <xref:IStream> 개체입니다.

 유효성 검사 없이.pdb 파일을 로드 하려면 사용 합니다 [idiadatasource:: Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) 메서드.

 특정 조건에 대해.pdb 파일의 유효성을 검사 하려면 사용 합니다 [idiadatasource:: Loadandvalidatedatafrompdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) 메서드.

 (콜백 메커니즘을)를 통해 데이터 로드 프로세스에 대 한 액세스 권한을 사용 합니다 [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) 메서드.

## <a name="see-also"></a>참고 항목
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)
- [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)