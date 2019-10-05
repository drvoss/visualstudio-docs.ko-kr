---
title: IDispatchEx::DeleteMemberByName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.DeleteMemberByName
apilocation:
- scrobj.dll
helpviewer_keywords:
- DeleteMemberByName method
ms.assetid: a01b4e6a-d989-4b29-bb3f-04554f8c39f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc7c8db4ab28e0bd0fcb48f352cb07595f72fd17
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63000895"
---
# <a name="idispatchexdeletememberbyname"></a>IDispatchEx::DeleteMemberByName
이름으로 멤버를 삭제합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT DeleteMemberByName(  
   BSTR bstrName,  
   DWORD grfdex  
  
```  
  
#### <a name="parameters"></a>매개 변수  
 `bstrName`  
 삭제할 멤버의 이름입니다.  
  
 `grfdex`  
 멤버 이름이 대/소문자 구분을 결정 합니다. 다음 값 중 하나일 수 있습니다.  
  
|값|의미|  
|-----------|-------------|  
|fdexNameCaseSensitive|요청 이름 조회는 대/소문자 구분 방식으로 수행 합니다. 대/소문자 구분 조회를 지원 하지 않는 개체에 의해 무시 됩니다.|  
|fdexNameCaseInsensitive|요청 이름 조회는 대/소문자 구분 방식으로 수행 합니다. 대/소문자 구분 조회를 지원 하지 않는 개체에 의해 무시 됩니다.|  
  
## <a name="return-value"></a>반환 값  
 다음 값 중 하나를 반환합니다.  
  
|||  
|-|-|  
|`S_OK`|명령 실행 성공|  
|`S_FALSE`|멤버가 있지만 삭제할 수 없습니다.|  
  
## <a name="remarks"></a>설명  
 경우 DISPID를 유효한 상태를 유지 해야 멤버 삭제 되 면 `GetNextDispID`합니다.  
  
 지정 된 이름을 가진 멤버는를 삭제 하 고 나중에 동일한 이름 가진 멤버를 다시 만들 경우 dispid가 동일 해야 합니다. (대/소문자만 다른 멤버인 "same" 한지 종속 개체입니다.)  
  
## <a name="example"></a>예제  
  
```cpp
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## <a name="see-also"></a>참고 항목  
 [IDispatchEx 인터페이스](../../winscript/reference/idispatchex-interface.md)