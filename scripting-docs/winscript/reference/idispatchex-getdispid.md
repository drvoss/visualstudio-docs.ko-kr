---
title: IDispatchEx::GetDispID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetDispID method
ms.assetid: a288d63d-b08a-4540-9d9d-0bcd182eff9a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 95ab1d72e5b2f608c51ac6e56be1986df8945ec2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63000858"
---
# <a name="idispatchexgetdispid"></a>IDispatchEx::GetDispID
해당 해당 경우 DISPID를 후속 호출에서 사용할 수 있는 단일 멤버 이름을 매핑합니다 `IDispatchEx::InvokeEx`합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetDispID(  
   BSTR bstrName,  
   DWORD grfdex,  
   DISPID *pid  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `bstrName`  
 매핑할 이름에 전달 합니다.  
  
 `grfdex`  
 멤버 식별자를 가져오기 위한 옵션을 결정 합니다. 다음 값의 조합 수 있습니다.  
  
|값|의미|  
|-----------|-------------|  
|fdexNameCaseSensitive|요청 이름 조회는 대/소문자 구분 방식으로 수행 합니다. 대/소문자 구분 조회를 지원 하지 않는 개체에 의해 무시 될 수 있습니다.|  
|fdexNameEnsure|아직 없는 경우는 멤버를 만들 수 있는지를 요청 합니다. 새 멤버 값을 사용 하 여 만들어야 `VT_EMPTY`합니다.|  
|fdexNameImplicit|기준 개체가 명시적으로 지정 하지 않으면 호출자가 특정 이름의 멤버에 대 한 개체를 검색 하를 나타냅니다.|  
|fdexNameCaseInsensitive|요청 이름 조회는 대/소문자 구분 방식으로 수행 합니다. 대/소문자 구분 조회를 지원 하지 않는 개체에 의해 무시 될 수 있습니다.|  
  
 `pid`  
 DISPID 결과 수신 하도록 호출자에 게 할당 된 위치에 대 한 포인터입니다. 오류가 발생 하는 경우 `pid` DISPID_UNKNOWN를 포함 합니다.  
  
## <a name="return-value"></a>반환 값  
 다음 값 중 하나를 반환합니다.  
  
|||  
|-|-|  
|`S_OK`|명령 실행 성공|  
|`E_OUTOFMEMORY`|메모리가 부족 합니다.|  
|`DISP_E_UNKNOWNNAME`|이름을 알 수 없습니다.|  
  
## <a name="remarks"></a>설명  
 `GetDispID` 대신 사용할 수 있습니다 `GetIDsOfNames` 지정된 된 멤버의 DISPID를 가져오려고 합니다.  
  
 때문에 `IDispatchEx` 추가 및 삭제, Dispid 집합 멤버 유지 되지 않습니다 상수 개체의 수명 동안 수 있습니다.  
  
 사용 되지 않은 `riid` 매개 변수에서 `IDispatch::GetIDsOfNames` 제거 되었습니다.  
  
## <a name="example"></a>예제  
  
```cpp
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
  
   // Assign to pdex and bstrName  
   pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid);  
   // Use dispid  
```  
  
## <a name="see-also"></a>참고 항목  
 [IDispatchEx 인터페이스](../../winscript/reference/idispatchex-interface.md)