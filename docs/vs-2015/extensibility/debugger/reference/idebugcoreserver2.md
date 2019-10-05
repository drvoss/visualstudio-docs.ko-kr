---
title: IDebugCoreServer2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer2
helpviewer_keywords:
- IDebugCoreServer2 interface
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c0bca6ccd3738518df339084b0f6463be181e52d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68192909"
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 표시 하 고 네트워크의 컴퓨터에서 서버에서 정보를 얻을 사용 됩니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugCoreServer2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 Visual Studio는 서버를 나타내는 데이 인터페이스를 구현 합니다. Visual Studio의 각 인스턴스는이 인터페이스의 인스턴스를 만듭니다.  
  
## <a name="notes-for-callers"></a>호출자에 대 한 정보  
 사용자 지정 포트 공급자에 대 한 호출에서이 인터페이스를 받는 [이벤트](../../../extensibility/debugger/reference/idebugportevents2-event.md)합니다.  
  
 디버그 엔진에 대 한 호출을 통해 간접적으로이 인터페이스를 가져올 수 있습니다 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) (반환 하는 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)에서 파생 된 인터페이스로 `IDebugCoreServer2`).  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서의 메서드를 보여 줍니다. `IDebugCoreServer2`합니다.  
  
|메서드|Description|  
|------------|-----------------|  
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|이름 및 컴퓨터의 특성을 가져옵니다.|  
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|컴퓨터의 이름을 가져옵니다.|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|컴퓨터에 존재 하는 포트 공급자를 가져옵니다.|  
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|컴퓨터에 이미 존재 하는 포트를 가져옵니다.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|컴퓨터에서 모든 포트에 대 한 열거자를 만듭니다.|  
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|컴퓨터에서 모든 포트 공급자에 대 한 열거자를 만듭니다.|  
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|컴퓨터의 컴퓨터 유틸리티를 가져옵니다.|  
  
## <a name="remarks"></a>설명  
 이 인터페이스를 네트워크의 컴퓨터에서 실행 중인 프로세스를 찾아보기도 Visual Studio에서 사용 됩니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [이벤트](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
