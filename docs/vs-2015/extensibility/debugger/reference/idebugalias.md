---
title: IDebugAlias | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugAlias
helpviewer_keywords:
- IDebugAlias interface
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6c05b6987804681176abdde0e8c94a7463a9163c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442312"
---
# <a name="idebugalias"></a>IDebugAlias
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 이러한 방식으로 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 정보를 참조 하세요 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 하 고 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)합니다.  
  
 변수에 대 한 숫자 별칭을 나타냅니다. 별칭은 변수에 다른 이름을 하기만 하면 됩니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugAlias : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 식 계산기 (EE) 변수에 대 한 숫자 별칭을 지원 하기 위해이 인터페이스를 구현 합니다.  
  
## <a name="notes-for-callers"></a>호출자에 대 한 정보  
 [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) 특정 개체에 대 한 별칭을 만듭니다. 별칭을 검색 하려면 사용 하 여 [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md) 하거나 [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 에 정의 된 다음 메서드는 `IDebugAlias` 인터페이스입니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|이 별칭이 참조 하는 개체를 가져옵니다.|  
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|별칭 이름을 가져옵니다.|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|검색을 `ICorDebugValue` 인터페이스에 대 한 액세스를 제공 하는 관리 되는이 개체 (관리 코드에만 해당)에 대 한 코드 정보.|  
|[Dispose](../../../extensibility/debugger/reference/idebugalias-dispose.md)|별칭으로 더 이상 사용 되지이 표시 됩니다.|  
  
## <a name="remarks"></a>설명  
 별칭은 문자열 형식의 예를 들어 1001 # # 문자를 뒤에 10 진수입니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: ee.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [식 계산 인터페이스](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)   
 [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)   
 [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)
