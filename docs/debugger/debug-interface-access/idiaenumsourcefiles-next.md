---
title: 'IDiaEnumSourceFiles:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Next method
ms.assetid: 83bf6317-ff39-4c5c-8987-cba34e7a6983
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 526c857acbe1283e16312355c181c56c67e19883
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744074"
---
# <a name="idiaenumsourcefilesnext"></a>IDiaEnumSourceFiles::Next
열거형 시퀀스에서 지정 된 수의 소스 파일을 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT Next ( 
   ULONG            celt,
   IDiaSourceFile** rgelt,
   ULONG*           pceltFetched
);
```

#### <a name="parameters"></a>매개 변수
 celt

진행 검색할 열거자의 소스 파일 수입니다.

 rgelt

제한이 원하는 소스 파일을 나타내는 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) 개체로 채워질 배열입니다.

 pceltFetched

제한이 인출 된 열거자의 소스 파일 수를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. 소스 파일이 더 이상 없는 경우 `S_FALSE`를 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="see-also"></a>참조
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)