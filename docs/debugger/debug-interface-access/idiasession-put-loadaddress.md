---
title: IDiaSession::p ut_loadAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39db3bc0e0107e734f5de3f6902a2ca0fcc55bb0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741898"
---
# <a name="idiasessionput_loadaddress"></a>IDiaSession::put_loadAddress
이 기호 저장소의 기호에 해당 하는 실행 파일의 로드 주소를 설정 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT put_loadAddress ( 
   ULONGLONG NewVal
);
```

#### <a name="parameters"></a>매개 변수
 `NewVal`

진행 실행 파일에 대 한 주소를 로드 합니다.

## <a name="remarks"></a>주의
 기호 가상 주소 (VA) 속성은이 메서드의 값을 사용 하 여 계산 됩니다. 이 속성이 0이 아닌 값으로 설정 되지 않으면 가상 주소가 계산 되지 않습니다.

> [!NOTE]
> [IDiaSession](../../debugger/debug-interface-access/idiasession.md) 개체를 가져오고 기호에서 가상 속성을 사용 해야 하는 경우 개체 사용을 시작 하기 전에이 메서드를 호출 해야 합니다.

## <a name="see-also"></a>참조
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)