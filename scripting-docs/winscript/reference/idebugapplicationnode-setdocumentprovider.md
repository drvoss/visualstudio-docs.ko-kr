---
title: 'IDebugApplicationNode:: SetDocumentProvider | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNode.SetDocumentProvider
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationNode::SetDocumentProvider
ms.assetid: 7cb587ca-d84e-4b5e-9b94-e973cca55a03
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dd1588ed1bb365e88bb3b09ee5093f15ac7a161
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574818"
---
# <a name="idebugapplicationnodesetdocumentprovider"></a>IDebugApplicationNode::SetDocumentProvider
이 응용 프로그램 노드에 대 한 문서 공급자를 설정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT SetDocumentProvider(  
   IDebugDocumentProvider*  pddp  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pddp`  
 진행 이 응용 프로그램 노드에 대 한 문서 공급자입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는이 응용 프로그램 노드에 대 한 문서 공급자를 설정 합니다.  
  
## <a name="see-also"></a>참조  
 [IDebugApplicationNode 인터페이스](../../winscript/reference/idebugapplicationnode-interface.md)