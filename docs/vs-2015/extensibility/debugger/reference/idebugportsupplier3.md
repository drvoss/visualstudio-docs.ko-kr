---
title: IDebugPortSupplier3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e4ece720cf6880bba528dee99cdbdeb25c10087a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65674125"
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 호출자가 포트 공급자 (디스크에 쓴 후)에서 디버거는 호출 간에 포트를 유지 하 고 다음 유지 해당 포트의 목록을 받을 수 있는지 여부를 확인할 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugPortSupplier3 : IDebugPortSupplier2  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 사용자 지정 포트 공급자 유지 또는 디스크에 포트 정보를 저장을 지원 하기 위해이 인터페이스를 구현 합니다. 동일한 개체에서이 인터페이스를 구현 해야 합니다 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) 인터페이스입니다.  
  
## <a name="notes-for-callers"></a>호출자에 대 한 정보  
 호출 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) 에 `IDebugPortSupplier2` 인터페이스가이 인터페이스를 가져올 수 있습니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 상속 된 메서드 외에 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) 인터페이스,이 인터페이스에서 다음을 지원 합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|지속할 지 여부를 포트 공급자 수 포트 (디스크에 쓴 후)에서 디버거는 호출 간에 반환 합니다.|  
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|이 포트 공급자에서 디스크에 기록 된 모든 포트를 통해 열거를 사용할 수 있는 개체를 반환 합니다.|  
  
## <a name="remarks"></a>설명  
 포트 공급자 호출에서 포트를 유지할 수 있습니다, 경우에이 인터페이스를 구현 해야 합니다. 포트 공급자가 인스턴스화되고 포트 공급자 소멸 될 때 디스크에 쓸 때 포트를 로드 해야 합니다.  
  
 디버그 엔진을 일반적으로 포트 공급자 상호 작용 하지 않습니다 있으며,이 인터페이스 사용 되지 않습니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
