---
title: IDebugReference2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugReference2
helpviewer_keywords:
- IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ac7e825bd33c184d580ada96843366f6d1627f22
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438964"
---
# <a name="idebugreference2"></a>IDebugReference2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 스택 프레임 속성 또는 다른 일부 속성에 대 한 참조를 나타냅니다.  
  
> [!NOTE]
> `IDebugReference2` 나중에 사용할 수 있도록 하 고 해당 메서드를 반환할지 모든 용으로 예약 되어 `E_NOTIMPL`입니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugReference2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 DE 특정 유형의 값에 대 한 참조를 나타내는 데이 인터페이스를 구현 합니다. 예를 들어, 값 식 계산, 메모리 또는 레지스터 및 해당 값의 목록을 표시 하는 데 메모리 컨텍스트 결과로 숫자 값을 수 있습니다.  
  
## <a name="notes-for-callers"></a>호출자에 대 한 정보  
 호출 [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) 이 인터페이스를 가져올 수 있습니다. [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) 하 고 [GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) 또한이 인터페이스를 반환 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서의 메서드를 보여 줍니다. `IDebugReference2`합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|가져옵니다 합니다 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 이 참조를 설명 하는 구조입니다.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|문자열에서이 참조의 값을 설정 합니다.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|다른 참조에서이 참조의 값을 설정 합니다.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|이 참조의 자식을 열거합니다.|  
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|이 참조의 부모를 가져옵니다.|  
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|이 참조의 가장 많이 파생 된 참조를 가져옵니다.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|이 참조가 메모리 바이트 수를 가져옵니다.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|이 참조에 대 한 메모리 컨텍스트를 가져옵니다.|  
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|이 참조를 바이트 단위로 크기를 가져옵니다.|  
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|이 참조 형식을 설정합니다.|  
|[Compare](../../../extensibility/debugger/reference/idebugreference2-compare.md)|다른이 참조를 비교합니다.|  
  
## <a name="remarks"></a>설명  
  
> [!NOTE]
> "Property"이이 사용 해야 혼동 하지 해당 클래스의 멤버 변수 의미 하지만 `IDebugReference2` 이러한 엔터티를 나타낼 수 있습니다.  
  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 속성을 나타내는 동안 `IDebugReference2` 속성을 일반적으로 디버깅 중인 프로그램의 개체에 대 한 참조에 대 한 참조를 나타냅니다.  
  
 속성 및 참조 간의 주요 차이점은 명명 되지 않은 인스턴스에 대 한 참조를 참조 하는 동안 개체의 명명된 된 인스턴스 속성 참조는 속성에서 프로그램의 힙에 있는 개체를 참조할 수 있습니다 예를 들어 `"a.b"`합니다. 다른 속성은 동일한 개체를 참조할 수 있습니다 `"c.d"`합니다. 에서는이 속성을 참조 하는 방법은 `"a.b"` 또는 `"c.d"` 범위 여야 합니다. 이 동일한 개체에 대 한 참조는 이름이 없습니다. 해당 개체에 대 한 메모리는 유효한 개체를 참조할 수 있습니다.  
  
 `IDebugProperty2` 인터페이스 이름, 형식 및 주소를 사용 하 여 값으로 생각할 수 있습니다. `IDebugReference2`다른, 전달, 형식 및 주소도 생각할 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)
