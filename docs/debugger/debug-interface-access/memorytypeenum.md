---
title: MemoryTypeEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MemoryTypeEnum enumeration
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0710ec5cdfcfcb59407d18b43b885603f017fdb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738626"
---
# <a name="memorytypeenum"></a>MemoryTypeEnum
액세스할 메모리의 유형을 지정 합니다.

## <a name="syntax"></a>구문

```C++
enum MemoryTypeEnum {
    MemTypeCode,
    MemTypeData,
    MemTypeStack,
    MemTypeAny = -1
};
```

#### <a name="parameters"></a>매개 변수
`MemTypeCode`는 코드 메모리에만 액세스 합니다.

`MemTypeData` 데이터 또는 스택 메모리에 액세스 합니다.

`MemTypeStack` 스택 메모리에만 액세스 합니다.

`MemTypeAny`는 모든 종류의 메모리에 액세스 합니다.

## <a name="remarks"></a>주의
이 열거형의 값은 여러 메모리 형식에 대 한 액세스를 제한 하기 위해 [IDiaStackWalkHelper:: readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) 메서드에 전달 됩니다.

## <a name="requirements"></a>요구 사항
헤더: cvconst

## <a name="see-also"></a>참조
- [열거형 및 구조체](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)
