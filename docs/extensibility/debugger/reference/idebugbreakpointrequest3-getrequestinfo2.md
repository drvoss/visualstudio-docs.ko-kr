---
title: IDebugBreakpointRequest3::GetRequestInfo2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBreakpointRequest3::GetRequestInfo2
helpviewer_keywords:
- IDebugBreakpointRequest3::GetRequestInfo2
ms.assetid: 33942e4a-0a0a-49e8-a693-004954f6d38a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0349ecb12d60018b09271efe5b988cc44585dc4d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939672"
---
# <a name="idebugbreakpointrequest3getrequestinfo2"></a>IDebugBreakpointRequest3::GetRequestInfo2
이 메서드는이 중단점 요청을 설명 하는 중단점 요청 정보를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetRequestInfo2(  
   BPREQI_FIELDS      dwFields,  
   BP_REQUEST_INFO2*  bBPRequestInfo  
);  
```  
  
```csharp  
int GetRequestInfo2(  
   enum_BPREQI_FIELDS  dwFields,   
   BP_REQUEST_INFO2[]  bBPRequestInfo  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dwFields`  
 [in] 플래그의 조합 된 [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) 의 필드를 결정 하는 열거형 `pBPRequestInfo` 작성 해야 할 합니다.  
  
 `bBPRequestInfo`  
 [out] 합니다 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) 구조를 채울 수 있습니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 이 요청에서 반환 되는 보다 자세한 정보는 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) 메서드.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)