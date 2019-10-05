---
title: IJsDebugDataTarget 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a9b784d6-958f-4d55-b3f6-c2d6b260a16b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3cbb4b0b54fb9a3821d3033ef0e65fd0bafbc246
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62582500"
---
# <a name="ijsdebugdatatarget-interface"></a>IJsDebugDataTarget 인터페이스
액세스 대상 디버거 프로세스의 상태를 변경 하는 기능을 제공 하도록 디버거에 의해 구현 됩니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
IJsDebugDataTarget : public IUnknown;  
```  
  
## <a name="members"></a>멤버  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[IJsDebugDataTarget::AllocateVirtualMemory 메서드](../../winscript/reference/ijsdebugdatatarget-allocatevirtualmemory-method.md)|예약 및/또는 커밋 대상 프로세스의 가상 주소 공간 내의 메모리 영역입니다.|  
|[IJsDebugDataTarget::CreateStackFrameEnumerator 메서드](../../winscript/reference/ijsdebugdatatarget-createstackframeenumerator-method.md)|스택 프레임에 대 한 열거자를 만듭니다.|  
|[IJsDebugDataTarget::FreeVirtualMemory 메서드](../../winscript/reference/ijsdebugdatatarget-freevirtualmemory-method.md)|릴리스 및/또는 대상 프로세스의 가상 주소 공간 내의 메모리 영역을 커밋 해제|  
|[IJsDebugDataTarget::GetThreadContext 메서드](../../winscript/reference/ijsdebugdatatarget-getthreadcontext-method.md)|스레드가 제공 하는 컨텍스트를 검색 합니다.|  
|[IJsDebugDataTarget::GetTlsValue 메서드](../../winscript/reference/ijsdebugdatatarget-gettlsvalue-method.md)|디버깅 중인 스레드의 지정된 된 TLS 인덱스에 대 한 스레드 로컬 저장소 (TLS) 슬롯에서 값을 검색 합니다.|  
|[IJsDebugDataTarget::ReadBSTR 메서드](../../winscript/reference/ijsdebugdatatarget-readbstr-method.md)|디버그 대상에서 읽히는 BSTR을 읽습니다.|  
|[IJsDebugDataTarget::ReadMemory 메서드](../../winscript/reference/ijsdebugdatatarget-readmemory-method.md)|대상 프로세스의 메모리를 읽습니다.|  
|[IJsDebugDataTarget::ReadNullTerminatedString 메서드](../../winscript/reference/ijsdebugdatatarget-readnullterminatedstring-method.md)|대상에서 지정한 개수의 문자를 읽습니다.|  
|[IJsDebugDataTarget::WriteMemory 메서드](../../winscript/reference/ijsdebugdatatarget-writememory-method.md)|대상 프로세스의 메모리를 읽습니다.|  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참고 항목  
 [Windows 스크립트 인터페이스 참조](../../winscript/reference/windows-script-interfaces-reference.md)