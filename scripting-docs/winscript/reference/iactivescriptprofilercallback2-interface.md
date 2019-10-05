---
title: IActiveScriptProfilerCallback2 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2 interface
ms.assetid: 8f2e62e4-c232-4dc3-a2c0-54dd06298306
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b0a0df287db477c5bf768798f200ea0d97de6d1e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63385937"
---
# <a name="iactivescriptprofilercallback2-interface"></a>IActiveScriptProfilerCallback2 인터페이스
문서 개체 모델 (DOM) 이벤트가 발생할 때 프로파일러 개체에 알리기 위해 스크립팅 엔진에서 사용 되는 메서드를 제공 합니다. 이 인터페이스는 프로파일러 개체에 의해 구현 됩니다.  
  
## <a name="methods"></a>메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)|스크립팅 엔진은 DOM 함수 호출을 실행 하는 프로파일러 개체를 알립니다.|  
|[IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)|DOM 함수 호출을 실행 하는 스크립팅 엔진 개체가 완료 되 면 프로파일러에 알립니다.|  
  
## <a name="remarks"></a>설명  
 `IActiveScriptProfilerCallback2` Internet Explorer 9과 함께 처음 릴리스 하는 인터페이스입니다.  
  
 DOM에 호출 되지 않는 함수 호출에 대 한 알림을 제공 합니다 [IActiveScriptProfilerCallback 인터페이스](../../winscript/reference/iactivescriptprofilercallback-interface.md)합니다.  
  
> [!NOTE]
> 시작 하 고 스크립트를 실행 중일 때 프로 파일링을 중지 하는 기능을 추가 하려면 다음 메서드를 호출 합니다. 이러한 메서드를 사용 하 여 얻을 수 있으면 전체 호출 스택을 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 시작 하거나 프로 파일링을 중지 하는 경우 실행 됩니다.  
> 
> - 호출 [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) 프로 파일링 시작 했다고 프로파일러에 알립니다.  
>   - 호출 [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) 는 곧 중지 하는 프로 파일링을 프로파일러에 알립니다.  
  
## <a name="see-also"></a>참고 항목  
 [액티브 스크립트 프로파일러 인터페이스](../../winscript/reference/active-script-profiler-interfaces.md)