---
title: IJsDebugProcess 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a7ad5525-55b7-4c68-a4f7-c508f7877712
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9200515b2c975fb1fa5b2acda7c261cb684d85b4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577338"
---
# <a name="ijsdebugprocess-interface"></a>IJsDebugProcess 인터페이스
대상 프로세스를 검사 하 고 제어 하는 루틴을 제공 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
IJsDebugProcess : public IUnknown;  
```  
  
## <a name="members"></a>멤버  
  
### <a name="public-methods"></a>Public 메서드  
  
|name|설명|  
|----------|-----------------|  
|[IJsDebugProcess::CreateBreakPoint 메서드](../../winscript/reference/ijsdebugprocess-createbreakpoint-method.md)|지정한 문서 위치에서 중단점을 설정합니다.|  
|[IJsDebugProcess::CreateStackWalker 메서드](../../winscript/reference/ijsdebugprocess-createstackwalker-method.md)|Stack walker에 대 한 팩터리 메서드입니다.|  
|[IJsDebugProcess::PerformAsyncBreak 메서드](../../winscript/reference/ijsdebugprocess-performasyncbreak-method.md)|스크립트 엔진을 중단 모드로 전환 하 여 다음 스크립트 명령에서 중단 되도록 합니다.|  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참조  
 [Windows 스크립트 인터페이스 참조](../../winscript/reference/windows-script-interfaces-reference.md)