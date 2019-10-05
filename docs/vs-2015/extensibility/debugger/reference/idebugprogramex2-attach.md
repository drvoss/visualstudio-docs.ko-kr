---
title: IDebugProgramEx2::Attach | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4fe729f2fc196380a3db1a60d1c32f62bbd70998
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439165"
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

프로그램에 세션을 연결 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason,  
   IDebugSession2*       pSession  
);  
```  
  
```  
[C#]  
int Attach(   
   IDebugEventCallback2 pCallback,  
   uint                 dwReason,  
   IDebugSession2       pSession  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pCallback`  
 [in] [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 연결 된 디버그 엔진 이벤트를 전송 하는 콜백 함수를 나타내는 개체입니다.  
  
 `dwReason`  
 [in] 값을 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) 연결 작업에 대 한 이유를 설명 하는 열거형입니다.  
  
 `pSession`  
 [in] 프로그램에 연결 된 세션을 고유 하 게 식별 하는 값입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`; 그렇지 않으면 오류 코드를 반환 합니다. 이 메서드에서 반환 해야 `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` 프로그램 이미 연결 된 경우.  
  
## <a name="remarks"></a>설명  
 프로그램을 포함 하는 포트에 값을 사용할 수 `pSession` 세션 프로그램에 연결 하려고 합니다. 확인 하려면. 예를 들어, 포트를 프로세스에 연결 하는 한 번에 하나만 디버그 세션을 허용 하는 경우 포트 동일한 세션 프로세스에서 다른 프로그램에 이미 연결 되어 있는지 확인할 수 있습니다.  
  
> [!NOTE]
> 인터페이스에 전달 된 `pSession` 쿠키를 고유 하 게이 프로그램에 연결 하 여 세션 디버그 관리자를 식별 하는 값으로 서만 처리할지 제공 된 인터페이스의 메서드는 작동 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
