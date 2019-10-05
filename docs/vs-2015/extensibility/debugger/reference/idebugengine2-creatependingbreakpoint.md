---
title: IDebugEngine2::CreatePendingBreakpoint | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords:
- IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 84c36d08c7ad907006eb9f41d2f6e2c9cd77e7bf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196040"
---
# <a name="idebugengine2creatependingbreakpoint"></a>IDebugEngine2::CreatePendingBreakpoint
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

디버그 엔진 (DE)에서 보류 중인 중단점을 만듭니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT CreatePendingBreakpoint(   
   IDebugBreakpointRequest2*  pBPRequest,  
   IDebugPendingBreakpoint2** ppPendingBP  
);  
```  
  
```csharp  
int CreatePendingBreakpoint(   
   IDebugBreakpointRequest2     pBPRequest,  
   out IDebugPendingBreakpoint2 ppPendingBP  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pBPRequest`  
 [in] [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) 만들려면 보류 중인 중단점을 설명 하는 개체입니다.  
  
 `ppPendingBP`  
 [out] 반환 된 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) 보류 중인 중단점을 나타내는 개체입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다. 일반적으로 반환 합니다 `E_FAIL` 경우는 `pBPRequest` 매개 변수는 DE 경우를 지 원하는 모든 언어에 맞지 않습니다를 `pBPRequest` 매개 변수가 잘못 되었거나 완전 하지 않습니다.  
  
## <a name="remarks"></a>설명  
 보류 중인 중단점은 기본적으로 코드에 중단점을 바인딩할 때 필요한 모든 정보 컬렉션입니다. 이 메서드에서 반환 된 보류 중인 중단점까지 코드에 바인딩되지 않은 합니다 [바인딩할](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) 메서드가 호출 됩니다.  
  
 중단점 보류 중인 각 사용자 집합을 세션 디버그 관리자 (SDM)이 메서드를 호출이 연결 된 각 DE에서. 해당 장치에서 실행 중인 프로그램이 중단점 올바른지 확인 하는 DE 책임 이라는 것입니다.  
  
 사용자 코드 줄에 중단점 설정 하는 경우는 DE는이 코드에 해당 하는 문서에 가장 가까운 줄에 중단점을 바인딩할 수 있습니다. 사용자가 여러 줄 문의 첫 번째 줄에 중단점을 설정 하지만 마지막 줄 (여기서 모든 코드 인 디버그 정보에서)에 바인딩할 수 있습니다.  
  
## <a name="example"></a>예제  
 다음 예제에서는 간단한에 대 한이 메서드를 구현 하는 방법을 보여 줍니다 `CProgram` 개체입니다. DE 구현의 `IDebugEngine2::CreatePendingBreakpoint` 각 프로그램에서 메서드의이 구현에 대 한 모든 호출을 다음으로 전달할 수 있습니다.  
  
```  
HRESULT CProgram::CreatePendingBreakpoint(IDebugBreakpointRequest2* pBPRequest, IDebugPendingBreakpoint2** ppPendingBP)     
{    
  
   // Create and initialize the CPendingBreakpoint object.  
   CComObject<CPendingBreakpoint> *pPending;    
   CComObject<CPendingBreakpoint>::CreateInstance(&pPending);    
   pPending->Initialize(pBPRequest, m_pInterp, m_pCallback, m_pEngine);    
   return pPending->QueryInterface(ppPendingBP);    
}    
```  
  
## <a name="see-also"></a>참고 항목  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)   
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
