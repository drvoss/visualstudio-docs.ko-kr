---
title: TEXT_DOCUMENT_ARRAY 구조체 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- TEXT_DOCUMENT_ARRAY Structure
ms.assetid: 47c08f23-981b-4105-9240-6dfffc6cb91b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9d188729b68f8086da62d40ca28fc29945c8be7f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62840059"
---
# <a name="textdocumentarray-structure"></a>TEXT_DOCUMENT_ARRAY 구조체
배열을 [IDebugDocumentText 인터페이스](../../winscript/reference/idebugdocumenttext-interface.md) 개체입니다. 멤버는 CoTaskMemAlloc을 사용 하 여 할당 됩니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
typedef struct tagTEXT_DOCUMENT_ARRAY{    DWORD dwCount;    [size_is(dwCount)] IDebugDocumentText **Members;} TEXT_DOCUMENT_ARRAY;  
```  
  
## <a name="members"></a>멤버  
 `dwCount`  
 문서 수입니다.  
  
 `Members`  
 문서 집합입니다.  
  
## <a name="see-also"></a>참고 항목  
 [액티브 스크립트 디버거 상수, 열거형 및 구조체](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)