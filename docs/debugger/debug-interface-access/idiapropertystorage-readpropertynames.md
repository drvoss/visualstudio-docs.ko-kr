---
title: 'IDiaPropertyStorage:: ReadPropertyNames | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f554485ae56a9d5f190c749879545165d299531c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742863"
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
지정 된 속성 식별자에 해당 하는 문자열 이름을 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT ReadPropertyNames (
   ULONG         cpropid,
   PROPID const* rgpropid,
   BSTR*         rglpwstrName
);
```

#### <a name="parameters"></a>매개 변수
 `cpropid`

진행 @No__t_0의 속성 id 수입니다.

 `rgpropid`

진행 이름을 가져올 속성 id의 배열입니다 (`PROPID`은 WTypes. h에서 `ULONG`로 정의 됨).

 `rglpwstrName`

[in, out] 지정 된 속성 id의 속성 이름 배열입니다. 요청 된 수의 속성 이름을 보유 하기 위해 배열을 미리 할당 해야 하며 적어도 `cpropid``BSTR` 문자열을 보유할 수 있어야 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>주의
 반환 된 속성 이름은 더 이상 필요 하지 않은 경우 `SysFreeString` 함수를 호출 하 여 해제 해야 합니다.

## <a name="see-also"></a>참조
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)