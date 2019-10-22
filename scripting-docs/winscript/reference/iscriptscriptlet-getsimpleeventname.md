---
title: 'IScriptScriptlet:: GetSimpleEventName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptScriptlet. GetSimpleEventName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptScriptlet::GetSimpleEventName
ms.assetid: 012eb555-b26c-4248-bbcc-fc30e6f2b308
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51b8d3b31c92006c4f5b91a874bbb9d66ffa0b1b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561501"
---
# <a name="iscriptscriptlet-getsimpleeventname"></a>IScriptScriptlet:: GetSimpleEventName
Scriptlet와 연결 된 단순 이벤트 이름을 반환 합니다. 공백을 포함 하지 않는 단일 단어 이름입니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetSimpleEventName(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pbstr`  
 제한이 @No__t_0 개체와 연결 된 단순 이벤트 이름을 포함 하는 버퍼입니다.  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
  
## <a name="see-also"></a>참조  
 [IScriptScriptlet 인터페이스](../../winscript/reference/iscriptscriptlet-interface.md)