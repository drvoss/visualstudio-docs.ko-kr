---
title: 'IDiaLoadCallback2:: RestrictOriginalPathAccess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictOriginalPathAccess method
ms.assetid: 31fde3af-2824-4b0f-8d0d-cee6046596f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6bcdaa7c1896a0ef29706e3650ad8ac56537f778
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742993"
---
# <a name="idialoadcallback2restrictoriginalpathaccess"></a>IDiaLoadCallback2::RestrictOriginalPathAccess
원본 디버그 디렉터리에서 .pdb 파일을 찾을 수 있는지 여부를 확인 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT RestrictOriginalPathAccess ();
```

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>주의
 @No__t_0 이외의 모든 반환 코드는 원래 디버그 디렉터리에서 .pdb 파일을 찾을 수 없습니다. 원본 디버그 디렉터리는 디버깅을 설정할 때 실행 파일로 컴파일되는 기호 파일의 경로입니다. 이 경로는 실행 파일이 있는 경로와 동일할 필요는 없습니다.

## <a name="see-also"></a>참조
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)