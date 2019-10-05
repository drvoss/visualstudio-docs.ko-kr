---
title: IDebugMemoryBytes2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2
helpviewer_keywords:
- IDebugMemoryBytes2 interface
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1e23588e8da41b981f372210def65fa34a7e55bf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68180545"
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 메모리의 바이트를 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugMemoryBytes2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 디버그 엔진 (DE) 메모리의 바이트를 나타내는 데이 인터페이스를 구현 합니다.  
  
## <a name="notes-for-callers"></a>호출자에 대 한 정보  
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) 시스템 메모리에 대 한 액세스를 제공 하려면이 인터페이스를 반환 합니다. [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) 하 고 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md) 개체의 바이트에 대 한 액세스를 제공 하려면이 인터페이스를 반환 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서의 메서드를 보여 줍니다. `IDebugMemoryBytes2`합니다.  
  
|메서드|Description|  
|------------|-----------------|  
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|지정된 된 위치에서 시작 하는 바이트 시퀀스를 읽습니다.|  
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|씁니다 `dwCount` 부터 바이트 `pStartContext`합니다.|  
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|이 인터페이스를 나타내는 메모리의 바이트에서 크기를 가져옵니다.|  
  
## <a name="remarks"></a>설명  
 속성에는 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 배열을 나타내는 인터페이스를 제공는 `IDebugMemoryBytes2` 해당 배열에 값에 액세스 하는 인터페이스입니다.  
  
 Visual Studio **메모리 보기** 호출 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) 검색 하는 `IDebugMemoryBytes2` 시스템 메모리에 액세스 하기 위한 인터페이스입니다. 주소에 액세스할 수를 가져온 메모리 뷰로 주소로 입력 식 구문 분석을 사용 하 여 구문 분석 된 식을 평가한 후 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 가져오려고는 `IDebugProperty2` 인터페이스입니다. 에 대 한 호출 [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) 를 반환 합니다 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 메모리 주소를 설명 하는 합니다. 이 메모리 컨텍스트에 전달 되어 [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) 하 고 [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)합니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
