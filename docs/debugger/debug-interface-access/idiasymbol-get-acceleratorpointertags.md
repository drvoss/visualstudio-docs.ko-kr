---
title: 'IDiaSymbol:: get_acceleratorPointerTags | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f36b4bf9fdd362f4941e33745d59d481a473c607
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741110"
---
# <a name="idiasymbolget_acceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
C++ AMP accelerator 스텁 함수에 해당 하는 액셀러레이터 포인터 태그 값을 모두 반환 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_acceleratorPointerTags(
   DWORD          cnt,
   DWORD*         pcnt,
   DWORD*         pPointerTags);
```

#### <a name="parameters"></a>매개 변수
 `cnt`

진행 출력 배열의 크기 `pPointerTags`입니다.

 `pcnt`

제한이 C++ AMP accelerator 스텁 함수의 액셀러레이터 포인터 태그 수입니다.

 `pPointerTags`

제한이 C++ AMP accelerator 스텁 함수의 액셀러레이터 포인터 태그 값으로 채워지는 `DWORD` 배열 포인터입니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 `S_FALSE` 또는 오류 코드를 반환 합니다.

## <a name="remarks"></a>주의
 이 메서드는 C++ AMP 액셀러레이터 스텁 함수에 해당 하는 `IDiaSymbol` 인터페이스에서 호출 됩니다.

## <a name="see-also"></a>참조
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)