---
title: 'IActiveScript:: SetScriptSite | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.SetScriptSite
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_SetScriptSite
ms.assetid: 47d94c32-09f8-4539-ac56-0236026f627b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 063dcc7b580334bff9780e9c209b621ef7e25656
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575325"
---
# <a name="iactivescriptsetscriptsite"></a>IActiveScript::SetScriptSite
호스트에서 제공 하는 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) interface 사이트의 스크립팅 엔진에 알립니다. 다른 [IActiveScript](../../winscript/reference/iactivescript.md) 인터페이스 메서드를 사용 하기 전에이 메서드를 호출 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT SetScriptSite(  
    IActiveScriptSite *pScriptSite  // address of host script site  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pScriptSite`  
 진행 이 스크립팅 엔진 인스턴스와 연결할 호스트에서 제공 하는 스크립트 사이트의 주소입니다. 이 스크립팅 엔진 인스턴스에 사이트를 고유 하 게 할당 해야 합니다. 다른 스크립팅 엔진과 공유할 수 없습니다.  
  
## <a name="return-value"></a>반환 값  
 는 다음 값 중 하나를 반환 합니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|`S_OK`|성공할.|  
|`E_FAIL`|지정 되지 않은 오류가 발생 했습니다. 스크립팅 엔진이 사이트 초기화를 완료할 수 없습니다.|  
|`E_INVALIDARG`|인수가 잘못 되었습니다.|  
|`E_POINTER`|잘못 된 포인터가 지정 되었습니다.|  
|`E_UNEXPECTED`|호출이 필요 하지 않습니다 (예: 사이트가 이미 설정 된 경우).|  
  
## <a name="see-also"></a>참조  
 [IActiveScript](../../winscript/reference/iactivescript.md)