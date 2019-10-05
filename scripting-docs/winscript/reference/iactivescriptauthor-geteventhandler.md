---
title: IActiveScriptAuthor::GetEventHandler | Microsoft Docs
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
ms.openlocfilehash: 7bba60df6485ddaac0363a3416739efd7be69389
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935635"
---
# <a name="iactivescriptauthorgeteventhandler"></a>IActiveScriptAuthor::GetEventHandler
지정 된 특성을 가진 scriptlet을 반환 합니다.  
  
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
 [in] `IDispatch` 에 해당 하는 개체는 `NamedItem` scriptlet 연결 됩니다.  
  
 `pszItem`  
 [in] 버퍼의 주소는 호스트에서 이름 정규화 scriptlet의 최상위 식별자입니다.  
  
 `pszSubItem`  
 [in] 버퍼의 주소는 호스트의 정규화 된 scriptlet 이름의 두 번째 수준 식별자입니다. 이름에 하나의 수준만 NULL로 설정 합니다.  
  
 `pszEvent`  
 [in] 이벤트 이름을 포함 하는 버퍼의 주소입니다. 스크립트릿은이 이벤트에 대 한 이벤트 처리기입니다.  
  
 `ppse`  
 [out] 에 대 한 포인터를 받는 변수의 주소는 `IScriptEntry` 지정 된 특성을 가진 scriptlet의 인터페이스입니다.  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>설명  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScriptAuthor 인터페이스](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IScriptEntry 인터페이스](../../winscript/reference/iscriptentry-interface.md)