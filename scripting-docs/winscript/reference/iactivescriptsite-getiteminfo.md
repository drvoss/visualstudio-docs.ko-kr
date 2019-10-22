---
title: 'IActiveScriptSite:: GetItemInfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetItemInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetItemInfo
ms.assetid: f859ed3b-02c1-4924-99f8-5f5bf1bf8405
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c0458f42466a264c30a440b1b14a028a2457f12
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570920"
---
# <a name="iactivescriptsitegetiteminfo"></a>IActiveScriptSite::GetItemInfo
스크립팅 엔진이 [IActiveScript:: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) 메서드를 사용 하 여 추가 된 항목에 대 한 정보를 가져올 수 있도록 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetItemInfo(  
    LPCOLESTR pstrName,     // address of item name  
    DWORD dwReturnMask,     // bit mask for information retrieval  
    IUnknown **ppunkItem,   // address of pointer to item's IUnknown  
    ITypeInfo **ppTypeInfo  // address of pointer to item's ITypeInfo  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pstrName`  
 진행 [IActiveScript:: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) 메서드에 지정 된 항목에 연결 된 이름입니다.  
  
 `dwReturnMask`  
 진행 반환 되어야 하는 항목에 대 한 정보를 지정 하는 비트 마스크입니다. 반환 매개 변수 (예: `ITypeInfo`)의 일부는 로드 하거나 생성 하는 데 상당한 시간이 걸릴 수 있으므로 스크립팅 엔진은 가능한 최소한의 정보만 요청 해야 합니다. 은 다음 값을 조합 하 여 사용할 수 있습니다.  
  
|값|의미|  
|-----------|-------------|  
|SCRIPTINFO_IUNKNOWN|이 항목에 대 한 `IUnknown` 인터페이스를 반환 합니다.|  
|SCRIPTINFO_ITYPEINFO|이 항목에 대 한 `ITypeInfo` 인터페이스를 반환 합니다.|  
  
 `ppunkItem`  
 제한이 지정 된 항목과 연결 된 `IUnknown` 인터페이스에 대 한 포인터를 받는 변수의 주소입니다. 스크립팅 엔진은 `IUnknown::QueryInterface` 메서드를 사용 하 여 항목의 `IDispatch` 인터페이스를 가져올 수 있습니다. @No__t_0에 SCRIPTINFO_IUNKNOWN 값이 포함 되어 있지 않으면이 매개 변수는 NULL을 받습니다. 또한 항목 이름과 연결 된 개체가 없는 경우 NULL을 수신 합니다. 이 메커니즘은 [IActiveScript:: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) 메서드에 설정 된 SCRIPTITEM_CODEONLY 플래그를 사용 하 여 명명 된 항목이 추가 된 경우 간단한 클래스를 만드는 데 사용 됩니다.  
  
 `ppTypeInfo`  
 제한이 항목과 연결 된 `ITypeInfo` 인터페이스에 대 한 포인터를 받는 변수의 주소입니다. 이 매개 변수는 `dwReturnMask`에 SCRIPTINFO_ITYPEINFO 값이 포함 되어 있지 않거나이 항목에 대해 형식 정보를 사용할 수 없는 경우 NULL을 받습니다. 형식 정보를 사용할 수 없는 경우 개체는 이벤트를 발생 시킬 수 없으며 `IDispatch::GetIDsOfNames` 메서드를 사용 하 여 이름 바인딩을 인식 해야 합니다. 개체에서 여러 인터페이스와 이벤트 인터페이스를 지원할 수 있으므로 검색 된 `ITypeInfo` 인터페이스는 항목의 coclass (TKIND_COCLASS)에 대해 설명 합니다. 항목이 `IProvideMultipleTypeInfo` 인터페이스를 지 원하는 경우 검색 된 `ITypeInfo` 인터페이스는 `IProvideMultipleTypeInfo::GetInfoOfIndex` 메서드를 사용 하 여 얻을 수 있는 인덱스 0 `ITypeInfo`와 동일 합니다.  
  
## <a name="return-value"></a>반환 값  
 는 다음 값 중 하나를 반환 합니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|`S_OK`|성공할.|  
|`E_INVALIDARG`|인수가 잘못 되었습니다.|  
|`E_POINTER`|잘못 된 포인터가 지정 되었습니다.|  
|`TYPE_E_ELEMENTNOTFOUND`|지정 된 이름의 항목을 찾을 수 없습니다.|  
  
## <a name="remarks"></a>주의  
 이 메서드는 `dwReturnMask` 매개 변수로 표시 된 정보만 검색 합니다. 이렇게 하면 성능이 향상 됩니다. 예를 들어 항목에 `ITypeInfo` 인터페이스가 필요 하지 않은 경우에는 `dwReturnMask`에 지정 되지 않습니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)