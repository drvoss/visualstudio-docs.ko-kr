---
title: IActiveScript::GetScriptThreadID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptThreadID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptThreadID
ms.assetid: 2595d76e-30b5-429f-88b4-1d026645dd9b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d329e08e6a17d9edcdf26e14b468c3c56f036c00
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935694"
---
# <a name="iactivescriptgetscriptthreadid"></a>IActiveScript::GetScriptThreadID
지정 된 Win32 스레드와 연결 된 스레드에 대 한 스크립팅 엔진 정의 식별자를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetScriptThreadID(  
    DWORD dwWin32ThreadID,       // Win32 thread identifier.  
    SCRIPTTHREADID *pstidThread  // Receives scripting thread. identifier  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dwWin32ThreadID` ,  
 [in] 현재 프로세스에서 실행 중인 Win32 스레드의 스레드 식별자입니다. 사용 된 [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md) 현재 실행 중인 스레드의 스레드 식별자를 검색 하는 함수입니다.  
  
 `pstidThread` ,  
 [out] 지정 된 Win32 스레드와 연결 된 스크립트 스레드 식별자를 받는 변수의 주소입니다. 이 식별자의 해석은 스크립팅 엔진에 그대로 있지만 Windows 스레드 식별자의 복사본 수 있습니다. 참고 Win32 스레드가 종료 하는 경우이 식별자 할당 되지 않은 되 고 이후에 다른 스레드가 할당 될 수 있습니다.  
  
## <a name="return-value"></a>반환 값  
 다음 값 중 하나를 반환합니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|`S_OK`|명령 실행 성공|  
|`E_POINTER`|잘못 된 포인터가 지정 되었습니다.|  
|`E_UNEXPECTED`|호출이 필요 하지 않습니다 (예를 들어, 스크립팅 엔진에 아직 로드 되지 않았거나 초기화) 하므로 실패 합니다.|  
  
## <a name="remarks"></a>설명  
 검색 된 식별자 스크립트 스레드 실행 컨트롤 메서드에 대 한 후속 호출에서 같은 사용할 수 있습니다 합니다 [iactivescript:: Interruptscriptthread](../../winscript/reference/iactivescript-interruptscriptthread.md) 메서드.  
  
 호스트 개체 또는 기본이 아닌 설명선 발생 하지 않고 기본이 아닌 스레드에서이 메서드를 호출할 수는 [iactivescript:: Interruptscriptthread](../../winscript/reference/iactivescript-interruptscriptthread.md) 인터페이스입니다.  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScript](../../winscript/reference/iactivescript.md)