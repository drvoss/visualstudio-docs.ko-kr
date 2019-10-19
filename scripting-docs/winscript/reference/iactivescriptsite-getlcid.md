---
title: 'IActiveScriptSite:: GetLCID | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetLCID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetLCID
ms.assetid: 7b4a2dc1-bcf6-4bbf-884e-97b305a28eb7
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 913ca23ac687fdd080a778afb1dcba2e4dcdd6b8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570745"
---
# <a name="iactivescriptsitegetlcid"></a>IActiveScriptSite::GetLCID
호스트의 사용자 인터페이스와 연결 된 로캘 식별자를 검색 합니다. 스크립팅 엔진은 식별자를 사용 하 여 엔진에서 생성 된 오류 문자열과 기타 사용자 인터페이스 요소가 해당 언어로 표시 되도록 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetLCID(  
    LCID *plcid  // address of variable for language identifier  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `plcid`  
 제한이 스크립팅 엔진에서 표시 하는 사용자 인터페이스 요소에 대 한 로캘 식별자를 수신 하는 변수의 주소입니다.  
  
## <a name="return-value"></a>반환 값  
 는 다음 값 중 하나를 반환 합니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|`S_OK`|성공할.|  
|`E_NOTIMPL`|이 메서드는 구현 되지 않습니다. 시스템 정의 로캘을 사용 합니다.|  
|`E_POINTER`|잘못 된 포인터가 지정 되었습니다.|  
  
## <a name="remarks"></a>주의  
 이 메서드가 `E_NOTIMPL` 반환 하는 경우 시스템 정의 로캘 식별자를 사용 해야 합니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)