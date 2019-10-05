---
title: IDebugProgramEx2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2d3abc956d736f5c9273134b41c0fc9c2dc7db62
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65688936"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 세션을 디버그 관리자 (SDM) 프로그램에 연결 및 프로그램과 연결 된 프로그램 노드를 가져올 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugProgramEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 동일한 개체에서이 인터페이스를 구현 하는 사용자 지정 포트 공급자는 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) SDM 동시에 연결 포트 공급자 모든 세션을 추적할 수 있도록 하는 동안 프로그램에 연결 하기 위해 인터페이스는 프로그램입니다. 사용자 지정 포트 공급자 선택 하는 경우이 인터페이스를 구현할 수 있습니다.  
  
## <a name="notes-for-callers"></a>호출자에 대 한 정보  
 SDM 호출 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) 에 `IDebugProgram2` 프로그램에 연결 하는 세션을 추적 하려면이 인터페이스를 얻기 위해 인터페이스입니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서의 메서드를 보여 줍니다. `IDebugProgramEx2`합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|세션에는 프로그램을 연결합니다.|  
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|프로그램과 연결 된 프로그램 노드를 가져옵니다.|  
  
## <a name="remarks"></a>설명  
 이 인터페이스는 SDM와 프로그램 간의 비공개입니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: Portpriv.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
