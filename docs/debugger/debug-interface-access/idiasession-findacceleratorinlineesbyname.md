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
ms.openlocfilehash: fb3caa5574605864a0dd16b59b6f451530b8e631
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62827793"
---
# <a name="idiasessionfindacceleratorinlineesbyname"></a>IDiaSession::findAcceleratorInlineesByName
지정 된 인라인 함수 이름에 해당 하는 인라인 프레임에 대 한 기호의 열거형을 반환 합니다.

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

[in] 검색할 인라인 함수 이름입니다.

 `option`

[in] 에 해당 하는 프레임 인라인을 검색할 때 사용 되는 이름 검색 옵션 `name`합니다. 자세한 내용은 [NameSearchOptions 열거형](../../debugger/debug-interface-access/namesearchoptions.md)합니다.

 `ppResult`

[out] 에 대 한 포인터는 `IDiaEnumSymbols` 결과 사용 하 여 초기화 된 인터페이스 포인터입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 이 함수를 인라인 가속기 스텁 함수 내 에서만 검색합니다. 네이티브 무시 C++ 프로시저 레코드입니다.

## <a name="see-also"></a>참고 항목
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)