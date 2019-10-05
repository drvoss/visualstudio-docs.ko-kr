---
title: 기호 및 기호 태그 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK]
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 625752125d3c68e9f03afd41cd549995fbc3272e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68193544"
---
# <a name="symbols-and-symbol-tags"></a>기호 및 기호 태그
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

컴파일된 프로그램에 대 한 디버그 정보는 디버그 인터페이스 액세스 (DIA) SDK Api를 사용 하 여 액세스할 수 있는 기호로 프로그램 데이터베이스 (.pdb) 파일에 저장 됩니다. 모든 기호는 [idiasymbol:: Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) 와 [idiasymbol:: Get_symindexid](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) 속성입니다. 합니다 `symTag` 속성에 정의 된 대로 기호의 종류를 나타내는 합니다 [SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md) 열거형입니다. 합니다 `symIndexId` 속성이 `DWORD` 기호의 모든 인스턴스에 대 한 고유 식별자를 포함 하는 값입니다.  
  
 기호에는 가장 자주 다른 기호에 대 한 참조 뿐만 아니라 기호에 대 한 추가 정보를 지정할 수 있는 속성을 [idiasymbol:: Get_lexicalparent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) 또는 [idiasymbol:: Get_classparent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md). 참조로 반환 됩니다 대 한 참조를 포함 하는 속성을 쿼리 하는 경우는 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 개체입니다. 이러한 속성은 항상 쌍을 이루는 다른 속성을 사용 하 여 "Id"를 사용 하 여 접미사가 있지만 동일한 이름으로 예를 들어 [idiasymbol:: Get_lexicalparentid](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) 하 고 [idiasymbol:: Get_classparentid](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)합니다. 테이블 [기호 위치](../../debugger/debug-interface-access/symbol-locations.md)를 [어휘 기호 형식 계층 구조](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md), 및 [기호 종류의 클래스 계층 구조](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) 다양 한 종류의 각 속성을 간략하게 설명의 기호입니다. 이러한 속성에 대 한 관련 정보 또는 다른 기호에 대 한 참조가 있을 수 있습니다. 때문에 `*Id` 속성은 해당 관련된 속성의 서 수 단순히 숫자 식별자, 추가로 토론에서 생략 하는 합니다. 참조 하는 매개 변수 설명이 필요한 경우에 합니다.  
  
 에서 오류가 발생 하지 않습니다 하 고 기호 속성 값을 지정 된 경우 속성에 액세스 하려고 하면 속성의 "get" 메서드가 반환 되는 `S_OK`합니다. 반환 값 `S_FALSE` 속성이 현재 기호에 유효 하지 않음을 나타냅니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [기호 위치](../../debugger/debug-interface-access/symbol-locations.md)  
 다양 한 종류의 기호를 가질 수 있습니다 위치를 설명 합니다.  
  
 [기호 형식의 어휘 계층 구조](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)  
 파일, 모듈, 함수 등 어휘 계층 구조를 형성 하는 기호 형식을 설명 합니다.  
  
 [기호 형식의 클래스 계층 구조](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)  
 클래스, 배열 및 함수 반환 형식이 같은 다른 언어 요소에 해당 하는 기호 형식을 설명 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [디버그 인터페이스 액세스 SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)
