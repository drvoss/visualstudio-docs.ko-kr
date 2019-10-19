---
title: TEXT_DOC_ATTR 상수 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- TEXT_DOC_ATTR
apilocation:
- scrobj.dll
helpviewer_keywords:
- TEXT_DOC_ATTR constants
ms.assetid: fd9c53a4-8f73-4c6a-abe5-6b831ecd5b1e
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3604c06b6cb36cc4ff7ef6c76348b5ece53bed61
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572988"
---
# <a name="text_doc_attr-constants"></a>TEXT_DOC_ATTR 상수
문서의 특성을 설명합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
typedef DWORD TEXT_DOC_ATTR;  
```  
  
## <a name="constants"></a>상수  
  
|상수|값|설명|  
|--------------|-----------|-----------------|  
|TEXT_DOC_ATTR_READONLY|0x00000001|문서가 읽기 전용입니다.|  
|TEXT_DOC_ATTR_TYPE_PRIMARY|0x00000002|문서는이 문서 트리의 주 파일입니다.|  
|TEXT_DOC_ATTR_TYPE_WORKER|0x00000004|문서는 작업자입니다.|  
|TEXT_DOC_ATTR_TYPE_SCRIPT|0x00000008|문서는 스크립트 파일입니다.|  
  
## <a name="see-also"></a>참조  
 [액티브 스크립트 디버거 상수, 열거형 및 구조체](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)