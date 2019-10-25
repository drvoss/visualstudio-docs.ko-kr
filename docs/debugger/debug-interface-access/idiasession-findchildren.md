---
title: IDiaSession::findChildren | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findChildren method
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cca6778e5697c5f8821322c19d706d733d7f2b9f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742294"
---
# <a name="idiasessionfindchildren"></a>IDiaSession::findChildren
이름 및 기호 형식과 일치 하는 지정 된 부모 식별자의 모든 자식을 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT findChildren ( 
   IDiaSymbol*       parent,
   SymTagEnum        symtag,
   LPCOLESTR         name,
   DWORD             compareFlags,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>매개 변수
 `parent`

진행 부모를 나타내는 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 개체입니다. 이 부모 기호가 함수, 모듈 또는 블록인 경우 해당 어휘 자식은 `ppResult` 반환 됩니다. 부모 기호가 형식이 면 해당 클래스의 자식이 반환 됩니다. 이 매개 변수를 `NULL` 하는 경우 `symtag`는 전역 범위 (.exe 파일)를 반환 하는 `SymTagExe` 또는 `SymTagNull`로 설정 되어야 합니다.

 `symtag`

진행 검색할 자식의 기호 태그를 지정 합니다. 값은 [SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md) 열거에서 가져옵니다. 모든 자식을 검색 하려면 `SymTagNull`로 설정 합니다.

 `name`

진행 검색할 자식의 이름을 지정 합니다. 모든 자식 항목을 검색 하려면 `NULL`로 설정 합니다.

 `compareFlags`

진행 이름 일치에 적용 되는 비교 옵션을 지정 합니다. [Namesearchoptions 열거형](../../debugger/debug-interface-access/namesearchoptions.md) 열거형의 값은 단독으로 사용 하거나 함께 사용할 수 있습니다.

 `ppResult`

제한이 검색 된 자식 기호의 목록을 포함 하는 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="example"></a>예제
 다음 예에서는 이름 `szVarName`와 일치 하 `pFunc` 함수의 지역 변수를 찾는 방법을 보여 줍니다.

```C++
IDiaEnumSymbols* pEnum;
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );
```

## <a name="see-also"></a>참조
- [개요](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [NameSearchOptions 열거형](../../debugger/debug-interface-access/namesearchoptions.md)
- [SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md)