---
title: IDebugDocument2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocument2
helpviewer_keywords:
- IDebugDocument2 interface
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2cd6afb417de4d8a362916f91593d0d0e67d307c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68156505"
---
# <a name="idebugdocument2"></a>IDebugDocument2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 원본 문서를 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugDocument2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 일반적으로이 인터페이스를 구현합니다. 디버그 엔진 (DE) 소스 코드를 제공 해야 하 고 원본 디스크에 없는 경우이 인터페이스를 구현할 수도 있습니다.  이러한 경우에는 DE도 구현 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 하 고 [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) 인터페이스 뿐만 아니라 일부 추가 메서드는 [ IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) 하 고 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) 인터페이스입니다.  
  
## <a name="notes-for-callers"></a>호출자에 대 한 정보  
 메서드는 `IDebugDocumentContext2`, `IDebugDisassemblyStream2`를 `IDebugDocumentPosition2`, 및 `IDebugActivateDocumentEvent2` 인터페이스는이 인터페이스를 반환 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서의 메서드를 보여 줍니다. `IDebugDocument2`합니다.  
  
|메서드|Description|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|여러 형식 중 하나로 문서의 이름을 가져옵니다.|  
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|문서 클래스 식별자를 가져옵니다.|  
  
## <a name="remarks"></a>설명  
 이 인터페이스는 DE 소스 코드를 제공 하는 경우에 구현 됩니다. 예를 들어, HTML 페이지에 스크립트를 디버깅 하는 경우는 DE 제공 소스 코드는 소스를 다운로드 하거나 동적으로 생성 하므로 한 디스크 파일로 존재 하지 않습니다. 와 같은 일반적인 언어에서 디버깅 하는 경우 C++에서이 인터페이스를 구현할 필요가 없습니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)
