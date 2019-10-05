---
title: IDebugObject2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject2
helpviewer_keywords:
- IDebugObject2 interface
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 979ede5601f1f31ca972bb9067b626954b1296f7
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65695203"
---
# <a name="idebugobject2"></a>IDebugObject2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 이러한 방식으로 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 정보를 참조 하세요 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 하 고 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)합니다.  
  
 이 인터페이스는 개체에 대 한 추가 정보를 제공 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugObject2 : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 식 계산기는 별칭 및 개체에 대 한 정보에 대 한 액세스에 대 한 지원을 제공 하기 위해이 인터페이스를 구현 합니다.  
  
## <a name="notes-for-callers"></a>호출자에 대 한 정보  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 인터페이스를 사용 하 여이 인터페이스를 가져올 수 있습니다 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)합니다. 또한 [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md) 이 인터페이스를 반환 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 메서드 외에도 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 인터페이스를 `IDebugObject2` 인터페이스에서 다음을 구현 합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|필드 또는 변수 (있는 경우)을 가져옵니다는이 개체가 나타내는 속성을 지 원하는 될 수 있습니다.|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|이 개체의 값을 나타내는 관리 코드 개체를 가져옵니다.|  
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|이 개체에 대 한 고유 ID를 만들거나 기존 별칭을 반환 합니다.|  
|[GetAlias](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|있는 경우이 개체와 연결 된 별칭을 가져옵니다.|  
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|이 개체의 형식을 가져옵니다.|  
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|이 개체가 사용자 데이터를 나타내는지 여부를 결정 합니다.|  
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|편집 하며 계속 하기 상태 유효한 이상 인지 확인 합니다.<br /><br /> 사용자 지정 식 계산기는이 메서드를 구현 하지 않습니다 (항상 반환할 `E_NOTIMPL`).|  
  
## <a name="remarks"></a>설명  
 참조 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) 별칭에 대 한 논의 합니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: ee.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [식 계산 인터페이스](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)   
 [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)
