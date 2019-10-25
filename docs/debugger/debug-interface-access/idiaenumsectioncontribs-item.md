---
title: 'IDiaEnumSectionContribs:: Item | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Item method
ms.assetid: 63a28f23-0ca0-44a7-b11b-ca0206d642a0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d021b5016bd0e0039f2bf175102dc44f04dabaab
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744301"
---
# <a name="idiaenumsectioncontribsitem"></a>IDiaEnumSectionContribs::Item
인덱스를 사용 하 여 섹션 기여를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT Item ( 
   DWORD                index,
   IDiaSectionContrib** section
);
```

#### <a name="parameters"></a>매개 변수
 인덱스입니다.

진행 검색할 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) 개체의 인덱스입니다. 인덱스의 범위는 0 ~ `count`-1입니다. 여기서 `count`는 [IDiaEnumSectionContribs:: get_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md) 메서드에서 반환 됩니다.

 section

제한이 원하는 섹션 기여를 나타내는 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="see-also"></a>참조
- [IDiaEnumSectionContribs::get_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)