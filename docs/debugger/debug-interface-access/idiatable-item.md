---
title: 'IDiaTable:: Item | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d402f5ad54d5c0f487cebb3a8c53f68d17828ed4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738722"
---
# <a name="idiatableitem"></a>IDiaTable::Item
테이블에서 지정 된 항목에 대 한 참조를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT Item ( 
   DWORD      index,
   IUnknown** element
);
```

#### <a name="parameters"></a>매개 변수
 `index`

진행 [IDiaTable:: get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)메서드에서 `count`을 반환 `count` 하는 0에서 1 사이의 범위에 있는 테이블 항목의 인덱스입니다.

 `element`

제한이 지정 된 테이블 항목을 나타내는 `IUnknown` 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>주의
 테이블은 개체의 컬렉션을 나타냅니다. 이러한 개체에 따라 요소 매개 변수를 적절 한 인터페이스로 캐스팅할 수 있습니다. 예를 들어 테이블에 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) 개체가 포함 되어 있는 경우 요소 매개 변수를 `IDiaSegment` 인터페이스로 캐스팅할 수 있습니다.

 [IDiaTable](../../debugger/debug-interface-access/idiatable.md) 인터페이스에서 적절 한 열거자 인터페이스에 대 한 `QueryInterface` 메서드를 호출 하 고, 열거자의 특정 메서드를 사용 하 여 테이블 내용에 액세스 하는 것이 더 일반적인 방법입니다. 예는 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) 인터페이스를 참조 하세요.

## <a name="see-also"></a>참조
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)