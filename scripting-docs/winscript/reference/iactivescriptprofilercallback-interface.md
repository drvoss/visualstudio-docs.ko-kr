---
title: IActiveScriptProfilerCallback 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 76f9164b-b086-4b29-ac79-76f9c76f1d11
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9ae520dcb36e00dfaba8702db6294a5a47484b0a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571719"
---
# <a name="iactivescriptprofilercallback-interface"></a>IActiveScriptProfilerCallback 인터페이스
이벤트가 발생할 때 스크립팅 엔진에서 프로파일러 개체에 알리는 데 사용 하는 메서드를 제공 합니다. 이 인터페이스는 프로파일러 개체에 의해 구현 됩니다.  
  
## <a name="methods"></a>메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)|스크립팅 엔진에서 프로 파일링이 시작 될 때마다 프로파일러 개체를 초기화 하기 위해 호출 됩니다.|  
|[IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)|스크립팅 엔진에서 프로 파일링이 중지 될 때마다 프로파일러 개체를 해제 하 고 해제 하기 위해 호출 됩니다.|  
|[IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)|스크립팅 엔진이 스크립트를 컴파일 했음을 프로파일러 개체에 알립니다.|  
|[IActiveScriptProfilerCallback::FunctionCompiled](../../winscript/reference/iactivescriptprofilercallback-functioncompiled.md)|스크립트를 컴파일할 때 스크립팅 엔진에서 함수를 발견 했음을 프로파일러 개체에 알립니다.|  
|[IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)|스크립팅 엔진이 DOM (문서 개체 모델)에 대 한 호출이 아닌 함수 호출을 실행 하려고 한다는 사실을 프로파일러 개체에 알립니다.|  
|[IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)|스크립팅 엔진이 DOM을 호출 하지 않는 함수 호출의 실행을 완료 했음을 프로파일러 개체에 알립니다.|  
  
## <a name="remarks"></a>주의  
 [IActiveScriptProfilerCallback2 인터페이스](../../winscript/reference/iactivescriptprofilercallback2-interface.md)를 통해 DOM (문서 개체 모델)에 대 한 함수 호출 알림이 제공 됩니다.  
  
> [!NOTE]
> 스크립트를 실행 하는 동안 프로 파일링을 시작 및 중지 하는 기능을 추가 하려면 다음 메서드를 호출 합니다. 이러한 메서드를 사용 하 여 프로 파일링을 시작 하거나 중지할 때 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 실행 되는 경우 전체 호출 스택을 가져올 수 있습니다.  
> 
> - [IActiveScriptProfilerControl2:: CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) 를 호출 하 여 프로파일러에 프로 파일링을 시작 했음을 알립니다.  
>   - [IActiveScriptProfilerControl2::P repareprofilerstop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) 를 호출 하 여 곧 프로 파일링을 중지할 프로파일러에 알립니다.  
  
## <a name="see-also"></a>참조  
 [액티브 스크립트 프로파일러 인터페이스](../../winscript/reference/active-script-profiler-interfaces.md)