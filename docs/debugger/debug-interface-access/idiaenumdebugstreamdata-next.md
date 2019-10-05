---
title: 'Idiaenumdebugstreamdata:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::Next method
ms.assetid: 114171dd-38fd-4bd7-a702-8ff887ffc99b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf641fde4c03053496c732aa7904ddcad671af20
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62838609"
---
# <a name="idiaenumdebugstreamdatanext"></a>IDiaEnumDebugStreamData::Next
지정된 된 수의 열거 된 순서 대로 레코드를 검색합니다.

## <a name="syntax"></a>구문

```C++
HRESULT Next ( 
   ULONG  celt,
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[],
   ULONG* pceltFetched
);
```

#### <a name="parameters"></a>매개 변수
 celt

[in] 검색할 레코드의 수입니다.

 cbData

[in] 바이트의 데이터 버퍼의 크기입니다.

 pcbData

[out] 반환 된 바이트 수를 반환 합니다. 하는 경우 `data` 가 null 인 경우 다음 `pcbData` 요청한 모든 레코드에 대 한 사용 가능한 데이터의 바이트의 총 수를 포함 합니다.

 데이터[]

[out] 디버그 스트림 레코드 데이터를 채울 수에 있는 버퍼입니다.

 pceltFetched

[out에서] 레코드의 수를 반환 합니다 `data`합니다.

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. 반환 `S_FALSE` 레코드가 더 이상 없으면입니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="see-also"></a>참고 항목
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
- [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)