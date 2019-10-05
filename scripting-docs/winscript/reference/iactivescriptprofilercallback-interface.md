---
title: IActiveScriptProfilerCallback 인터페이스 | Microsoft 문서
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
ms.openlocfilehash: e8f64f187638af7f9ab4bf6b80e88fe6992c78e6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63386082"
---
# <a name="iactivescriptprofilercallback-interface"></a>IActiveScriptProfilerCallback 인터페이스
이벤트가 발생할 때 프로파일러 개체에 알리기 위해 스크립팅 엔진에서 사용 되는 메서드를 제공 합니다. 이 인터페이스는 프로파일러 개체에 의해 구현 됩니다.  
  
## <a name="methods"></a>메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)|스크립팅 엔진에서 프로 파일링을 시작할 때마다 프로파일러 개체를 초기화 하기 위해 호출 됩니다.|  
|[IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)|해제 하 고 스크립팅 엔진에서 프로 파일링이 중지 될 때마다 프로파일러 개체를 해제 하기 위해 호출 됩니다.|  
|[IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)|개체는 스크립팅 엔진 컴파일된 스크립트 프로파일러에 알립니다.|  
|[IActiveScriptProfilerCallback::FunctionCompiled](../../winscript/reference/iactivescriptprofilercallback-functioncompiled.md)|스크립트를 컴파일할 때 함수 개체는 스크립팅 엔진에 발생 프로파일러에 알립니다.|  
|[IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)|문서 개체 모델 (DOM)를 호출 하지 않은 함수 호출을 실행 하는 스크립팅 엔진 프로파일러 개체를 알립니다.|  
|[IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)|개체는 호출 하는 함수를 실행 하는 완성 된 스크립팅 엔진 아님을 DOM에 대 한 호출 프로파일러에 알립니다.|  
  
## <a name="remarks"></a>설명  
 함수 호출 문서 개체 모델 (DOM)에 대 한 알림을 제공 합니다 [IActiveScriptProfilerCallback2 인터페이스](../../winscript/reference/iactivescriptprofilercallback2-interface.md)합니다.  
  
> [!NOTE]
> 시작 하 고 스크립트를 실행 중일 때 프로 파일링을 중지 하는 기능을 추가 하려면 다음 메서드를 호출 합니다. 이러한 메서드를 사용 하 여 얻을 수 있으면 전체 호출 스택을 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 시작 하거나 프로 파일링을 중지 하는 경우 실행 됩니다.  
> 
> - 호출 [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) 프로 파일링 시작 했다고 프로파일러에 알립니다.  
>   - 호출 [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) 는 곧 중지 하는 프로 파일링을 프로파일러에 알립니다.  
  
## <a name="see-also"></a>참고 항목  
 [액티브 스크립트 프로파일러 인터페이스](../../winscript/reference/active-script-profiler-interfaces.md)