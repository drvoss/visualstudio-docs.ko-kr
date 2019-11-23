---
title: 'IDebugApplicationNode:: Attach | Microsoft Docs'
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
ms.openlocfilehash: 30d4e189ec878def1cfd88517654955cd2d1aa12
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574780"
---
# <a name="idebugapplicationnodeattach"></a>IDebugApplicationNode::Attach
지정 된 프로젝트 트리에이 응용 프로그램 노드를 추가 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT Attach(  
   IDebugApplicationNode*  pdanParent  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pdanParent`  
 진행 이 응용 프로그램 노드를 추가할 프로젝트 트리입니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 `HRESULT`를 반환합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 `pdanParent`를 부모로 사용 하 여이 응용 프로그램 노드를 프로젝트 트리에 추가 합니다. `pdanParent` `NULL`되는 경우이 응용 프로그램 노드는 최상위 노드가 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)   
 [IDebugApplicationNode 인터페이스](../../winscript/reference/idebugapplicationnode-interface.md)