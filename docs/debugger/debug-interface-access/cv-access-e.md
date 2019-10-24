---
title: CV_access_e | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bbe338ba9d3aa6cbc795606c3fa285526afdfd36
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745364"
---
# <a name="cv_access_e"></a>CV_access_e
멤버 함수 및 변수의 표시 여부 (액세스 수준) 범위를 지정 합니다.

## <a name="syntax"></a>구문

```C++
typedef enum CV_access_e {
    CV_private   = 1,
    CV_protected = 2,
    CV_public    = 3
} CV_access_e;
```

## <a name="elements"></a>요소
CV_private 멤버에 개인 액세스 권한이 있습니다.

CV_protected Member에 보호 된 액세스 권한이 있습니다.

CV_public Member에 공용 액세스 권한이 있습니다.

## <a name="remarks"></a>주의
@No__t_0 액세스 지정자는 클래스의 private 및 protected 요소 모두에 액세스할 수 있는 비 멤버 함수에서 일반적으로 사용 되기 때문에 여기에 포함 되지 않습니다. [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) 메서드를 사용 하 여 `SymTagFriend` 액세스 권한을 가진 기호를 찾습니다.

## <a name="requirements"></a>요구 사항
헤더: cvconst

## <a name="see-also"></a>참조
- [열거형 및 구조체](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)
- [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
