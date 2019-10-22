---
title: 'IScriptNode:: GetChild | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetChild
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetChild
ms.assetid: 8cb3f8b0-958b-40bb-a91a-49a788661861
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 27ddde527be1ea4148e4166581ab2cb1a71d15f7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573561"
---
# <a name="iscriptnodegetchild"></a>IScriptNode::GetChild
노드의 지정 된 인덱스에 있는 자식을 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetChild(  
   ULONG              isn,  
   IScriptNode        **ppsn  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `isn`  
 진행 부모에 있는 자식의 인덱스입니다.  
  
 `ppsn`  
 제한이 자식 인스턴스의 `IScriptNode` 인터페이스에 대 한 포인터를 받는 변수의 주소입니다.  
  
 웹 페이지를 나타내는 `IScriptNode` 개체의 경우이 매개 변수는 스크립트 블록을 포함 하는 개체를 반환 합니다.  
  
 스크립트 블록을 지정 하는 `IScriptEntry` 개체의 경우이 매개 변수는 함수를 지정 하는 개체를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 함수 개체와 `IScriptScriptlet` 개체를 지정 하는 `IScriptEntry` 개체의 경우 자식 항목이 없으므로이 메서드는 실패 합니다.  
  
## <a name="see-also"></a>참조  
 [IScriptNode 인터페이스](../../winscript/reference/iscriptnode-interface.md)