---
title: 'IDiaAddressMap:: set_addressMap | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_addressMap method
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8414788af44d78943088b78b2d3e42a5a8d8c50b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745023"
---
# <a name="idiaaddressmapset_addressmap"></a>IDiaAddressMap::set_addressMap
이미지 레이아웃 번역을 지 원하는 주소 맵을 제공 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT set_addressMap ( 
   DWORD                     cbData,
   struct DiaAddressMapEntry data[],
   BOOL                      imagetoSymbols
);
```

#### <a name="parameters"></a>매개 변수
 `cbData`

진행 @No__t_0 매개 변수에 있는 요소의 수입니다.

 `data[]`

진행 번역 맵을 정의 하는 [Diaaddressmapentry 구조](../../debugger/debug-interface-access/diaaddressmapentry.md) 구조체의 배열입니다.

 `imagetoSymbols`

[in] `data` 매개 변수가 새 이미지 레이아웃에서 원래 레이아웃 (디버그 기호에서 설명)으로 맵을 정의 하는 경우에 `TRUE` 합니다. `data` 원래 레이아웃에서 가져온 새 이미지 레이아웃에 대 한 맵입니다 `FALSE` 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>주의
 일반적으로 DIA는 프로그램 데이터베이스 (.pdb) 파일에서 주소 변환 맵을 검색 합니다. 이러한 값이 없는 경우 [IDiaAddressMap:: set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) 메서드는 `imagetoSymbols` 매개 변수를 `TRUE`로 설정 하 고 `imagetoSymbols` 매개 변수를 `FALSE`로 설정 하 여 한 번 호출 됩니다. [IDiaAddressMap::P ut_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) 메서드를 사용 하 여 두 변환 맵을 모두 제공 하지 않으면 주소 맵 번역을 사용 하도록 설정할 수 없습니다.

## <a name="see-also"></a>참조
- [DiaAddressMapEntry 구조체](../../debugger/debug-interface-access/diaaddressmapentry.md)
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)