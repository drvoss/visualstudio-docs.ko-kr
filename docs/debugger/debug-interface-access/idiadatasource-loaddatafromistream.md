---
title: 'IDiaDataSource:: loadDataFromIStream | Microsoft Docs'
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
ms.openlocfilehash: b2bcf657b4404ed72059351175d124a9c07abb46
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744948"
---
# <a name="idiadatasourceloaddatafromistream"></a>IDiaDataSource::loadDataFromIStream
메모리 내 데이터 스트림을 통해 액세스 되는 프로그램 데이터베이스 (.pdb) 파일에 저장 된 디버그 데이터를 준비 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT loadDataFromIStream ( 
   IStream* pIStream
);
```

#### <a name="parameters"></a>매개 변수
 pIStream

진행 사용할 데이터 스트림을 나타내는 <xref:IStream> 개체입니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다. 다음 표에서는이 메서드에 사용할 수 있는 반환 값을 보여 줍니다.

|값|설명|
|-----------|-----------------|
|E_PDB_FORMAT|사용 되지 않는 형식으로 파일에 액세스 하려고 했습니다.|
|E_INVALIDARG|잘못된 매개 변수입니다.|
|E_UNEXPECTED|데이터 원본이 이미 준비 되었습니다.|

## <a name="remarks"></a>주의
 이 메서드를 사용 하면 <xref:IStream> 개체를 통해 메모리에서 실행 파일의 디버그 데이터를 가져올 수 있습니다.

 유효성 검사 없이 .pdb 파일을 로드 하려면 [IDiaDataSource:: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) 메서드를 사용 합니다.

 특정 조건에 대해 .pdb 파일의 유효성을 검사 하려면 [IDiaDataSource:: loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) 메서드를 사용 합니다.

 콜백 메커니즘을 통해 데이터 로드 프로세스에 대 한 액세스 권한을 얻으려면 [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) 메서드를 사용 합니다.

## <a name="see-also"></a>참조
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)
- [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)