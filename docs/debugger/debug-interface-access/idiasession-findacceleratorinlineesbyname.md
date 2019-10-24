---
title: IDiaSession::findAcceleratorInlineesByName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 007477d3f0de3767b0c5ef0af977f969505884ed
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742304"
---
# <a name="idiasessionfindacceleratorinlineesbyname"></a>IDiaSession::findAcceleratorInlineesByName
지정 된 인라인 함수 이름에 해당 하는 인라인 프레임의 기호 열거형을 반환 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT findAcceleratorInlineeLinesByName ( 
   LPCOLESTR             name,
   DWORD                 option,
   IDiaEnumSymbols**     ppResult
);
```

#### <a name="parameters"></a>매개 변수
 `name`

진행 검색할 인라인 대상 함수 이름입니다.

 `option`

진행 @No__t_0에 해당 하는 인라인 프레임을 검색할 때 사용 되는 이름 검색 옵션입니다. 자세한 내용은 [Namesearchoptions 열거](../../debugger/debug-interface-access/namesearchoptions.md)를 참조 하세요.

 `ppResult`

제한이 결과를 사용 하 여 초기화 되는 `IDiaEnumSymbols` 인터페이스 포인터에 대 한 포인터입니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>주의
 이 함수는 액셀러레이터 키 함수 내 에서만 가진을 검색 합니다. 기본 C++ 프로시저 레코드는 무시 됩니다.

## <a name="see-also"></a>참조
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)