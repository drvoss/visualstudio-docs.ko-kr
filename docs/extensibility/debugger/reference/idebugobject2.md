---
title: IDebugObject2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject2
helpviewer_keywords:
- IDebugObject2 interface
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d5e60c9e084872b08ec8d38b784b47969af2d52e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31118923"
---
# <a name="idebugobject2"></a>IDebugObject2
> [!IMPORTANT]
>  Visual Studio 2015에서 구현 하는 식 계산기의 이러한 방식으로 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 정보를 참조 하십시오 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)합니다.  
  
 이 인터페이스는 개체에 대 한 추가 정보를 제공 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugObject2 : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 식 계산기는 별칭 및 개체에 대 한 정보에 액세스 하기 위한 지원을 제공 하기 위해이 인터페이스를 구현 합니다.  
  
## <a name="notes-for-callers"></a>호출자에 대 한 참고 사항  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 인터페이스를 사용 하 여이 인터페이스를 가져올 수 [QueryInterface](/cpp/atl/queryinterface)합니다. 또한 [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md) 이 인터페이스를 반환 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 메서드 외에도 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 인터페이스를는 `IDebugObject2` 다음 인터페이스를 구현 합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|필드 또는 변수를 가져옵니다 (있는 경우)는이 개체에 의해 표현 되는 속성 백업 될 수 있습니다.|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|이 개체의 값을 나타내는 관리 코드 개체를 가져옵니다.|  
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|이 개체에 대 한 고유 ID를 만들거나 기존 별칭을 반환 합니다.|  
|[GetAlias](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|있는 경우이 개체와 연결 된 별칭을 가져옵니다.|  
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|이 개체의 형식을 가져옵니다.|  
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|이 개체가 사용자 데이터를 나타내는지 여부를 결정 합니다.|  
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|편집 하며 계속 하기 상태 유효 더 이상 인지 확인 합니다.<br /><br /> 사용자 지정 식 계산기는이 메서드를 구현 하지 않습니다 (항상 반환 해야 `E_NOTIMPL`).|  
  
## <a name="remarks"></a>설명  
 참조 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) 별칭에 대 한 내용은 합니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [식 평가 인터페이스](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)   
 [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)