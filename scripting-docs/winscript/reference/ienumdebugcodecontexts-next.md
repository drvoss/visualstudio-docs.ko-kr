---
title: 'IEnumDebugCodeContexts:: Next | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugCodeContexts.Next
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugCodeContexts::Next
ms.assetid: 844cc353-ae0b-45e1-84a6-32b0bb67f57f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 289085265f182ec0fafca27a2cc18e8865b98091
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577169"
---
# <a name="ienumdebugcodecontextsnext"></a>IEnumDebugCodeContexts::Next
열거형 시퀀스에서 지정 된 수의 세그먼트를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT Next(  
   ULONG                celt,  
   IDebugCodeContext**  pscc,  
   ULONG*               pceltFetched  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `celt`  
 진행 검색할 세그먼트 수입니다.  
  
 `pscc`  
 제한이 검색 되는 세그먼트를 나타내는 `IDebugCodeContext` 인터페이스의 배열을 반환 합니다.  
  
 `pceltFetched`  
 제한이 열거자에서 가져온 실제 세그먼트 수입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 열거형 시퀀스에서 지정 된 수의 세그먼트를 검색 합니다.  
  
## <a name="see-also"></a>참조  
 [IEnumDebugCodeContexts 인터페이스](../../winscript/reference/ienumdebugcodecontexts-interface.md)