---
title: 'Iactivescriptsite:: Getiteminfo | Microsoft Docs'
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
ms.openlocfilehash: 997245f8e4fd43ac2162587f07e4c8711af7caac
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992743"
---
# <a name="iactivescriptsitegetiteminfo"></a>IActiveScriptSite::GetItemInfo
스크립팅 엔진이 사용 하 여 추가 된 항목에 대 한 정보를 얻을 수 있게 합니다 [iactivescript:: Addnameditem](../../winscript/reference/iactivescript-addnameditem.md) 메서드.  
  
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
 [in] 에 지정 된 항목과 연결 된 이름을 합니다 [iactivescript:: Addnameditem](../../winscript/reference/iactivescript-addnameditem.md) 메서드.  
  
 `dwReturnMask`  
 [in] 항목에 대 한 정보를 반환할지를 지정 하는 비트 마스크입니다. 스크립팅 엔진 때문에 사용할 수 있는 정보가의 최소 크기를 요청 해야 반환 매개 변수 중 일부 (예를 들어 `ITypeInfo`) 로드 하거나 생성 하는 데 상당한 시간이 걸릴 수 있습니다. 다음 값의 조합일 수 있습니다.  
  
|값|의미|  
|-----------|-------------|  
|SCRIPTINFO_IUNKNOWN|반환 된 `IUnknown` 이 항목에 대 한 인터페이스입니다.|  
|SCRIPTINFO_ITYPEINFO|반환 된 `ITypeInfo` 이 항목에 대 한 인터페이스입니다.|  
  
 `ppunkItem`  
 [out] 에 대 한 포인터를 받는 변수의 주소는 `IUnknown` 지정 된 항목과 연결 된 인터페이스입니다. 스크립팅 엔진을 사용 하 여 수를 `IUnknown::QueryInterface` 메서드를 `IDispatch` 항목에 대 한 인터페이스입니다. 이 매개 변수 경우 NULL을 받는 `dwReturnMask` SCRIPTINFO_IUNKNOWN 값이 포함 되지 않습니다. 또한 수신한 NULL 항목 이름과; 연결 된 개체가 없는 경우 이 메커니즘 설정 된 SCRIPTITEM_CODEONLY 플래그를 사용 하 여 명명 된 항목을 추가할 때 간단한 클래스를 만드는 데 사용 되는 [iactivescript:: Addnameditem](../../winscript/reference/iactivescript-addnameditem.md) 메서드.  
  
 `ppTypeInfo`  
 [out] 에 대 한 포인터를 받는 변수의 주소는 `ITypeInfo` 항목과 연결 된 인터페이스입니다. 하는 경우이 매개 변수는 NULL을 받습니다 `dwReturnMask` SCRIPTINFO_ITYPEINFO 값이 포함 되지 않습니다 또는 형식 정보를이 항목에 대해 사용할 수 없는 경우. 형식 정보를 사용할 수 없는 경우, 개체 이벤트 원본 없습니다 및 이름 바인딩을 사용 하 여 필요 하는 경우는 `IDispatch::GetIDsOfNames` 메서드. `ITypeInfo` 검색 인터페이스 개체 여러 인터페이스 및 이벤트 인터페이스를 지원할 수 있으므로 항목의 coclass (TKIND_COCLASS)에 대해 설명 합니다. 항목에서 지 원하는 경우는 `IProvideMultipleTypeInfo` 인터페이스를 `ITypeInfo` 검색 하는 인터페이스는 인덱스 0으로 동일 `ITypeInfo` 를 사용 하 여 가져온 것는 `IProvideMultipleTypeInfo::GetInfoOfIndex` 메서드.  
  
## <a name="return-value"></a>반환 값  
 다음 값 중 하나를 반환합니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|`S_OK`|명령 실행 성공|  
|`E_INVALIDARG`|인수가 잘못 되었습니다.|  
|`E_POINTER`|잘못 된 포인터가 지정 되었습니다.|  
|`TYPE_E_ELEMENTNOTFOUND`|지정 된 이름의 항목을 찾을 수 없습니다.|  
  
## <a name="remarks"></a>설명  
 이 메서드를 가리키는 정보만 검색 합니다 `dwReturnMask` 매개 변수; 성능이 향상 됩니다. 예를 들어 경우는 `ITypeInfo` 인터페이스 항목에 대 한 필요 하지 않은 단순히 지정 되지 않은에서 `dwReturnMask`합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)