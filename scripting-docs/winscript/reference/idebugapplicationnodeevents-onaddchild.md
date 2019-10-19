---
title: 'IDebugApplicationNodeEvents:: onAddChild | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNodeEvents.onAddChild
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugApplicationNodeEvents::onAddChild
ms.assetid: 59ce33cf-1843-4b03-98a2-34859d3023f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 052fe47f1ddf2d20e7486a95a9dd79bc388f7ebc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574701"
---
# <a name="idebugapplicationnodeeventsonaddchild"></a>IDebugApplicationNodeEvents::onAddChild
자식 노드가 디버그 응용 프로그램 노드 개체에 추가 될 때 이벤트를 처리 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT onAddChild(  
   IDebugApplicationNode*  prddpChild  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `prddpChild`  
 진행 추가 된 자식 디버그 응용 프로그램 노드입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 자식 노드가 디버그 응용 프로그램 노드 개체에 추가 될 때 이벤트를 처리 합니다.  
  
 @No__t_0 인터페이스의 구현자는이 이벤트를 발생 시킵니다.  
  
## <a name="see-also"></a>참조  
 [Idebugapplicationnodeevents 인터페이스](../../winscript/reference/idebugapplicationnodeevents-interface.md)    
 [Idebugapplicationnodeevents:: onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)    
 [IDebugApplicationNode 인터페이스](../../winscript/reference/idebugapplicationnode-interface.md)