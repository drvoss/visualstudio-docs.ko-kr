---
title: 'IDiaEnumTables:: Item | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Item method
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf2d6b14f17d42a128e59446e27bfc251de40d17
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743746"
---
# <a name="idiaenumtablesitem"></a>IDiaEnumTables::Item
인덱스 또는 이름을 사용 하 여 테이블을 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT Item ( 
   VARIANT     index,
   IDiaTable** table
);
```

#### <a name="parameters"></a>매개 변수
 `index`

진행 검색할 [IDiaTable](../../debugger/debug-interface-access/idiatable.md) 의 인덱스 또는 이름입니다. 정수 variant를 사용 하는 경우 0에서 `count`-1 사이의 범위에 있어야 합니다. 여기서 `count`는 [IDiaEnumTables:: get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md) 메서드에서 반환 됩니다.

 `table`

제한이 원하는 테이블을 나타내는 [IDiaTable](../../debugger/debug-interface-access/idiatable.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>주의
 문자열 변형이 지정 된 경우 문자열은 특정 테이블의 이름을 지정 합니다. 이름은 [상수 (Debug Interface Access SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)에 정의 된 테이블 이름 중 하나 여야 합니다.

## <a name="example"></a>예제

```C++
VARIANT var;
var.vt = VT_BSTR;
var.bstrVal = SysAllocString(DiaTable_Symbols );
IDiaTable* pTable;
pEnumTables->Item( var, &pTable );
```

## <a name="see-also"></a>참조
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)
- [상수(디버그 인터페이스 액세스 SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)