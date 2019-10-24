---
title: 'IDiaSymbol:: get_classParent | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_classParent method
ms.assetid: 99db875a-caae-4d60-ae70-64bc8a9f6fba
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 36dfed97fb8abd30f97c4068da94148715cae5c7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740848"
---
# <a name="idiasymbolget_classparent"></a>IDiaSymbol::get_classParent
기호의 클래스 부모에 대 한 참조를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_classParent ( 
   IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

제한이 기호의 클래스 부모를 나타내는 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 `S_FALSE` 또는 오류 코드를 반환 합니다.

> [!NOTE]
> @No__t_0의 반환 값은 해당 속성을 기호에 사용할 수 없음을 의미 합니다.

## <a name="requirements"></a>요구 사항

|요구 사항|설명|
|-----------------|-----------------|
|헤더:|dia2.h|
|버전:|DIA SDK v7.0|

## <a name="remarks"></a>주의
 클래스 부모가 될 수 있는 기호 형식은 [기호 형식의 클래스 계층 구조](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)에 설명 되어 있습니다.

## <a name="see-also"></a>참조
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [기호 형식의 클래스 계층 구조](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)