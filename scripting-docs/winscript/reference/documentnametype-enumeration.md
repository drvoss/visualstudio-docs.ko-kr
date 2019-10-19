---
title: DOCUMENTNAMETYPE 열거형 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DOCUMENTNAMETYPE
apilocation:
- scrobj.dll
helpviewer_keywords:
- DOCUMENTNAMETYPE enumeration
ms.assetid: d36d550e-efb4-493d-8971-4de267005654
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 401eb759523ed1a33d24c3a298db0b3de2b7d5a7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575870"
---
# <a name="documentnametype-enumeration"></a>DOCUMENTNAMETYPE 열거형
문서에 대한 가져올 유형을 설명합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
typedef enum tagDOCUMENTNAMETYPE {  
   DOCUMENTNAMETYPE_APPNODE,  
   DOCUMENTNAMETYPE_TITLE,  
   DOCUMENTNAMETYPE_FILE_TAIL,  
   DOCUMENTNAMETYPE_URL,  
DOCUMENTNAMETYPE_UNIQUE_TITLE,} DOCUMENTNAMETYPE;  
```  
  
## <a name="members"></a>멤버  
  
|멤버|설명|  
|------------|-----------------|  
|DOCUMENTNAMETYPE_APPNODE|응용 프로그램 트리에 표시 되는 이름을 가져옵니다.|  
|DOCUMENTNAMETYPE_TITLE|뷰어 제목 표시줄에 표시 되는 이름을 가져옵니다.|  
|DOCUMENTNAMETYPE_FILE_TAIL|경로 없이 파일 이름을 가져옵니다.|  
|DOCUMENTNAMETYPE_URL|문서의 URL을 가져옵니다.|  
|DOCUMENTNAMETYPE_UNIQUE_TITLE|식별을 위해 열거와 함께 추가 된 제목을 가져옵니다.|  
  
## <a name="see-also"></a>참조  
 [액티브 스크립트 디버거 상수, 열거형 및 구조체](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)