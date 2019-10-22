---
title: 'IActiveScriptAuthor:: GetEventHandler | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetEventHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetEventHandler
ms.assetid: 87c7a71d-46b9-448c-b34d-394105e20982
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c69b32f0040ea6d52e0712b8e1813cc5a0b40c58
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576224"
---
# <a name="iactivescriptauthorgeteventhandler"></a>IActiveScriptAuthor::GetEventHandler
지정 된 특성이 있는 scriptlet을 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetEventHandler(  
   IDispatch          *pdisp,  
   LPCOLESTR          pszItem,  
   LPCOLESTR          pszSubItem,  
   LPCOLESTR          pszEvent,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pdisp`  
 진행 Scriptlet가 연결 된 `NamedItem`에 해당 하는 `IDispatch` 개체입니다.  
  
 `pszItem`  
 진행 호스트에서 정규화 된 scriptlet name의 최상위 식별자에 대 한 버퍼 주소입니다.  
  
 `pszSubItem`  
 진행 호스트에서 정규화 된 scriptlet 이름의 두 번째 수준 식별자에 대 한 버퍼 주소입니다. 이름에 수준이 하나뿐인 경우 NULL로 설정 합니다.  
  
 `pszEvent`  
 진행 이벤트 이름을 포함 하는 버퍼의 주소입니다. Scriptlet는이 이벤트에 대 한 이벤트 처리기입니다.  
  
 `ppse`  
 제한이 지정 된 특성을 가진 scriptlet의 `IScriptEntry` 인터페이스에 대 한 포인터를 받는 변수의 주소입니다.  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
  
## <a name="see-also"></a>참조  
 [IActiveScriptAuthor 인터페이스](../../winscript/reference/iactivescriptauthor-interface.md)    
 [IScriptEntry 인터페이스](../../winscript/reference/iscriptentry-interface.md)