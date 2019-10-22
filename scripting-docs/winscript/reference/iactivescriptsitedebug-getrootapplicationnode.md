---
title: 'IActiveScriptSiteDebug:: GetRootApplicationNode | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.GetRootApplicationNode
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::GetRootApplicationNode
ms.assetid: 2393f566-6b97-47c0-8041-4dd7e3b1d3a3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b19ed10178d03be0b96393ad08f1eab88ce40329
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570066"
---
# <a name="iactivescriptsitedebuggetrootapplicationnode"></a>IActiveScriptSiteDebug::GetRootApplicationNode
스크립트 문서를 추가 해야 하는 응용 프로그램 노드를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetRootApplicationNode(  
   IDebugApplicationNode**  ppdanRoot  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ppdanRoot`  
 제한이 스크립트 문서를 포함 하는 디버그 응용 프로그램 노드입니다. `NULL`일 수 있습니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 스크립트 문서를 추가 해야 하는 응용 프로그램 노드를 반환 합니다. 스크립트 문서가 최상위 수준인 경우 메서드는 `ppdanRoot`에 대 한 `NULL`를 반환할 수 있습니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScriptSiteDebug 인터페이스](../../winscript/reference/iactivescriptsitedebug-interface.md)