---
title: 'IDiaStackWalkHelper:: readMemory | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 57afd033b2d969a4ed57dc713b2c4266e0ead632
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741356"
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
메모리의 실행 파일 이미지에서 데이터 블록을 읽습니다.

## <a name="syntax"></a>구문

```C++
HRESULT readMemory( 
   enum MemoryTypeEnum type,
   ULONGLONG           va,
   DWORD               cbData,
   DWORD*              pcbData,
   BYTE*               pbData
);
```

#### <a name="parameters"></a>매개 변수
 `type`

진행 읽을 메모리의 형식을 지정 하는 [MemoryTypeEnum 열거형](../../debugger/debug-interface-access/memorytypeenum.md) 열거형의 값입니다.

 va

진행 읽기를 시작할 이미지의 가상 주소입니다.

 `cbData`

진행 데이터 버퍼의 크기 (바이트)입니다.

 `pcbData`

제한이 실제로 읽은 바이트 수를 반환 합니다. @No__t_0 `NULL` 되 면 사용할 수 있는 데이터의 총 바이트 수입니다.

 `pbData`

[in, out] 읽은 메모리를 사용 하 여 채워진 버퍼입니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="see-also"></a>참조
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [MemoryTypeEnum 열거형](../../debugger/debug-interface-access/memorytypeenum.md)