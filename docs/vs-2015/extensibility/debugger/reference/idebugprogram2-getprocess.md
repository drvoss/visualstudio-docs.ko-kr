---
title: IDebugProgram2::GetProcess | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 366b35a90eb44496dc1b50cd85dfa0fef5656ddb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68148662"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 프로그램에서 실행 중인 프로세스를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetProcess(  
   IDebugProcess2** ppProcess  
);  
```  
  
```csharp  
int GetProcess(  
   out IDebugProcess2 ppProcess  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ppProcess`  
 [out] 반환 된 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 프로세스를 나타내는 인터페이스입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 디버그 엔진 (DE) 구현 하지 않는 한 합니다 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) 인터페이스는 DE이이 메서드 구현은 항상 반환 `E_NOTIMPL` 는 DE 수 없습니다. 따라서와 실행 중인 프로세스를 확인할 수 없으므로 이 메서드의 구현을 충족 합니다.  
  
 구현 합니다 `IDebugEngineLaunch2` 인터페이스는 DE 프로세스를 만드는 방법을 알고 있어야 한다는 의미 따라서는 DE 구현의 합니다 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 인터페이스는 프로세스에서 실행 중인 것을 알 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
