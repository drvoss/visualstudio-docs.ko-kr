---
title: 'IDiaInjectedSource:: get_sourceCompression | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_sourceCompression method
ms.assetid: 854b142f-23a9-466c-bf7f-98e581d5abcd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9428b30df82d92a8c74511644aaf97f2166807a2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743327"
---
# <a name="idiainjectedsourceget_sourcecompression"></a>IDiaInjectedSource::get_sourceCompression
사용 된 원본 압축의 표시기를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_sourceCompression ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

제한이 사용 된 원본 압축의 표시기를 반환 합니다. 값이 0 이면 원본 압축을 사용 하지 않았음을 나타냅니다.

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. 이 속성이 지원 되지 않는 경우 `S_FALSE`를 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>주의
 이 메서드에서 반환 되는 값은 사용 되는 컴파일러에 따라 다릅니다. 예를 들어, 컴파일러는 실행 길이 인코딩 또는 Huffman 스타일 압축을 사용할 수 있습니다.

## <a name="see-also"></a>참조
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)