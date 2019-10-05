---
title: IDiaSymbol::get_unmodifiedType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_unmodifiedType method
ms.assetid: bf914dc0-ff84-4f5d-9f75-1733b17f3be0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2e609f59e0d72628be4233be52738ff244c6acca
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/12/2019
ms.locfileid: "64806767"
---
# <a name="idiasymbolgetunmodifiedtype"></a>IDiaSymbol::get_unmodifiedType
이 기호에 대 한 원래 형식을 검색합니다. 사용 시기를 [SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md) 유형으로 설정 됩니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_unmodifiedType( 
   IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

[out] 반환 된 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 이 기호의 원래 형식을 나타내는 개체입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`이 고, 그렇지 않으면 반환 `S_FALSE` 또는 오류 코드입니다.

> [!NOTE]
> 반환 값이 `S_FALSE` 속성 기호를 사용할 수 없는 것을 의미 합니다.

## <a name="remarks"></a>설명
 현재 형식이 반환 된 원래 형식의 수정 합니다. 기호에 대 한 원래 형식은 먼저 기호의 형식을 가져오고 다음 원래 형식에 대 한 형식을 반환 하는 조회 하 여 확인할 수 있습니다. 참고 일부 기호는 원래 형식이 수정 된 형식에 없을 수 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: Dia2.h

 라이브러리: diaguids.lib

 DLL: msdia100.dll

## <a name="see-also"></a>참고 항목
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)