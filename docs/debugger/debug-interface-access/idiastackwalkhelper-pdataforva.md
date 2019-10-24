---
title: IDiaStackWalkHelper::p dataForVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d51736a80021847881db164c9e176a010124638
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741396"
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
가상 주소와 연결 된 .PDATA 데이터 블록을 반환 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT pdataForVA( 
   ULONGLONG  va,
   DWORD      cbData,
   DWORD*     pcbData,
   BYTE*      pbData
);
```

#### <a name="parameters"></a>매개 변수
 `va`

진행 가져올 데이터의 가상 주소를 지정 합니다.

 `cbData`

진행 가져올 데이터의 크기 (바이트)입니다.

 `pcbData`

제한이 가져온 데이터의 실제 크기 (바이트)를 반환 합니다.

 `pbData`

[in, out] 요청 된 데이터로 채워진 버퍼입니다. @No__t_0 수 없습니다.

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. 지정 된 주소에 대 한 .PDATA가 없는 경우 `S_FALSE`를 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>주의
 Compiland의 .PDATA (".pdata" 섹션)은 함수에 대 한 예외 처리에 대 한 정보를 포함 합니다.

 호출자는 반환 되는 데이터의 양을 알고 있으므로 호출자는 사용할 수 있는 데이터의 양을 요청할 필요가 없습니다. 따라서 `pbData` 매개 변수가 `NULL` 되는 경우이 메서드를 구현 하 여 오류를 반환 하는 것이 허용 됩니다.

## <a name="see-also"></a>참조
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)