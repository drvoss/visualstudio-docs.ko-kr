---
title: 'IDebugApplicationNode:: EnumChildren | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNode.EnumChildren
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationNode::EnumChildren
ms.assetid: d79b362b-23d5-4a5e-a214-5a78618eaf71
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 906f437d94d3ed8f50204930eddb1891b80b7cc8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574798"
---
# <a name="idebugapplicationnodeenumchildren"></a>IDebugApplicationNode::EnumChildren
이 응용 프로그램 노드의 자식 노드를 열거 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT EnumChildren(  
   IEnumDebugApplicationNodes**  pperddp  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pperddp`  
 제한이 이 노드의 자식 노드에 대 한 열거형입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는이 응용 프로그램 노드의 자식 노드를 열거 합니다.  
  
## <a name="see-also"></a>참조  
 [IDebugApplicationNode 인터페이스](../../winscript/reference/idebugapplicationnode-interface.md)