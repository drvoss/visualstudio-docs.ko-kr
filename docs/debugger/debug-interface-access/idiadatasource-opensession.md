---
title: 'IDiaDataSource:: openSession | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7dd6ab61db3e3bafd594298aa41d32bce64d4941
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744928"
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
기호 쿼리를 위한 세션을 엽니다.

## <a name="syntax"></a>구문

```C++
HRESULT openSession ( 
   IDiaSession** ppSession
);
```

#### <a name="parameters"></a>매개 변수
ppSession

제한이 열려 있는 세션을 나타내는 [IDiaSession](../../debugger/debug-interface-access/idiasession.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다. 다음 표에서는이 메서드에 사용할 수 있는 반환 값을 보여 줍니다.

|값|설명|
|-----------|-----------------|
|E_UNEXPECTED|[IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) 개체가 이전에 기호 소스를 사용 하 여 초기화 되지 않았습니다.|
|E_INVALIDARG|잘못된 `ppSession` 매개 변수입니다.|
|E_OUTOFMEMORY|메모리가 부족 하 여 세션을 열 수 없습니다.|

## <a name="remarks"></a>주의
이 메서드는 데이터 원본에 대 한 [IDiaSession](../../debugger/debug-interface-access/idiasession.md) 개체를 엽니다.

`IDiaSession` 개체는 데이터 원본에 대 한 쿼리를 구현 합니다. 세션은 각 디버그 기호 집합에 대해 하나의 주소 공간을 관리 합니다. 데이터 원본 기호에서 설명 하는 .exe 또는 .dll 파일이 여러 주소 범위에서 활성화 된 경우 (예: 여러 프로세스가 로드 되었으므로) 각 주소 범위에 대해 하나의 세션을 사용 해야 합니다.

## <a name="example"></a>예제

```C++
IDiaSession* pSession;
HRESULT hr = pSource->openSession( &pSession );
if (FAILED(hr))
{
   // report error
}
```

## <a name="see-also"></a>참조
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [개요](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [.Pdb 파일 쿼리](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)
