---
title: 'IDiaLoadCallback:: RestrictSymbolServerAccess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::RestrictSymbolServerAccess method
ms.assetid: db37ad9f-f75e-4f0c-83bf-21a6e66ba859
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 87d590af5162d3efd2ef2c9702a3fe9f45250993
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743027"
---
# <a name="idialoadcallbackrestrictsymbolserveraccess"></a>IDiaLoadCallback::RestrictSymbolServerAccess
기호를 확인 하기 위해 기호 서버에 대 한 액세스가 허용 되는지 여부를 결정 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT RestrictSymbolServerAccess();
```

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>주의
 @No__t_0 이외의 모든 반환 코드는 기호 서버를 사용 하 여 기호를 확인할 수 없습니다.

## <a name="see-also"></a>참조
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)