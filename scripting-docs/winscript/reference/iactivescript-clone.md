---
title: 'Iactivescript:: Clone | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.Clone
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_Clone
ms.assetid: aa000b2a-7085-448d-a422-f7adac7851cb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bec912596c792a67f65434062bc0d0ed11bd3fb9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935707"
---
# <a name="iactivescriptclone"></a>IActiveScript::Clone
현재 스크립팅 엔진 (빼기 모든 현재 실행 상태)를 현재 스레드에서 사이트가 있는 로드 된 스크립팅 엔진 반환을 복제 합니다. 이 새 스크립팅 엔진의 속성은 원래 스크립팅 엔진 수 초기화 된 상태로 전환 된 경우 속성에 동일 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ppscript`  
 [out] 에 대 한 포인터를 받는 변수의 주소는 [IActiveScript](../../winscript/reference/iactivescript.md) 복제 스크립팅 엔진의 인터페이스입니다. 호스트는 사이트 및 호출을 만들어야 합니다.는 [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) 메서드를 사용 하기 전에 초기화 된 상태에서 새 스크립팅 엔진에서 이며, 따라서 사용할 수 있습니다.  
  
## <a name="return-value"></a>반환 값  
 다음 값 중 하나를 반환합니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|`S_OK`|명령 실행 성공|  
|`E_NOTIMPL`|이 메서드는 지원되지 않습니다.|  
|`E_POINTER`|잘못 된 포인터가 지정 되었습니다.|  
|`E_UNEXPECTED`|호출이 필요 하지 않습니다 (예를 들어, 스크립팅 엔진에 아직 로드 되지 않았거나 초기화).|  
  
## <a name="remarks"></a>설명  
 `IActiveScript::Clone` 최적화 하는 방법은 `IPersist*::Save`, `CoCreateInstance`, 및 `IPersist*::Load`이므로 새 스크립팅 엔진의 상태 원래 스크립팅 엔진의 상태 저장 되었으며 새 스크립팅 엔진을 로드 하는 경우에 따라 동일한 이어야 합니다. 복제 스크립팅 엔진의 명명 된 항목은 중복 되지만 각 항목에 대 한 특정 개체 포인터 혀 및 사용 하 여 가져온 합니다 [iactivescriptsite:: Getiteminfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) 메서드. 이렇게 하면 동일한 개체 모델을 스레드별 진입점 (아파트 모델)을 사용할 수 있습니다.  
  
 이 메서드는 동일한 스크립트의 여러 인스턴스를 실행할 수 있는 다중 스레드 서버 호스트에 사용 됩니다. 스크립팅 엔진에서 반환 될 수 있습니다 `E_NOTIMPL`, 호스트 영구 상태를 복제 하 고 사용 하 여 스크립팅 엔진의 새 인스턴스를 만들어 동일한 결과 얻을 수 있는 경우에 `IPersist*` 인터페이스입니다.  
  
 호스트 개체 또는 기본이 아닌 설명선 발생 하지 않고 기본이 아닌 스레드에서이 메서드를 호출할 수는 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) 인터페이스입니다.  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScript](../../winscript/reference/iactivescript.md)