---
title: IDebugBinder3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBinder3
helpviewer_keywords:
- IDebugBinder3 interface
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3f23c2ad4aeaf911e45b28686584d741e5c4d22f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704131"
---
# <a name="idebugbinder3"></a>IDebugBinder3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 이러한 방식으로 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 정보를 참조 하세요 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 하 고 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)합니다.  
  
 이 인터페이스 형식, 별칭 및 사용자 지정 시각화 도우미 서비스에 액세스할 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugBinder3 : IDebugBinder  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 디버그 엔진 별칭, 사용자 지정 시각화 도우미 서비스 및 개체 형식 정보에 대 한 액세스를 지원 하기 위해이 인터페이스를 구현 합니다.  
  
## <a name="notes-for-callers"></a>호출자에 대 한 정보  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) 인터페이스를 사용 하 여이 인터페이스를 가져오는 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 제공한 메서드 외에도 합니다 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) 인터페이스에서이 인터페이스에서 다음을 구현 합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|이 개체가 연결 된 메모리를 나타내는 메모리 개체를 검색 합니다.|  
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|이 개체 (있는 경우)와 관련 된 예외를 검색 합니다.|  
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|지정 된 이름, 별칭을 검색 합니다.|  
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|이 개체에 대 한 모든 별칭의 배열을 검색합니다|  
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|이 개체와 연결 된 인수 형식의 수를 가져옵니다.|  
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|이 개체와 연결 된 인수 형식 목록을 검색 합니다.|  
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|시각화 도우미 서비스에 대 한 인터페이스를 가져옵니다.|  
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|메모리 컨텍스트에 개체 위치 또는 64 비트 메모리 주소를 변환합니다.|  
  
## <a name="requirements"></a>요구 사항  
 헤더: ee.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [식 계산 인터페이스](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
