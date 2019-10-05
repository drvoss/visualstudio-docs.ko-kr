---
title: IDebugDocumentTextEvents2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b574ae45dafed11ed28047859676524054951512
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65678963"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 Visual Studio 디버그 엔진에 의해 제공 되는 소스 문서의 변경 내용을 알릴 사용 됩니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugDocumentTextEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 DE 소스 코드를 변경 하도록 지원 하기 위해이 인터페이스를 구현 합니다. 이 인터페이스를 구현 하는 동일한 개체에서 일반적으로 구현 됩니다 합니다 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) 인터페이스입니다.  
  
## <a name="notes-for-callers"></a>호출자에 대 한 정보  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 호출을 통해이 인터페이스를 가져옵니다는 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> 메서드. 합니다 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> 인터페이스에 대 한 호출에서 가져온는 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> 메서드. <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> 인터페이스를 호출 하 여 가져온 합니다 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) 메서드를 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) 인터페이스.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서의 메서드를 보여 줍니다. `IDebugDocumentTextEvents2`합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|소멸 된 전체 문서를 나타냅니다.|  
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|텍스트 문서에 삽입 되었음을 디버그 패키지에 알립니다.|  
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|텍스트 문서에서 제거 되었습니다 디버그 패키지에 알립니다.|  
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|문서에서 텍스트를 교체한 디버그 패키지에 알립니다.|  
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|문서에서 텍스트 특성 업데이트 되었습니다는 디버그 패키지에 알립니다.|  
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|문서 속성을 업데이트 된 이벤트의 수신기에 알립니다.|  
  
## <a name="remarks"></a>설명  
 해당 문서를 제공 하는 디버그 엔진은 활용 하기 위해 전용 된 `IDebugDocumentTextEvent2` 인터페이스. 이 예제는 스크립팅 디버그 엔진을 것입니다. 스크립트 해석 하는 동안 새 소스 코드 생성할 수 있습니다 디스크 파일에 없는 하는 DE에만 알려집니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
