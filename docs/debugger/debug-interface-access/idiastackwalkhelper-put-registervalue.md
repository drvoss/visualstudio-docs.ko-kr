---
title: IDiaStackWalkHelper::p ut_registerValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::put_registerValue method
ms.assetid: 8f02ce54-ef59-455f-8aa6-dc26761c7aff
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 619ed78584a9fe897b19d6ac2ffd4c28838c61ab
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741376"
---
# <a name="idiastackwalkhelperput_registervalue"></a>IDiaStackWalkHelper::put_registerValue
레지스터의 값을 설정 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT put_registerValue ( 
   DWORD     index,
   ULONGLONG NewVal
);
```

#### <a name="parameters"></a>매개 변수
 `index`

진행 쓸 레지스터를 지정 하는 [CV_HREG_e 열거형](../../debugger/debug-interface-access/cv-hreg-e.md) 열거형의 값입니다.

 `NewVal`

진행 새 레지스터 값입니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>주의
 값의 크기에도 불구 하 고 구현은 일반적으로 등록에 포함 된 내용만 저장 해야 합니다. 예를 들어 8 비트 레지스터는 지정 된 값의 가장 낮은 8 비트만 보유 합니다.

## <a name="see-also"></a>참조
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [CV_HREG_e 열거형](../../debugger/debug-interface-access/cv-hreg-e.md)