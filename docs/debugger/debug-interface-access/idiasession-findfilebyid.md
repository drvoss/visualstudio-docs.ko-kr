---
title: 'IDiaSession:: findFileById | Microsoft Docs'
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
ms.openlocfilehash: aafdd2270606ba6e56713e9166dbae2b8c635b41
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742269"
---
# <a name="idiasessionfindfilebyid"></a>IDiaSession::findFileById
소스 파일 식별자를 기준으로 소스 파일을 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT findFileById ( 
   DWORD            uniqueId,
   IDiaSourceFile** ppResult
);
```

#### <a name="parameters"></a>매개 변수
 `uniqueId`

진행 원본 파일 식별자를 지정 합니다.

 `ppResult`

제한이 검색 된 소스 파일을 나타내는 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>주의
 원본 파일 식별자는 모든 소스 파일을 고유 하 게 만들기 위해 DIA SDK에 내부적으로 사용 되는 고유 값입니다. 이 메서드는 일반적으로 DIA SDK에 내부적으로 사용 됩니다.

## <a name="see-also"></a>참조
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)