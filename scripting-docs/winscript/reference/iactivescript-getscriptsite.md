---
title: IActiveScript::GetScriptSite | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptSite
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptSite
ms.assetid: 83a2a89d-93d0-4cbd-9244-91a730cb406b
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b57c4282b7ec77eb4af2ffa983479ae77388e1c9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935773"
---
# <a name="iactivescriptgetscriptsite"></a>IActiveScript::GetScriptSite
Windows 스크립트 엔진을 사용 하 여 연결 된 사이트 개체를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetScriptSite(  
    REFIID iid,           // interface identifier  
    void **ppvSiteObject  // address of host site interface  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `iid`  
 [in] 요청된 된 인터페이스의 식별자입니다.  
  
 `ppvSiteObject`  
 [out] 주소는 호스트의 사이트 개체에 대 한 인터페이스 포인터를 수신 하는 위치입니다.  
  
## <a name="return-value"></a>반환 값  
 다음 값 중 하나를 반환합니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|`S_OK`|명령 실행 성공|  
|`E_INVALIDARG`|인수가 잘못 되었습니다.|  
|`E_NOINTERFACE`|지정된 된 인터페이스는 지원 되지 않습니다.|  
|`E_POINTER`|잘못 된 포인터가 지정 되었습니다.|  
|`S_FALSE`|사이트 없이 설정한; 합니다 `ppvSiteObject` 매개 변수는 설정 `NULL`합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScript](../../winscript/reference/iactivescript.md)