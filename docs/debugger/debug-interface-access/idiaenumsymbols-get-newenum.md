---
title: 'IDiaEnumSymbols:: get__NewEnum | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::get__NewEnum method
ms.assetid: 879609ea-8e5a-4fa3-afa6-d24870fb4392
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dccfb37d2abe38a9fd1c805f03acd7172ca01af6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743966"
---
# <a name="idiaenumsymbolsget__newenum"></a>IDiaEnumSymbols::get__NewEnum
이 열거자의 <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> 버전을 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get__NewEnum ( 
   IUnknown** pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 pRetVal

제한이 이 열거자의 <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> 버전을 나타내는 `IUnknown` 인터페이스를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="see-also"></a>참조
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)