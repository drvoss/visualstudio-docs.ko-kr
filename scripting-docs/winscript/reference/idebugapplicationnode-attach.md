---
title: IDebugApplicationNode::Attach | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNode.Attach
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationNode::Attach
ms.assetid: f4aad4ae-5bb0-4b5e-8f70-912a677f8f7a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c41d06c116c7c15ad308ce2ace837ea01d90ab1d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62990481"
---
# <a name="idebugapplicationnodeattach"></a>IDebugApplicationNode::Attach
지정한 프로젝트 트리에이 응용 프로그램 노드를 추가합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT Attach(  
   IDebugApplicationNode*  pdanParent  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pdanParent`  
 [in] 이 응용 프로그램 노드를 추가 해야 하는 위치는 프로젝트 트리.  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 `HRESULT`를 반환합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>설명  
 이 메서드는 프로젝트에이 응용 프로그램 노드를 추가 합니다. 트리를 사용 하 여 `pdanParent` 부모로 합니다. 하는 경우 `pdanParent` 는 `NULL`,이 응용 프로그램 노드는 최상위 노드가 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)   
 [IDebugApplicationNode 인터페이스](../../winscript/reference/idebugapplicationnode-interface.md)