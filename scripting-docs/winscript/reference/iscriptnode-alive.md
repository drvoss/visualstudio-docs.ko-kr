---
title: IScriptNode::Alive | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.Alive
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::Alive
ms.assetid: d2755c83-e9b9-4c0a-acb7-25b554fc9fe8
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da0a55d26b5ab643670ba7ed51e576eeb89d8b98
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62787175"
---
# <a name="iscriptnodealive"></a>IScriptNode::Alive
개체가 아직 활성 인지를 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT Alive();  
```  
  
#### <a name="parameters"></a>매개 변수  
 메서드 매개 변수를 사용 합니다.  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|스크립트 노드가 여전히 활성입니다.|  
  
## <a name="remarks"></a>설명  
 개체가 활성 상태 이면이 메서드를 호출에 대 한 마샬링 프록시에서 오류를 반환 하는 구성 요소 개체 모델 (COM).  
  
## <a name="see-also"></a>참고 항목  
 [IScriptNode 인터페이스](../../winscript/reference/iscriptnode-interface.md)