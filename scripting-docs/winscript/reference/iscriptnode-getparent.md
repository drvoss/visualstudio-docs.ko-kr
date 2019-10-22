---
title: 'IScriptNode:: GetParent | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetParent
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetParent
ms.assetid: 0fb813f6-ab94-46b2-b0cf-ef5d1cd38ae4
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 58ef5f88f4404d57a7edad3590fba1d2614faec6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572561"
---
# <a name="iscriptnodegetparent"></a>IScriptNode::GetParent
개체의 부모인 `IScriptNode` 개체를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetParent(  
   IScriptNode       **ppsnParent  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ppsnParent`  
 제한이 부모 인스턴스의 `IScriptNode` 인터페이스에 대 한 포인터를 받는 변수의 주소입니다.  
  
 클래스가 `IScriptEntry` 또는 `IScriptScriptlet`를 구현 하는 경우 `IScriptNode` 개체가 반환 됩니다.  
  
 클래스가 `IScriptNode`를 구현 하는 경우 (웹 페이지를 나타냄) NULL이 반환 됩니다.  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
  
## <a name="see-also"></a>참조  
 [IScriptNode 인터페이스](../../winscript/reference/iscriptnode-interface.md)