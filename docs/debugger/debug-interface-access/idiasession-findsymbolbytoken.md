---
title: 'IDiaSession:: Find기호 Bytoken | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findSymbolByToken method
ms.assetid: 3c92149c-6eef-454f-86be-66e89557b9e6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 098d84d6c7c79fee5fea5e5b2b36136bf7b55b26
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742019"
---
# <a name="idiasessionfindsymbolbytoken"></a>IDiaSession::findSymbolByToken
지정 된 메타 데이터 토큰을 포함 하는 기호를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT findSymbolByToken ( 
   ULONG        token,
   SymTagEnum   symtag,
   IDiaSymbol** ppSymbol
);
```

#### <a name="parameters"></a>매개 변수
 `token`

진행 토큰을 지정 합니다.

 `symtag`

진행 찾을 기호 형식입니다. 값은 [SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md) 열거에서 가져옵니다.

 `ppSymbol`

제한이 검색 된 기호를 나타내는 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="example"></a>예제

```C++
IDiaSymbol* pFunc;
pSession->findSymbolByToken( token, SymTagFunction, &pFunc );
```

## <a name="see-also"></a>참조
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md)