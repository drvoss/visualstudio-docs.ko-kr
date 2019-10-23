---
title: 'IDiaDataSource:: get_lastError | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::get_lastError method
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 48595dda70560f555533a1857f73db4d7bd20a86
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744970"
---
# <a name="idiadatasourceget_lasterror"></a>IDiaDataSource::get_lastError
마지막 로드 오류에 대 한 파일 이름을 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_lastError (
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 pRetVal

제한이 마지막 로드 오류와 연결 된 .pdb 파일 이름을 포함 하는 문자열을 반환 합니다.

## <a name="return-value"></a>반환 값
 로드 작업으로 인해 발생 한 마지막 오류 코드를 반환 합니다. @No__t_1 매개 변수가 `NULL` 경우 `E_INVALIDARG`를 반환 합니다.

## <a name="example"></a>예제

```C++
BSTR    fileName;
HRESULT errorCode = pSource->get_lastError( &fileName );
```

## <a name="see-also"></a>참조
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)