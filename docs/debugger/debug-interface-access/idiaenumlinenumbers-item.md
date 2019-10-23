---
title: 'IDiaEnumLineNumbers:: Item | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::Item method
ms.assetid: 08efbeaf-22f7-49e9-96a8-bb906dfe4fd8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9bba71efce68864b8737011ab7dda5cb8da3267c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744407"
---
# <a name="idiaenumlinenumbersitem"></a>IDiaEnumLineNumbers::Item
인덱스를 통해 줄 번호를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT Item ( 
   DWORD            index,
   IDiaLineNumber** lineNumber
);
```

#### <a name="parameters"></a>매개 변수
 인덱스입니다.

진행 검색할 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) 개체의 인덱스입니다. 인덱스의 범위는 0 ~ `count`-1입니다. 여기서 `count`는 [IDiaEnumLineNumbers:: get_Count](../../debugger/debug-interface-access/idiaenumlinenumbers-get-count.md) 메서드에서 반환 됩니다.

 lineNumber

제한이 원하는 줄 번호를 나타내는 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="see-also"></a>참조
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)