---
title: IDebugDisassemblyStream2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2
helpviewer_keywords:
- IDebugDisassemblyStream2 interface
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5b5126758c60262564390f84b6278300a41660f5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68187181"
---
# <a name="idebugdisassemblystream2"></a>IDebugDisassemblyStream2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 명령의 스트림을 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugDisassemblyStream2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 디버그 엔진을 프로그램의 코드는 디스어셈블리를 지원 하기 위해이 인터페이스를 구현 합니다.  
  
## <a name="notes-for-callers"></a>호출자에 대 한 정보  
 에 대 한 호출을 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) 메서드는이 인터페이스를 반환 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서의 메서드를 보여 줍니다. `IDebugDisassemblyStream2`합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[읽기](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|디스어셈블리 스트림 내의 현재 위치에서 시작 하는 지침을 읽습니다.|  
|[Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|디스어셈블리 스트림에 지정된 된 수의 지정 된 위치를 기준으로 지침 읽기 포인터를 이동합니다.|  
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|특정 코드 컨텍스트에 대 한 코드 위치 식별자를 반환합니다.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|지정 된 코드 위치 id에 해당 하는 코드 컨텍스트 개체를 반환 합니다.|  
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|현재 코드 위치를 나타내는 코드 위치 식별자를 반환 합니다.|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|이 디스어셈블리 스트림과 연결 된 원본 문서를 가져옵니다.|  
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|이 디스어셈블리 스트림의 범위를 가져옵니다.|  
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|이 디스어셈블리 스트림의 크기를 가져옵니다.|  
  
## <a name="remarks"></a>설명  
 디스어셈블리 스트림은 나타내는 전체 주소 공간 또는 방금 함수나 모듈의 공간 내에서 만들 수 있습니다. 각 명령으로 표시 됩니다는 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) 구조에 대 한 호출에서 반환 되는 [읽기](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) 메서드.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
