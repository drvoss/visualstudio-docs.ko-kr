---
title: IDebugProgram2::GetDisassemblyStream | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::GetDisassemblyStream
helpviewer_keywords:
- IDebugProgram2::GetDisassemblyStream
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e8d2220d928128b02ea02d26f8273714a89171ea
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49896460"
---
# <a name="idebugprogram2getdisassemblystream"></a>IDebugProgram2::GetDisassemblyStream
이 프로그램 또는이 프로그램의 일부에 대 한 디스어셈블리 스트림을 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetDisassemblyStream(   
   DISASSEMBLY_STREAM_SCOPE   dwScope,  
   IDebugCodeContext2*        pCodeContext,  
   IDebugDisassemblyStream2** ppDisassemblyStream  
);  
```  
  
```csharp  
int GetDisassemblyStream(   
   enum_DISASSEMBLY_STREAM_SCOPE  dwScope,  
   IDebugCodeContext2             pCodeContext,  
   out IDebugDisassemblyStream2   ppDisassemblyStream  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dwScope`  
 [in] 값을 지정 합니다 [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) 디스어셈블리 스트림의 범위를 정의 하는 열거형입니다.  
  
 `pCodeContext`  
 [in] [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 디스어셈블리 stream을 시작할 위치를 위치를 나타내는 개체입니다.  
  
 `ppDisassemblyStream`  
 [out] 반환 된 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) 디스어셈블리 스트림을 나타내는 개체입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다. 반환 `E_DISASM_NOTSUPPORTED` 이 특정 아키텍처에 대 한 디스어셈블리를 지원 하지 않는 경우.  
  
## <a name="remarks"></a>설명  
 경우는 `dwScopes` 매개 변수를 `DSS_HUGE` 의 플래그를 [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) 열거형 설정한 디스어셈블리 전체 파일에 대 한 많은 수의 디스어셈블리 지침, 예를 들어, 반환 될 또는 모듈을 추가 합니다. 경우는 `DSS_HUGE` 플래그를 설정 하지 않으면 다음 디스어셈블리 작은 지역으로 제한 해야 하는 단일 함수는 일반적으로 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)