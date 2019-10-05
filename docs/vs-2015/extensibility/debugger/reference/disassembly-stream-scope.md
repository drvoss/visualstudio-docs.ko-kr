---
title: DISASSEMBLY_STREAM_SCOPE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords:
- DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0132aad5ad6e37e7bb811693afde7ebfe80b272d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68198838"
---
# <a name="disassemblystreamscope"></a>DISASSEMBLY_STREAM_SCOPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

디스어셈블리 stream의 범위를 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
typedef DWORD DISASSEMBLY_STREAM_SCOPE;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
```  
  
## <a name="members"></a>멤버  
 DSS_HUGE  
 코드 컨텍스트를 디스어셈블는 클라이언트를 한 번의 호출을 검색 하려면 일반적으로 보다 자세한 출력을 생성 하도록 지정 합니다.  
  
 DSS_FUNCTION  
 코드 컨텍스트에 포함 된 함수를 디스어셈블 해야를 지정 합니다. 반환 하는 경우 디스어셈블리 스트림에 함수를 나타내도록 지정 합니다는 [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) 메서드.  
  
 DSS_MODULE  
 반환 하는 `IDebugDisassemblyStream2::GetScope` 디스어셈블리 스트림을 모듈을 나타내는 메서드를 지정 합니다.  
  
 DSS_ALL  
 전체 주소 공간에 대 한 디스어셈블리를 지정합니다.  
  
## <a name="remarks"></a>설명  
 인수로 전달 합니다 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) 메서드 반환한를 [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) 메서드.  
  
 이러한 값을 비트 결합할 수 있습니다 `OR`합니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)
