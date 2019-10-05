---
title: IActiveScriptSite::OnScriptError | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnScriptError
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnScriptError
ms.assetid: 5c9c85cc-21ad-4232-be83-a24cc7570108
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d76aa46cbbcdab9a3c5c7b561b91ee58cfcac4ac
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992600"
---
# <a name="iactivescriptsiteonscripterror"></a>IActiveScriptSite::OnScriptError
엔진을 스크립트를 실행 하는 동안 실행 오류가 발생 했음을 호스트에 알립니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT OnScriptError(  
    IActiveScriptError *pase  // address of error interface  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pase`  
 [in] 오류 개체의 주소 [IActiveScriptError](../../winscript/reference/iactivescripterror.md) 인터페이스입니다. 호스트는이 인터페이스를 사용 하 여 실행 오류에 대 한 정보를 가져올 수 있습니다.  
  
## <a name="return-value"></a>반환 값  
 반환 `S_OK` OLE 오류 코드를 그렇지 않으면 정의 또는 오류를 올바르게 처리 하는 경우.  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)