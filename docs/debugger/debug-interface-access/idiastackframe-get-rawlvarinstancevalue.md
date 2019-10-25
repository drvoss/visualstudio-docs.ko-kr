---
title: 'IDiaStackFrame:: get_rawLVarInstanceValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_rawLVarInstanceValue method
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b1118517988f6a790cd4f6732eba3bc8a9fc25a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741630"
---
# <a name="idiastackframeget_rawlvarinstancevalue"></a>IDiaStackFrame::get_rawLVarInstanceValue
이 메서드는 지정 된 지역 변수의 값을 원시 바이트로 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_rawLVarInstanceValue(
   IDiaLVarInstance* pInstance,
   DWORD             cbDataMax,
   DWORD*            pcbData,
   BYTE*             pbData
);
```

#### <a name="parameters"></a>매개 변수
 `pInstance`

진행 값을 가져올 지역 변수의 인스턴스를 나타내는 `IDiaLVarInstance` 개체입니다.

 `cbDataMax`

진행 @No__t_0가 가리키는 버퍼의 최대 바이트 수입니다. 최대 8 바이트 (`sizeof(ULONGLONG)`)가 될 수 있습니다.

 `pcbData`

제한이 버퍼에 저장 된 실제 바이트 수를 반환 합니다.

 `pbData`

제한이 데이터로 채울 버퍼입니다. @No__t_0 수 없습니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="see-also"></a>참조
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)