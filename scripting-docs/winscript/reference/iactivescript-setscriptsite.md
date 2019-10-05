---
title: IActiveScript::SetScriptSite | Microsoft Docs
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
ms.openlocfilehash: 3fdf5f3ae84d1a991d67170b5f2b02114b91ee05
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935556"
---
# <a name="iactivescriptsetscriptsite"></a>IActiveScript::SetScriptSite
스크립팅 엔진에 알립니다 합니다 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) 인터페이스 사이트 호스트에서 제공 합니다. 다른 전에이 메서드를 호출 [IActiveScript](../../winscript/reference/iactivescript.md) 인터페이스 메서드가 사용 됩니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT SetScriptSite(  
    IActiveScriptSite *pScriptSite  // address of host script site  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pScriptSite`  
 [in] 스크립팅 엔진의이 인스턴스와 연결 되도록 호스트 제공 하는 스크립트 사이트의 주소입니다. 스크립팅 엔진 인스턴스에;에 사이트를 고유 하 게 할당 되어야 합니다. 다른 스크립팅 엔진을 사용 하 여 공유할 수 없습니다.  
  
## <a name="return-value"></a>반환 값  
 다음 값 중 하나를 반환합니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|`S_OK`|명령 실행 성공|  
|`E_FAIL`|지정 되지 않은 오류가 발생 했습니다. 스크립팅 엔진 사이트 초기화를 완료할 수 없습니다.|  
|`E_INVALIDARG`|인수가 잘못 되었습니다.|  
|`E_POINTER`|잘못 된 포인터가 지정 되었습니다.|  
|`E_UNEXPECTED`|호출이 필요 하지 않습니다 (예를 들어 사이트를 이미 설정한).|  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScript](../../winscript/reference/iactivescript.md)