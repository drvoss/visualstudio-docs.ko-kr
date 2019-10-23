---
title: 'IDiaPropertyStorage:: ReadMultiple | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadMultiple
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9cd1e419e1d08120274fc627a672eb52331ca50f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742880"
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
현재 속성 집합에서 지정 된 속성을 읽습니다.

## <a name="syntax"></a>구문

```C++
HRESULT ReadMultiple( 
   ULONG          cpspec,
   PROPSPEC const rgpspec,
   PROPVARIANT    rgvar
);
```

#### <a name="parameters"></a>매개 변수
 `cpspec`

진행 @No__t_0 배열에 지정 된 속성의 수입니다. 0 인 경우이 메서드는 속성을 반환 하지 않지만 `S_OK` 성공 코드로 반환 합니다.

 `rgpspec`

진행 읽을 속성의 배열입니다. 속성은 속성 ID 또는 선택적 문자열 이름으로 지정할 수 있습니다. 배열의 특정 순서로 속성을 지정할 필요는 없습니다. 배열에 중복 된 속성이 포함 될 수 있으며,이로 인해 단순 속성에 대해 반환 되는 속성 값이 중복 됩니다. 단순 하지 않은 속성은 두 번째로 열 때 액세스 거부를 반환 해야 합니다. 배열에는 속성 Id와 문자열 Id를 혼합 하 여 포함할 수 있습니다. 이 배열에는 적어도 `cpspec`의 속성 값이 있어야 합니다.

 `rgvar`

[in, out] 각 속성에 대 한 값으로 채워질 `PROPVARIANT` 구조체 (VisualStudio 네임 스페이스)의 배열입니다. 배열의 크기는 `cpspec` 이상 이어야 합니다. 호출자는 배열의 값을 초기화할 필요가 없습니다.

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. 하나 이상의 속성을 찾을 수 없는 경우 `S_FALSE`를 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>주의
 속성을 찾을 수 없는 경우 `rgvar` 배열의 해당 항목에 `VT_EMPTY` 형식의 `VARIANT` 포함 됩니다.

## <a name="see-also"></a>참조
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)