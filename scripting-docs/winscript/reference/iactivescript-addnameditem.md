---
title: 'IActiveScript:: AddNamedItem | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.AddNamedItem
apilocation:
- scrobj.dll
helpviewer_keywords:
- AddNamedItem method, IActiveScript interface
ms.assetid: a7c6317d-948f-4bb3-b169-1bbe5b7c7cc5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a343e38b944ca36da221da39832046c19b332230
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575820"
---
# <a name="iactivescriptaddnameditem"></a>IActiveScript::AddNamedItem
스크립트 엔진의 이름 공간에 루트 수준 항목의 이름을 추가 합니다. 루트 수준 항목은 속성 및 메서드, 이벤트 원본 또는 세 가지 모두를 포함 하는 개체입니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT AddNamedItem(  
    LPCOLESTR pstrName,  // address of item name  
    DWORD dwFlags          // item flags  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pstrName`  
 진행 스크립트에서 볼 때 항목의 이름을 포함 하는 버퍼의 주소입니다. 이름은 고유 해야 하며 지속 가능 해야 합니다.  
  
 `dwFlags`  
 진행 항목과 연결 된 플래그입니다. 는 다음과 같은 값을 조합 하 여 사용할 수 있습니다.  
  
|값|의미|  
|-----------|-------------|  
|SCRIPTITEM_CODEONLY|명명 된 항목이 코드 전용 개체를 나타내며 호스트에이 코드 전용 개체와 연결할 `IUnknown` 없음을 나타냅니다. 호스트에는이 개체의 이름만 있습니다. 과 C++같은 개체 지향 언어에서이 플래그는 클래스를 만듭니다. 모든 언어가이 플래그를 지 원하는 것은 아닙니다.|  
|SCRIPTITEM_GLOBALMEMBERS|항목이 스크립트와 연결 된 전역 속성 및 메서드의 모음 임을 나타냅니다. 일반적으로 스크립팅 엔진은 개체 이름 ( [IActiveScriptSite:: GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) 메서드에 대 한 쿠키로 사용 하거나 명시적 범위를 확인 하기 위해)을 무시 하 고 해당 멤버를 전역 변수 및 메서드로 노출 합니다. 이렇게 하면 호스트가 스크립트에서 사용할 수 있는 라이브러리 (런타임 함수 등)를 확장할 수 있습니다. 이러한 상황 때문에 오류가 반환 되어서는 안 되기는 하지만 이름 충돌 (예: 두 개의 SCRIPTITEM_GLOBALMEMBERS 항목에 동일한 이름의 메서드가 있는 경우)을 처리 하는 스크립팅 엔진이 남아 있습니다.|  
|SCRIPTITEM_ISPERSISTENT|스크립팅 엔진이 저장 된 경우 항목을 저장 해야 함을 나타냅니다. 마찬가지로이 플래그를 설정 하면 초기화 됨 상태로 다시 전환 하는 경우 항목의 이름과 형식 정보를 유지 해야 합니다. 그러나 스크립팅 엔진은 실제 개체의 인터페이스에 대 한 모든 포인터를 해제 해야 합니다.|  
|SCRIPTITEM_ISSOURCE|항목에서 스크립트가 싱크할 수 있는 이벤트를 소스 함을 나타냅니다. 자식 개체 (개체의 속성)는 스크립트에 이벤트를 발생 시킬 수도 있습니다. 이는 재귀적이 지 않지만 컨테이너와 모든 멤버 컨트롤을 만드는 경우와 같이 일반적인 경우에 편리 하 게 사용할 수 있는 메커니즘을 제공 합니다.|  
|SCRIPTITEM_ISVISIBLE|항목의 이름을 스크립트의 이름 공간에서 사용할 수 있음을 나타냅니다. 항목의 속성, 메서드 및 이벤트에 대 한 액세스를 허용 합니다. 규칙에 따라 항목의 속성은 항목의 자식을 포함 합니다. 따라서 모든 자식 개체 속성 및 메서드와 자식 (재귀적)에 액세스할 수 있습니다.|  
|SCRIPTITEM_NOCODE|항목은 단순히 스크립트의 이름 공간에 추가 되는 이름이 며 코드를 연결 해야 하는 항목으로 처리 되어서는 안 됨을 나타냅니다. 예를 들어이 플래그를 설정 하지 않으면 VBScript가 명명 된 항목에 대 한 별도의 모듈을 C++ 만들고 명명 된 항목에 대 한 별도의 래퍼 클래스를 만들 수 있습니다.|  
  
## <a name="return-value"></a>반환 값  
 는 다음 값 중 하나를 반환 합니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|`S_OK`|성공할.|  
|`E_INVALIDARG`|인수가 잘못 되었습니다.|  
|`E_POINTER`|잘못 된 포인터가 지정 되었습니다.|  
|`E_UNEXPECTED`|호출이 필요 하지 않습니다. 예를 들어 스크립팅 엔진이 아직 로드 되거나 초기화 되지 않았습니다.|  
  
## <a name="see-also"></a>참조  
 [IActiveScript](../../winscript/reference/iactivescript.md)