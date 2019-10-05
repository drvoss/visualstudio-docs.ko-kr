---
title: IDebugProgram2::Terminate | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4673259e4a8ca0d4354037efbc35b63bedfcbc96
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68146340"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

프로그램을 종료합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT Terminate(   
   void   
);  
```  
  
```csharp  
int Terminate();  
```  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 가능한 경우 프로그램이 종료 되며; 프로세스에서 언로드 그렇지 않은 경우 디버그 엔진 (DE)는 필요한 정리를 수행 합니다.  
  
 이 메서드 또는 [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) 모든 디버깅을 중지 하는 사용자에 대 한 응답에서 일반적으로 IDE에서 호출 됩니다. 이 메서드의 구현은 프로세스 내에서 프로그램을 종료 이상적으로 해야 합니다. 없는 경우는 DE 해야 프로그램에서이 프로세스에서 더 이상 실행 되지 않도록 (및 필요한 정리 작업을 수행). 경우는 `IDebugProcess2::Terminate` IDE에서 메서드를 호출한, 전체 프로세스가 완료 된 후 종료 됩니다는 `IDebugProgram2::Terminate` 메서드가 호출 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)
