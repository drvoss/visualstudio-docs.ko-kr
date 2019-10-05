---
title: IDebugProgramProvider2::GetProviderProgramNode | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5fa9f4db6aa71e9bba1f456b13ba52abd24ab966
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68198723"
---
# <a name="idebugprogramprovider2getproviderprogramnode"></a>IDebugProgramProvider2::GetProviderProgramNode
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

특정 프로그램에 대 한 프로그램 노드를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetProviderProgramNode(  
   PROVIDER_FLAGS       Flags,  
   IDebugDefaultPort2*  pPort,  
   AD_PROCESS_ID        processId,  
   REFGUID              guidEngine,  
   UINT64               programId,  
   IDebugProgramNode2** ppProgramNode  
);  
```  
  
```csharp  
int GetProviderProgramNode(  
   enum_PROVIDER_FLAGS    Flags,  
   IDebugDefaultPort2     pPort,  
   AD_PROCESS_ID          ProcessId,  
   ref Guid               guidEngine,  
   ulong                  programId,  
   out IDebugProgramNode2 ppProgramNode  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `Flags`  
 [in] 플래그의 조합 된 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) 열거형입니다. 이 호출에 대 한 일반 플래그는 다음과 같습니다.  
  
|Flag|Description|  
|----------|-----------------|  
|`PFLAG_REMOTE_PORT`|호출자에 게 원격 컴퓨터에서 실행 됩니다.|  
|`PFLAG_DEBUGGEE`|호출자에 게 현재 디버깅 중인 (마샬링 하는 방법에 대 한 자세한 내용은 각 노드에 대해 반환 됩니다).|  
|`PFLAG_ATTACHED_TO_DEBUGGEE`|호출자에 연결 되었지만 디버거에서 실행 되지 않습니다.|  
  
 `pPort`  
 [in] 포트는 호출 프로세스에서 실행 됩니다.  
  
 `processId`  
 [in] [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) 구조에서 해당 프로그램을 포함 하는 프로세스의 ID를 보유 합니다.  
  
 `guidEngine`  
 [in] GUID (해당 되는 경우) 프로그램에 연결 된 디버그 엔진입니다.  
  
 `programId`  
 [in] 프로그램 노드를 프로그램의 ID입니다.  
  
 `ppProgramNode`  
 [out] [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 요청 된 프로그램이 노드를 나타내는 개체입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
