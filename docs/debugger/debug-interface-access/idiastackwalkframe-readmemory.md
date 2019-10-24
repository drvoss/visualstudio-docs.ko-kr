---
title: 'IDiaStackWalkFrame:: readMemory | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae1201fca1fc25cce19b40b47d6435d02d80e1b4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741475"
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
이미지에서 메모리를 읽습니다.

## <a name="syntax"></a>구문

```C++
HRESULT readMemory ( 
   MemoryTypeEnum type,
   ULONGLONG va,
   DWORD     cbData,
   DWORD*    pcbData,
   BYTE      data[]
);
```

#### <a name="parameters"></a>매개 변수
 `type`

진행 액세스할 메모리 종류를 지정 하는 [MemoryTypeEnum 열거형](../../debugger/debug-interface-access/memorytypeenum.md) 열거형 값 중 하나입니다.

 `va`

진행 읽기를 시작할 이미지의 가상 주소 위치입니다.

 `cbData`

진행 데이터 버퍼의 크기 (바이트)입니다.

 `pcbData`

제한이 반환 된 바이트 수를 반환 합니다. @No__t_0 `NULL` 되 면 사용할 수 있는 데이터의 총 바이트 수가 `pcbData`에 포함 됩니다.

 `data`

제한이 지정 된 위치의 데이터로 채워질 버퍼입니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="see-also"></a>참조
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)