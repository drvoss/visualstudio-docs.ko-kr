---
title: 'IActiveScript:: GetScriptSite | Microsoft Docs'
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
ms.openlocfilehash: 567c7b5c1ead5388e6ec9c67d6ab6f9f580adf20
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575738"
---
# <a name="iactivescriptgetscriptsite"></a>IActiveScript::GetScriptSite
Windows 스크립트 엔진과 연결 된 사이트 개체를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetScriptSite(  
    REFIID iid,           // interface identifier  
    void **ppvSiteObject  // address of host site interface  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `iid`  
 진행 요청 된 인터페이스의 식별자입니다.  
  
 `ppvSiteObject`  
 제한이 호스트의 사이트 개체에 대 한 인터페이스 포인터를 수신 하는 위치의 주소입니다.  
  
## <a name="return-value"></a>반환 값  
 는 다음 값 중 하나를 반환 합니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|`S_OK`|성공할.|  
|`E_INVALIDARG`|인수가 잘못 되었습니다.|  
|`E_NOINTERFACE`|지정 된 인터페이스가 지원 되지 않습니다.|  
|`E_POINTER`|잘못 된 포인터가 지정 되었습니다.|  
|`S_FALSE`|사이트가 설정 되지 않았습니다. `ppvSiteObject` 매개 변수는 `NULL`로 설정 됩니다.|  
  
## <a name="see-also"></a>참조  
 [IActiveScript](../../winscript/reference/iactivescript.md)