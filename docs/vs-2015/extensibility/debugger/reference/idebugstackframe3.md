---
title: IDebugStackFrame3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d63d4dcd6e3b7a3b81504b485ee710779cef3c13
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65688531"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스를 확장 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) 가로챈된 예외를 처리 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugStackFrame3 : IDebugStackFrame2  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 디버그 엔진 (DE)를 구현 하는 동일한 개체에서이 인터페이스를 구현 합니다 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) 인터페이스를 가로챈된 예외를 지원 합니다.  
  
## <a name="notes-for-callers"></a>호출자에 대 한 정보  
 호출 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) 에 `IDebugStackFrame2` 인터페이스가이 인터페이스를 가져올 수 있습니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 상속 된 메서드 외에도 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md), `IDebugStackFrame3` 다음 메서드를 노출 합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|일반 예외 처리 하기 전에 현재 스택 프레임에 대 한 예외를 처리합니다.|  
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|스택 해제 발생 한다면 코드 컨텍스트를 반환 합니다.|  
  
## <a name="remarks"></a>설명  
 가로챈된 예외는 모든 일반 예외 처리 루틴 실행된 시간을 기준으로 호출 되기 전에 디버거가 예외를 처리할 수 있습니다 의미 합니다. 기본적으로 예외가 가로채 없는 경우에 있는 예외 처리기는 노테이션 런타임 만들기 의미 합니다.  
  
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) 모든 일반 예외 콜백 이벤트 동안 호출 됩니다 (이 유일한 예외는 디버깅 하는 경우 혼합 모드 코드 (관리 및 비관리 코드) 하는 동안 예외를 가로챌 수 없는 경우는 마지막 기회 콜백)입니다. DE 구현 하지 않는 경우 `IDebugStackFrame3`에 DE IDebugStackFrame3에서 오류를 반환 합니다. 또는::`InterceptCurrentException` (같은 `E_NOTIMPL`), 디버거 일반적으로 예외를 처리 한 다음.  
  
 예외를 가로채에서 디버거가 디버그 중인 프로그램의 상태를 변경 하 고 예외가 throw 된 지점에서 실행을 다시 시작 사용자를 수 있습니다.  
  
> [!NOTE]
> 가로챈된 예외는 아래에서 언어 런타임 (CLR (공용)를 실행 하는 프로그램에서, 관리 코드 에서만에서 허용 됩니다.  
  
 디버그 엔진을 지원함을 나타냅니다이 가로채 예외 "metricExceptions"를 설정 하 여 1의 값으로 런타임 시 사용 하 여는 `SetMetric` 함수입니다. 자세한 내용은 [디버깅을 위한 SDK 도우미](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)합니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [디버깅을 위한 SDK 도우미](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
