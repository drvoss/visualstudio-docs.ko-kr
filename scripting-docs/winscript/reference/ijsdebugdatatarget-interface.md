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
ms.openlocfilehash: 85c77209230abfe261c9ec0b884ad0a677cfbf07
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572457"
---
# <a name="ijsdebugdatatarget-interface"></a>IJsDebugDataTarget 인터페이스
대상 디버거 프로세스의 상태를 액세스 하 고 해당 상태를 변경 하는 기능을 제공 하기 위해 디버거에서 구현 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
IJsDebugDataTarget : public IUnknown;  
```  
  
## <a name="members"></a>멤버  
  
### <a name="public-methods"></a>Public 메서드  
  
|name|설명|  
|----------|-----------------|  
|[IJsDebugDataTarget::AllocateVirtualMemory 메서드](../../winscript/reference/ijsdebugdatatarget-allocatevirtualmemory-method.md)|대상 프로세스의 가상 주소 공간 내에서 메모리 영역을 예약 및/또는 커밋합니다.|  
|[IJsDebugDataTarget::CreateStackFrameEnumerator 메서드](../../winscript/reference/ijsdebugdatatarget-createstackframeenumerator-method.md)|스택 프레임에 대 한 열거자를 만듭니다.|  
|[IJsDebugDataTarget::FreeVirtualMemory 메서드](../../winscript/reference/ijsdebugdatatarget-freevirtualmemory-method.md)|대상 프로세스의 가상 주소 공간 내에서 메모리 영역을 해제 및/또는 커밋 취소 합니다.|  
|[IJsDebugDataTarget::GetThreadContext 메서드](../../winscript/reference/ijsdebugdatatarget-getthreadcontext-method.md)|지정 된 스레드의 컨텍스트를 검색 합니다.|  
|[IJsDebugDataTarget::GetTlsValue 메서드](../../winscript/reference/ijsdebugdatatarget-gettlsvalue-method.md)|디버깅 중인 스레드의 경우 지정 된 TLS 인덱스의 TLS (스레드 로컬 저장소) 슬롯에서 값을 검색 합니다.|  
|[IJsDebugDataTarget::ReadBSTR 메서드](../../winscript/reference/ijsdebugdatatarget-readbstr-method.md)|디버그 대상에서 BSTR을 읽습니다.|  
|[IJsDebugDataTarget::ReadMemory 메서드](../../winscript/reference/ijsdebugdatatarget-readmemory-method.md)|대상 프로세스의 메모리를 읽습니다.|  
|[IJsDebugDataTarget::ReadNullTerminatedString 메서드](../../winscript/reference/ijsdebugdatatarget-readnullterminatedstring-method.md)|대상에서 지정 된 수의 문자를 읽습니다.|  
|[IJsDebugDataTarget::WriteMemory 메서드](../../winscript/reference/ijsdebugdatatarget-writememory-method.md)|대상 프로세스의 메모리를 읽습니다.|  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참조  
 [Windows 스크립트 인터페이스 참조](../../winscript/reference/windows-script-interfaces-reference.md)