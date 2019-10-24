---
title: 기호 및 기호 태그 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK]
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d2281a82926dabfde88b8d4bb9096f0e9624211
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738526"
---
# <a name="symbols-and-symbol-tags"></a>기호 및 기호 태그
컴파일된 프로그램에 대 한 디버그 정보는 프로그램 데이터베이스 (.pdb) 파일에 DIA (디버그 인터페이스 액세스) SDK Api를 사용 하 여 액세스할 수 있는 기호로 저장 됩니다. 모든 기호에는 [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) 및 [IDiaSymbol:: get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) 속성이 있습니다. @No__t_0 속성은 [SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md) 열거형에서 정의한 기호의 종류를 나타냅니다. @No__t_0 속성은 기호의 모든 인스턴스에 대 한 고유 식별자를 포함 하는 `DWORD` 값입니다.

 기호에는 기호에 대 한 추가 정보 뿐만 아니라 다른 기호 ( [IDiaSymbol:: get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) 또는 [IDiaSymbol:: get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md))에 대 한 참조도 지정할 수 있는 속성도 있습니다. 참조가 포함 된 속성을 쿼리하면 참조가 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 개체로 반환 됩니다. 이러한 속성은 항상 동일한 이름을 사용 하 여 다른 속성과 쌍을 이룹니다. 예를 들어, [IDiaSymbol:: get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) 및 [IDiaSymbol:: get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)와 같이 "Id"로 접미사가 붙습니다. 기호 [위치](../../debugger/debug-interface-access/symbol-locations.md), [기호 형식의 어휘 계층](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)및 [기호 형식의 클래스 계층 구조](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) 에 있는 테이블은 다양 한 종류의 기호에 대 한 속성을 간략하게 설명 합니다. 이러한 속성에는 관련 된 정보나 다른 기호에 대 한 참조가 있을 수 있습니다. @No__t_0 속성은 관련 속성의 숫자 서 수 식별자 이기 때문에 추가 토론에서 생략 됩니다. 이러한 매개 변수는 매개 변수 설명이 필요한 경우에만 참조 됩니다.

 속성에 액세스 하려고 할 때 오류가 발생 하지 않고 symbol 속성에 값이 할당 된 경우 속성의 "get" 메서드는 `S_OK`를 반환 합니다. @No__t_0의 반환 값은 속성이 현재 기호에 대해 유효 하지 않음을 나타냅니다.

## <a name="in-this-section"></a>단원 내용

[기호 위치](../../debugger/debug-interface-access/symbol-locations.md)

기호에 포함 될 수 있는 다양 한 종류의 위치를 설명 합니다.

[기호 형식의 어휘 계층 구조](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)

파일, 모듈, 함수 등의 어휘 계층 구조를 구성 하는 기호 형식을 설명 합니다.

[기호 형식의 클래스 계층 구조](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)

클래스, 배열 및 함수 반환 형식과 같은 다양 한 언어 요소에 해당 하는 기호 형식을 설명 합니다.

## <a name="see-also"></a>참조

- [디버그 인터페이스 액세스 SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)