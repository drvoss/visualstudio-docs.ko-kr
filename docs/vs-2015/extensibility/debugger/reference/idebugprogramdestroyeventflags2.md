---
title: IDebugProgramDestroyEventFlags2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 86f7e211c742e4d95f3459d058139854874e7d85
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68182207"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

기본 동작을 재정의 하는 디버그 엔진을 사용 하도록 설정 된 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] UI 디버그 세션을 종료 하는 경우.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugProgramDestroyEventFlags2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 이 인터페이스는 디버그 엔진에서 구현 됩니다. 수 만들고 프로세스의 수명 동안 여러 프로그램을 삭제 하는 호스트에 두는 것이 유용 합니다.  
  
## <a name="methods"></a>메서드  
 다음 표에서의 메서드를 보여 줍니다. `IDebugProgramDestroyEventFlags2`합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|프로그램 검색 플래그를 삭제 합니다.|  
  
## <a name="remarks"></a>설명  
 기본 동작을 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] UI 모든 프로그램 프로그램 전송한 후 디자인 모드로 다시 이동 하는 이벤트를 삭제 합니다. 이 인터페이스에는 해당 동작을 변경 하는 디버그 엔진을 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: Msdbg.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll
