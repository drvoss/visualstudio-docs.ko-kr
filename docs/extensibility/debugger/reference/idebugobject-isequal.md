---
title: IDebugObject::IsEqual | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 91e84d47f7fc60e60c3c7fb58ba66bc0a00daf30
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49840001"
---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
이 개체를 사용 하 여 개체를 비교합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT IsEqual(   
   IDebugObject* pObject,  
   BOOL*         pfIsEqual  
);  
```  
  
```csharp  
int IsEqual(  
   IDebugObject pObject,  
   out int      pfIsEqual  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pObject`  
 [in] [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 비교할 개체를 나타내는 개체입니다.  
  
 `pfIsEqual`  
 [out] 0이 아닌 값을 반환 합니다 (`TRUE`) 개체의 값이 고 그렇지 않으면 동일한 경우 0을 반환 합니다 (`FALSE`).  
  
## <a name="return-value"></a>반환 값  
 성공 하면 S_OK를 반환 합니다. 그렇지 않으면 오류 코드를 반환합니다.  
  
## <a name="remarks"></a>설명  
 이 메서드 주소를 나타내는 값을 비교할 수는 일반적으로 `pObject` 매개 변수 및이 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 개체; 주소가 같지 않으면 개체는 같은 간주 될 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)