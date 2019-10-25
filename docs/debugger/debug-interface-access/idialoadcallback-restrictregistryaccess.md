---
title: IDiaLoadCallback::RestrictRegistryAccess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::RestrictRegistryAccess method
ms.assetid: de4760c3-a746-4bab-8065-1388fed31b67
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2240ef2d20b46e50e36942553d76b83fce6232b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743045"
---
# <a name="idialoadcallbackrestrictregistryaccess"></a>IDiaLoadCallback::RestrictRegistryAccess
레지스트리 쿼리를 사용 하 여 기호 검색 경로를 찾을 수 있는지 여부를 결정 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT RestrictRegistryAccess();
```

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>주의
 @No__t_0 이외의 모든 반환 코드는 레지스트리에 기호 검색 경로를 쿼리할 수 없습니다.

## <a name="see-also"></a>참조
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)