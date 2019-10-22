---
title: IScriptNode::D e) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.Delete
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::Delete
ms.assetid: 6765ff80-a9a8-40a3-a669-7fcc284c87af
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c3522e5543d333443de5b1287c994bf29de51c9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576298"
---
# <a name="iscriptnodedelete"></a>IScriptNode::Delete
이 개체 트리를 삭제 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT Delete();  
```  
  
#### <a name="parameters"></a>매개 변수  
 메서드는 매개 변수를 사용 하지 않습니다.  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 @No__t_0 메서드가 호출 된 후 [Iscriptnode:: Alive](../../winscript/reference/iscriptnode-alive.md) 메서드는 스크립트 노드가 활성화 되지 않았음을 나타내야 합니다.  
  
## <a name="see-also"></a>참조  
 [IScriptNode 인터페이스](../../winscript/reference/iscriptnode-interface.md)