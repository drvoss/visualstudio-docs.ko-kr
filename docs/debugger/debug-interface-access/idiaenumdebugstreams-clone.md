---
title: 'IDiaEnumDebugStreams:: Clone | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::Clone method
ms.assetid: e85ec592-de97-4f95-a774-1623315ba415
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 105a84b7c4a1b0a43f8f8008cffbebe7b6e23af5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744775"
---
# <a name="idiaenumdebugstreamsclone"></a>IDiaEnumDebugStreams::Clone
현재 열거자와 동일한 열거 상태를 포함 하는 열거자를 만듭니다.

## <a name="syntax"></a>구문

```C++
HRESULT Clone ( 
   IDiaEnumDebugStreams** ppenum
);
```

#### <a name="parameters"></a>매개 변수
 `ppenum`

제한이 열거자의 복제본을 포함 하는 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md) 개체를 반환 합니다. 스트림은 중복 되지 않으며 열거자만을 사용할 수 있습니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="see-also"></a>참조
- [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)