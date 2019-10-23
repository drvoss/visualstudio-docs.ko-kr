---
title: 'IDiaSourceFile:: get_fileName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_fileName method
ms.assetid: a5cb8927-23c6-469e-8f78-f2787d85dba4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a6e871570ad49a4efe2df320f98fe56b5372c6bb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741802"
---
# <a name="idiasourcefileget_filename"></a>IDiaSourceFile::get_fileName
소스 파일 이름을 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_fileName ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

제한이 소스 파일 이름을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="see-also"></a>참조
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)