---
title: 'IActiveScript:: Clone | Microsoft Docs'
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
ms.openlocfilehash: fbaad29cb31af26a0f26a1c679a900192fc77041
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575793"
---
# <a name="iactivescriptclone"></a>IActiveScript::Clone
현재 실행 상태를 제외 하 고 현재 스크립팅 엔진을 복제 하 여 현재 스레드에 사이트가 없는 로드 된 스크립팅 엔진을 반환 합니다. 이 새 스크립팅 엔진의 속성은 초기화 된 상태로 다시 전환 된 경우 원래 스크립팅 엔진의 속성과 동일 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ppscript`  
 제한이 복제 된 스크립팅 엔진의 [IActiveScript](../../winscript/reference/iactivescript.md) 인터페이스에 대 한 포인터를 받는 변수의 주소입니다. 호스트는 사이트를 만들고 새 스크립팅 엔진에서 [IActiveScript:: SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) 메서드를 호출 하 여 초기화 된 상태에 있기 때문에 사용 가능한 상태 여야 합니다.  
  
## <a name="return-value"></a>반환 값  
 는 다음 값 중 하나를 반환 합니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|`S_OK`|성공할.|  
|`E_NOTIMPL`|이 메서드는 지원되지 않습니다.|  
|`E_POINTER`|잘못 된 포인터가 지정 되었습니다.|  
|`E_UNEXPECTED`|호출이 필요 하지 않습니다. 예를 들어 스크립팅 엔진이 아직 로드 되거나 초기화 되지 않았습니다.|  
  
## <a name="remarks"></a>주의  
 @No__t_0 메서드는 `IPersist*::Save`, `CoCreateInstance` 및 `IPersist*::Load`에 대 한 최적화 이므로 새 스크립팅 엔진의 상태는 원래 스크립팅 엔진의 상태가 새 스크립팅 엔진에 저장 되 고 로드 된 것과 동일 해야 합니다. 명명 된 항목은 복제 된 스크립팅 엔진에서 중복 되지만 각 항목에 대 한 특정 개체 포인터는 기억나지 않으며 [IActiveScriptSite:: GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) 메서드를 사용 하 여 가져옵니다. 따라서 스레드 단위 진입점 (아파트 모델)을 사용 하는 동일한 개체 모델을 사용할 수 있습니다.  
  
 이 메서드는 동일한 스크립트의 여러 인스턴스를 실행할 수 있는 다중 스레드 서버 호스트에 사용 됩니다. 스크립팅 엔진은 `E_NOTIMPL`를 반환할 수 있습니다 .이 경우 호스트는 영구 상태를 복제 하 고 `IPersist*` 인터페이스를 사용 하 여 스크립팅 엔진의 새 인스턴스를 만들어 동일한 결과를 얻을 수 있습니다.  
  
 이 메서드는 기본이 아닌 스레드에서 개체를 호스트 하거나 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) 인터페이스를 호스트 하는 경우를 제외 하 고는 기본이 아닌 스레드에서 호출 될 수 있습니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScript](../../winscript/reference/iactivescript.md)