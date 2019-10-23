---
title: NameSearchOptions | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NameSearchOptions enumeration
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 61905c0c6c40d893cc8723b711d67690133a7155
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738620"
---
# <a name="namesearchoptions"></a>NameSearchOptions
기호 및 파일 이름에 대 한 검색 옵션을 지정 합니다.

## <a name="syntax"></a>구문

```C++
enum NameSearchOptions {
    nsNone,
    nsfCaseSensitive     = 0x1,
    nsfCaseInsensitive   = 0x2,
    nsfFNameExt          = 0x4,
    nsfRegularExpression = 0x8,
    nsfUndecoratedName   = 0x10,

// For backward compatibility:
    nsCaseSensitive           = nsfCaseSensitive,
    nsCaseInsensitive         = nsfCaseInsensitive,
    nsFNameExt                = nsfCaseInsensitive | nsfFNameExt,
    nsRegularExpression       = nsfRegularExpression | nsfCaseSensitive,
    nsCaseInRegularExpression = nsfRegularExpression | nsfCaseInsensitive
};
```

## <a name="elements"></a>요소
`nsNone` 지정된 옵션이 없습니다.

`nsfCaseSensitive`는 대/소문자를 구분 하는 이름 일치를 적용 합니다.

`nsfCaseInsensitive`는 대/소문자를 구분 하지 않는 이름 일치를 적용 합니다.

`nsfFNameExt`는 이름을 경로로 처리 하 고 파일 이름. ext 이름 일치를 적용 합니다.

`nsfRegularExpression`는 별표 (*) 및 물음표 (?)를 와일드 카드로 사용 하 여 대/소문자를 구분 하는 이름 일치를 적용 합니다. 다른 일반 정규식 문자는 지원 되지 않습니다.

`nsfUndecoratedName`은 데코레이팅되지 않은 이름과 데코레이팅된 이름을 모두 포함 하는 기호에만 적용 됩니다.

## <a name="remarks"></a>주의
이 열거형의 값은 다음 메서드에 전달 됩니다.

- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)

- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)

- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)

## <a name="requirements"></a>요구 사항
헤더: dia2

## <a name="see-also"></a>참조
- [열거형 및 구조체](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
