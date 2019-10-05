---
title: 'Iactivescript:: Addnameditem | Microsoft Docs'
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
ms.openlocfilehash: db0a97c01d948a0c26850ebd1c3f47c6e3900614
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935799"
---
# <a name="iactivescriptaddnameditem"></a>IActiveScript::AddNamedItem
스크립팅 엔진의 네임 스페이스에는 루트 수준 항목의 이름을 추가합니다. 루트 수준 항목은 속성 및 메서드, 이벤트 소스, 또는 세 가지 모두를 사용 하 여 개체.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT AddNamedItem(  
    LPCOLESTR pstrName,  // address of item name  
    DWORD dwFlags          // item flags  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pstrName`  
 [in] 스크립트에서 볼 때 항목의 이름을 포함 하는 버퍼의 주소입니다. 고유 하 고 유지할 수 있는 이름 이어야 합니다.  
  
 `dwFlags`  
 [in] 항목과 연결 된 플래그입니다. 이 값의 조합일 수 있습니다.  
  
|값|의미|  
|-----------|-------------|  
|SCRIPTITEM_CODEONLY|지정된 된 항목이 코드 전용 개체를 나타낸다고 나타내고 호스트 되지 `IUnknown` 이 코드 전용 개체와 연결 되도록 합니다. 호스트는이 개체에 대 한 이름을 가집니다. 와 같은 개체 지향 언어에서 C++에서이 플래그는 클래스를 만듭니다. 일부 언어는이 플래그를 지원합니다.|  
|SCRIPTITEM_GLOBALMEMBERS|전역 속성 및 메서드 스크립트에 연결 된 컬렉션 항목 임을 나타냅니다. 일반적으로 스크립팅 엔진 무시 개체 이름 (외에 대 한 쿠키로 사용 하기 위해 합니다 [iactivescriptsite:: Getiteminfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) 메서드를 또는 명시적 범위 지정을 확인 하는 데) 전역으로 멤버를 노출 하 고 변수 및 메서드를 제공 합니다. 따라서 호스트를 라이브러리를 확장 하는 (런타임 함수 및 등) 스크립트에 사용할 수 있습니다. 이름으로 처리 하기 위해 스크립팅 엔진에는 항목이 없으면 충돌 (예를 들어 두 SCRIPTITEM_GLOBALMEMBERS 항목이 있는 경우 동일한 이름의 메서드),이 상황으로 인해 오류를 반환할 수는 있지만 합니다.|  
|SCRIPTITEM_ISPERSISTENT|스크립팅 엔진이 저장 된 경우 항목을 저장할 수를 나타냅니다. 그러나 마찬가지로,이 플래그로 설정 다시 초기화 됨 상태 전환 (스크립팅 엔진, 릴리스해야 실제 개체의 인터페이스에 대 한 모든 포인터) 항목의 이름 및 형식 정보를 유지 해야 합니다.|  
|SCRIPTITEM_ISSOURCE|항목 원본 스크립트를 싱크할 수는 이벤트를 나타냅니다. 자식 개체 (개체의 속성 개체 자체에 있는) 스크립트에는 이벤트 소스도 수 있습니다. 이 재귀, 하지만 컨테이너 및 해당 멤버의 모든 컨트롤을 만드는 예를 들어, 일반적인 사례에 대 한 편리한 메커니즘을 제공 합니다.|  
|SCRIPTITEM_ISVISIBLE|속성, 메서드 및 항목의 이벤트에 대 한 액세스를 허용 하는 스크립트의 네임 스페이스에서 사용할 수 있는 항목의 이름을 나타냅니다. 규칙에 따라 항목의 속성 포함 항목의 자식입니다. 따라서 모든 자식 개체 속성 및 메서드 (및 해당 자식을 재귀적으로) 액세스할 수 있습니다.|  
|SCRIPTITEM_NOCODE|항목 이름이 단순히 스크립트의 네임 스페이스에 추가할 코드를 연결 해야 하는 항목으로 처리 되지 않아야 함을 나타냅니다. 예를 들어,이 플래그가 설정 되 고 없으면 VBScript 만들어집니다 명명 된 항목에 대해 별도 모듈 및 C++ 명명 된 항목에 대 한 별도 래퍼 클래스를 만들 수 있습니다.|  
  
## <a name="return-value"></a>반환 값  
 다음 값 중 하나를 반환합니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|`S_OK`|명령 실행 성공|  
|`E_INVALIDARG`|인수가 잘못 되었습니다.|  
|`E_POINTER`|잘못 된 포인터가 지정 되었습니다.|  
|`E_UNEXPECTED`|호출이 필요 하지 않습니다 (예를 들어, 스크립팅 엔진에 아직 로드 되지 않았거나 초기화).|  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScript](../../winscript/reference/iactivescript.md)