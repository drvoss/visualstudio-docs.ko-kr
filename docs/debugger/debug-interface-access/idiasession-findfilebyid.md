---
title: 'Idiasession:: Findfilebyid | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFileById method
ms.assetid: 710efe04-78b5-4f3e-a1d8-f9b069063503
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3454ff5ef087b67dda5d48849d4a6c4eceb7e52
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839357"
---
# <a name="idiasessionfindfilebyid"></a>IDiaSession::findFileById
원본 파일 식별자에서 소스 파일을 검색합니다.

## <a name="syntax"></a>구문

```C++
HRESULT findFileById ( 
   DWORD            uniqueId,
   IDiaSourceFile** ppResult
);
```

#### <a name="parameters"></a>매개 변수
 `uniqueId`

[in] 소스 파일 식별자를 지정합니다.

 `ppResult`

[out] 반환을 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) 소스 파일을 나타내는 개체를 검색 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 소스 파일 식별자에는 모든 소스 파일을 고유 하 게 DIA SDK를 내부적으로 사용 되는 고유 값입니다. 이 메서드는 일반적으로 DIA SDK를 내부적으로 사용 됩니다.

## <a name="see-also"></a>참고 항목
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)