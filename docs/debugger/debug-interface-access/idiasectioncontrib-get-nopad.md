---
title: 'IDiaSectionContrib:: get_nopad | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_nopad method
ms.assetid: f5c08603-0b3e-4e81-acf1-1b95a6a83bed
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a81113242379070e56d6d0bd0f916355985eaa42
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742617"
---
# <a name="idiasectioncontribget_nopad"></a>IDiaSectionContrib::get_nopad
섹션을 다음 메모리 경계로 패딩 하지 않아야 하는지 여부를 나타내는 플래그를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_nopad(
   BOOL* pRetVal
};
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

제한이 섹션을 다음 메모리 경계로 패딩 하지 않아야 하는 경우 `TRUE`를 반환 합니다. 그렇지 않으면 `FALSE`을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. 이 속성이 지원 되지 않는 경우 `S_FALSE`를 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>주의
 이 속성은 일반적으로 이전 파일 에서만 표시 되는 속성입니다.

## <a name="see-also"></a>참조
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)