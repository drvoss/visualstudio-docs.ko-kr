---
title: 'IScriptNode:: Alive | Microsoft Docs'
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
ms.openlocfilehash: b7e0216824506ee942b42a42d5c3c4475f63f9e2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573620"
---
# <a name="iscriptnodealive"></a>IScriptNode::Alive
개체가 여전히 활성 상태 인지 여부를 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT Alive();  
```  
  
#### <a name="parameters"></a>매개 변수  
 메서드는 매개 변수를 사용 하지 않습니다.  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|스크립트 노드가 아직 활성 상태입니다.|  
  
## <a name="remarks"></a>주의  
 개체가 활성화 되어 있지 않으면 COM (구성 요소 개체 모델)이이 메서드에 대 한 호출에 대 한 마샬링 프록시에서 오류를 반환 합니다.  
  
## <a name="see-also"></a>참조  
 [IScriptNode 인터페이스](../../winscript/reference/iscriptnode-interface.md)