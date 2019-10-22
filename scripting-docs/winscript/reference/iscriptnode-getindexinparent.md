---
title: 'IScriptNode:: GetIndexInParent | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetIndexInParent
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetIndexInParent
ms.assetid: 521c1ca1-2d27-4344-bf3b-d8b53132b648
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9251f65414a5ebd48ce56dae6a7dbfeec4e514e3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575038"
---
# <a name="iscriptnodegetindexinparent"></a>IScriptNode::GetIndexInParent
부모의 자식 목록에 있는 개체의 인덱스를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetIndexInParent(  
   ULONG              pisn,  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pisn`  
 제한이 부모의 자식 목록에 있는 개체의 인덱스를 반환 합니다.  
  
 웹 페이지를 나타내는 `IScriptNode` 개체에서이 메서드를 호출 하는 경우이 매개 변수는 0을 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
  
## <a name="see-also"></a>참조  
 [IScriptNode 인터페이스](../../winscript/reference/iscriptnode-interface.md)