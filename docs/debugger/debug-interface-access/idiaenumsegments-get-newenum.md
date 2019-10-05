---
title: 'Idiaenumsegments:: Get__newenum | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::get__NewEnum method
ms.assetid: 504505fa-b35c-402f-a440-8972c589cc5b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5c021e74c758b6409d42deae6a7e6831368367e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62829812"
---
# <a name="idiaenumsegmentsgetnewenum"></a>IDiaEnumSegments::get__NewEnum
검색 된 <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> 이 열거자의 버전입니다.

## <a name="syntax"></a>구문

```C++
HRESULT get__NewEnum ( 
   IUnknown** pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 pRetVal

[out] 반환 된 `IUnknown` 나타내는 인터페이스입니다는 <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> 이 열거자의 버전.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="see-also"></a>참고 항목
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)