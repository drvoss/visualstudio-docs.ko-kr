---
title: ERRORRESUMEACTION 열거형 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ERRORRESUMEACTION
apilocation:
- scrobj.dll
helpviewer_keywords:
- ERRORRESUMEACTION enumeration
ms.assetid: a68293c8-056b-439f-83e7-69e4a38f4976
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad9b8598cb027c96f6fb6fad6f3d343e6058cfdb
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575858"
---
# <a name="errorresumeaction-enumeration"></a>ERRORRESUMEACTION 열거형
런타임 오류에서 계속 진행하는 방법을 설명합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
typedef enum tagERRORRESUMEACTION {  
   ERRORRESUMEACTION_ReexecuteErrorStatement,  
   ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller,  
   ERRORRESUMEACTION_SkipErrorStatement,  
} ERRORRESUMEACTION;  
```  
  
## <a name="members"></a>멤버  
  
|멤버|설명|  
|------------|-----------------|  
|ERRORRESUMEACTION_ReexecuteErrorStatement|오류를 생성 한 문을 다시 실행 합니다.|  
|ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller|언어 엔진에서 오류를 처리할 수 있습니다.|  
|ERRORRESUMEACTION_SkipErrorStatement|오류를 생성 한 문 다음에 코드에서 실행을 다시 시작 합니다.|  
  
## <a name="see-also"></a>참조  
 [액티브 스크립트 디버거 상수, 열거형 및 구조체](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)