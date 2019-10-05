---
title: IDebugExceptionEvent2::PassToDebuggee | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ecc7eb3830522cdee0022f4193482daab3780230
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68150403"
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

예외를 삭제 해야 하는 경우 또는 예외 실행을 다시 시작할 때 디버깅 중인 프로그램에 전달 되어야 합니다 있는지 여부를 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT PassToDebuggee(  
   BOOL fPass  
);  
```  
  
```csharp  
int PassToDebuggee(  
   int fPass  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `fPass`  
 [in] 0이 아닌 값 (`TRUE`) 예외 0 또는 실행을 다시 시작할 때 디버깅 중인 프로그램에 전달 되어야 하는 경우 (`FALSE`) 예외를 삭제 해야 하는 경우.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 이 메서드를 호출 해도 디버깅 중인 프로그램에서 실행 하는 코드를 실제로 발생 하지 않습니다. 호출은 다음 코드 실행에 대 한 상태를 설정할 뿐입니다. 예를 들어, 호출을 [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) 메서드를 반환할 수 있습니다 `S_OK` 사용 하 여를 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md).`dwState` 필드 설정 `EXCEPTION_STOP_SECOND_CHANCE`합니다.  
  
 IDE 나타날 수는 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) 이벤트 및 호출 합니다 [계속](../../../extensibility/debugger/reference/idebugprogram2-continue.md) 메서드. 디버그 엔진 (DE) 경우를 처리 하는 기본 동작이 있어야 합니다.는 `PassToDebuggee` 메서드가 호출 되지 않습니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)   
 [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)
