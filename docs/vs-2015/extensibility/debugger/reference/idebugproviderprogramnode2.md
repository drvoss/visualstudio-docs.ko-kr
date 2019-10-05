---
title: IDebugProviderProgramNode2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2
helpviewer_keywords:
- IDebugProviderProgramNode2
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a81668d5c45dd4b3363821972914e3f9dc10266a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65692209"
---
# <a name="idebugproviderprogramnode2"></a>IDebugProviderProgramNode2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스를 프로세스 경계를 넘어 프로그램 관련 인터페이스를 마샬링합니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugProviderProgramNode2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 디버그 엔진 (DE)를 구현 하는 동일한 개체에서이 인터페이스를 구현 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 프로세스 경계를 넘어 마샬링 인터페이스를 지원 하도록 합니다.  
  
## <a name="notes-for-callers"></a>호출자에 대 한 정보  
 호출 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) 에 `IDebugProgramNode2` 인터페이스가이 인터페이스를 가져올 수 있습니다. 이 인터페이스를 가져올 수 없는 경우는 DE 인터페이스의 마샬링을 지원 하지 않습니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 이 인터페이스는 다음 메서드를 구현합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|프로세스 경계를 넘어 지정된 된 인터페이스를 가져옵니다.|  
  
## <a name="remarks"></a>설명  
 디버그 중인 프로그램에서 별도 프로세스 공간에서 실행 되는 DE 하는 경우이 인터페이스는 구현:는 DE 디버깅 중인 프로그램의 프로세스 공간 대신 Visual Studio 프로세스 공간에서 실행 중인 경우에 예를 들어 있습니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
