---
title: 'IRemoteDebugApplication:: ResumeFromBreakPoint | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.ResumeFromBreakPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::ResumeFromBreakPoint
ms.assetid: a613cc2b-1d69-4713-a235-64372c253b4a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7fead9c14efbe73bd006a5ff3e1cfb10ad40404b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577455"
---
# <a name="iremotedebugapplicationresumefrombreakpoint"></a>IRemoteDebugApplication::ResumeFromBreakPoint
현재 중단점에 있는 응용 프로그램을 계속 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT ResumeFromBreakPoint(  
   IRemoteDebugApplicationThread*  prptFocus,  
   BREAKRESUMEACTION               bra,  
   ERRORRESUMEACTION               era  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `prptFocus`  
 진행 스테핑 모드의 경우 단계별 실행 모드의 영향을 받을 스레드입니다.  
  
 `bra`  
 진행 응용 프로그램을 다시 시작할 때 수행할 동작입니다.  
  
 `era`  
 진행 오류가 발생 하 여 응용 프로그램이 중지 되는 경우 수행할 작업입니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 `HRESULT`를 반환합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 현재 중단점에 있는 응용 프로그램을 계속 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [Iremotedebugapplication 인터페이스](../../winscript/reference/iremotedebugapplication-interface.md)   
 [BREAKRESUMEACTION 열거형](../../winscript/reference/breakresumeaction-enumeration.md)   
 [ERRORRESUMEACTION 열거형](../../winscript/reference/errorresumeaction-enumeration.md)