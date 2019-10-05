---
title: IDebugPortNotify2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 18edddd698953bf71febb8f9f2f1bac704205120
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703930"
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 등록 또는 실행 중인 포트를 사용 하 여 디버깅할 수 있는 프로그램의 등록을 취소 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugPortNotify2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 사용자 지정 포트 공급자에서에서 추가 및 제거 프로그램 포트를 지원 하기 위해이 인터페이스를 구현 합니다. 일반적으로 구현 하는 동일한 개체에서 구현 되는 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 인터페이스입니다.  
  
## <a name="notes-for-callers"></a>호출자에 대 한 정보  
 에 대 한 호출 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) 에 `IDebugPort2` 인터페이스는이 인터페이스를 반환 합니다. 또한 호출 [GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) 이 인터페이스를 반환 합니다. 디버그 엔진을 매개 변수로이 인터페이스를 볼 수 [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서의 메서드를 보여 줍니다. `IDebugPortNotify2`합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|실행 되는 포트를 사용 하 여 디버깅할 수 있는 프로그램을 등록 합니다.|  
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|실행 되 고 포트에서 디버깅할 수 있는 프로그램을 등록 취소 합니다.|  
  
## <a name="remarks"></a>설명  
 디버그 포트에 프로그램이 로드 되거나 언로드될 때를 알 수 있게 하지 않는 한 사용자 지정 포트 공급자는이 인터페이스를 구현 해야 합니다. 특정 포트를 통해 디버깅을 위해 로드 되는 모든 프로그램은이 인터페이스를 사용 하 여 추적 됩니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
