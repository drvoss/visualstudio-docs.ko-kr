---
title: IDiaSession::findFile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFile method
ms.assetid: a215dc21-b316-40d7-9923-55bfa014976b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d9751127007b4e7823cf6d2ae35ed2fe80cb83b8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742286"
---
# <a name="idiasessionfindfile"></a>IDiaSession::findFile
Compiland 및 이름으로 소스 파일을 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT findFile ( 
   IDiaSymbol*           pCompiland,
   LPCOLESTR             name,
   DWORD                 option,
   IDiaEnumSourceFiles** ppResult
);
```

#### <a name="parameters"></a>매개 변수
 `pCompiland`

진행 검색 컨텍스트로 사용할 compiland을 나타내는 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 개체입니다. 이 매개 변수를 `NULL` 설정 하 여 모든 compilands에서 원본 파일을 찾을 수 있습니다.

 `name`

진행 검색할 소스 파일의 이름을 지정 합니다. 검색할 모든 소스 파일에 대 한 `NULL`이 매개 변수를로 설정 합니다.

 `option`

진행 이름 검색에 적용 되는 비교 옵션을 지정 합니다. [Namesearchoptions 열거형](../../debugger/debug-interface-access/namesearchoptions.md) 열거형의 값은 단독으로 사용 하거나 함께 사용할 수 있습니다.

 `ppResult`

제한이 검색 된 소스 파일의 목록을 포함 하는 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="example"></a>예제

```C++
IDiaEnumSourceFiles* pEnum;
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );
```

## <a name="see-also"></a>참조
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [NameSearchOptions 열거형](../../debugger/debug-interface-access/namesearchoptions.md)