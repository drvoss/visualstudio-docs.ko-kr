---
title: IScriptNode::Delete | Microsoft Docs
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
ms.openlocfilehash: 41bf932b242865b1deac4c61db400f973bd0b00c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62787162"
---
# <a name="iscriptnodedelete"></a>IScriptNode::Delete
이 개체 트리를 삭제합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT Delete();  
```  
  
#### <a name="parameters"></a>매개 변수  
 메서드 매개 변수를 사용 합니다.  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>설명  
 후 합니다 `Delete` 메서드를 호출 합니다 [IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md) 메서드는 스크립트 노드가 비활성 상태임을 지정 해야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IScriptNode 인터페이스](../../winscript/reference/iscriptnode-interface.md)