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
ms.openlocfilehash: 5ee258602c47951f4731dc1378542cc83d57d72b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955218"
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
|DOCUMENTNAMETYPE_APPNODE|응용 프로그램 트리에서 표시 된 대로 이름을 가져옵니다.|  
|DOCUMENTNAMETYPE_TITLE|뷰어의 제목 표시줄에 표시 된 대로 이름을 가져옵니다.|  
|DOCUMENTNAMETYPE_FILE_TAIL|경로 없이 파일 이름을 가져옵니다.|  
|DOCUMENTNAMETYPE_URL|문서의 URL을 가져옵니다.|  
|DOCUMENTNAMETYPE_UNIQUE_TITLE|Id에 대 한 열거형을 사용 하 여 추가 된 제목을 가져옵니다.|  
  
## <a name="see-also"></a>참고 항목  
 [액티브 스크립트 디버거 상수, 열거형 및 구조체](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)