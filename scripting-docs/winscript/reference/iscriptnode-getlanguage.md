---
title: 'IScriptNode:: GetLanguage | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetLanguage
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetLanguage
ms.assetid: 089715fd-6746-474e-94ed-2e57ee4bc0da
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 26fd5db22346292585be3cea751eaa8be1c284a9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575689"
---
# <a name="iscriptnodegetlanguage"></a>IScriptNode::GetLanguage
현재 스크립트 노드에서 사용 하는 스크립트 언어를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetLanguage(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pbstr`  
 제한이 스크립트 노드가 JScript를 사용 하는 경우 "JScript"를 반환 하 고 스크립트 노드에서 Visual Basic Scripting Edition (VBScript)를 사용 하는 경우 "VBScript"를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
  
## <a name="see-also"></a>참조  
 [IScriptNode 인터페이스](../../winscript/reference/iscriptnode-interface.md)