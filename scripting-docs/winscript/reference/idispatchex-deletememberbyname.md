---
title: IDispatchEx::D eleteMemberByName | Microsoft Docs
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
ms.openlocfilehash: 2abb562f65885ee1d12f2ec9b2300fcddd3be37b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576614"
---
# <a name="idispatchexdeletememberbyname"></a>IDispatchEx::DeleteMemberByName
이름을 기준으로 멤버를 삭제 합니다.  
  
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
 멤버 이름이 대/소문자를 구분 하는지 여부를 확인 합니다. 이 값은 다음 값 중 하나일 수 있습니다.  
  
|값|의미|  
|-----------|-------------|  
|fdexNameCaseSensitive|대/소문자 구분 방식으로 이름 조회를 수행 하도록 요청 합니다. 대/소문자를 구분 하는 조회를 지원 하지 않는 개체에서 무시할 수 있습니다.|  
|fdexNameCaseInsensitive|대/소문자를 구분 하지 않는 방식으로 이름 조회를 수행 하도록 요청 합니다. 대/소문자를 구분 하지 않는 조회를 지원 하지 않는 개체에서 무시할 수 있습니다.|  
  
## <a name="return-value"></a>반환 값  
 는 다음 값 중 하나를 반환 합니다.  
  
|||  
|-|-|  
|`S_OK`|성공할.|  
|`S_FALSE`|멤버가 있지만 삭제할 수 없습니다.|  
  
## <a name="remarks"></a>주의  
 멤버가 삭제 된 경우 DISPID는 `GetNextDispID`에 대해 유효한 상태로 유지 되어야 합니다.  
  
 지정 된 이름의 멤버를 삭제 하 고 나중에 동일한 이름의 멤버를 다시 만들 경우 DISPID는 동일 해야 합니다. 대/소문자만 다른 멤버가 "동일" 인지 여부는 개체에 따라 달라 집니다.  
  
## <a name="example"></a>예제  
  
```cpp
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## <a name="see-also"></a>참조  
 [IDispatchEx 인터페이스](../../winscript/reference/idispatchex-interface.md)