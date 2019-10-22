---
title: 'IActiveScriptSite:: OnScriptError | Microsoft Docs'
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
ms.openlocfilehash: 9f0078b53515a881d7f2ac1475cf5565fa22a025
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570275"
---
# <a name="iactivescriptsiteonscripterror"></a>IActiveScriptSite::OnScriptError
엔진에서 스크립트를 실행 하는 동안 실행 오류가 발생 했음을 호스트에 알립니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT OnScriptError(  
    IActiveScriptError *pase  // address of error interface  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pase`  
 진행 오류 개체의 [IActiveScriptError](../../winscript/reference/iactivescripterror.md) 인터페이스 주소입니다. 호스트는이 인터페이스를 사용 하 여 실행 오류에 대 한 정보를 가져올 수 있습니다.  
  
## <a name="return-value"></a>반환 값  
 오류가 올바르게 처리 된 경우 `S_OK`을 반환 하 고 그렇지 않으면 OLE 정의 오류 코드를 반환 합니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)