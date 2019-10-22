---
title: APPLICATION_NODE_EVENT_FILTER 열거형 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- APPLICATION_NODE_EVENT_FILTER Constants
ms.assetid: dccb2cf7-0598-46f8-b3eb-16b752815e96
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 481e015ec84d833f52220276bffa4ce0163f98ff
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572653"
---
# <a name="application_node_event_filter-enumeration"></a>APPLICATION_NODE_EVENT_FILTER 열거형
코드 문서를 필터링 할 때 제외할 노드 형식을 지정 합니다. [IDebugApplicationNode100:: GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) 및 [IDebugApplicationNode100:: SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md) 에 사용 됩니다.  
  
> [!IMPORTANT]
> 이러한 상수는 PDM v 10.0 이상에서 구현 됩니다. activdbg100.h에서 찾을 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
typedef enum tagAPPLICATION_NODE_EVENT_FILTER {    FILTER_EXCLUDE_NOTHING = 0,    FILTER_EXCLUDE_ANONYMOUS_CODE = 0x1,    FILTER_EXCLUDE_EVAL_CODE = 0x2} APPLICATION_NODE_EVENT_FILTER;  
```  
  
## <a name="members"></a>멤버  
  
|멤버|값|설명|  
|------------|-----------|-----------------|  
|FILTER_EXCLUDE_NOTHING|0x00000000|모든 이벤트를 보냅니다.|  
|FILTER_EXCLUDE_ANONYMOUS_CODE|0x00000001|익명 코드 노드를 제외 합니다. 이러한 노드는 JScript 런타임에서 `new Function([args,] <code>)'`에 사용 됩니다.|  
|FILTER_EXCLUDE_EVAL_CODE|0x00000002|Eval 코드 노드를 제외 합니다. 이러한 노드는 JScript 런타임에서 eval 지원에 사용 됩니다.|  
  
## <a name="see-also"></a>참조  
 [액티브 스크립트 디버거 상수, 열거형 및 구조체](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)