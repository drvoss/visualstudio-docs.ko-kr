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
ms.openlocfilehash: 25f9616497192659df67feedfe16bd9ea0c5e3b1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577309"
---
# <a name="iactivescriptprofilercallback2-interface"></a>IActiveScriptProfilerCallback2 인터페이스
DOM (문서 개체 모델) 이벤트가 발생할 때 스크립팅 엔진에서 프로파일러 개체에 알리는 데 사용 하는 메서드를 제공 합니다. 이 인터페이스는 프로파일러 개체에 의해 구현 됩니다.  
  
## <a name="methods"></a>메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)|스크립팅 엔진이 DOM 함수 호출을 실행 하 고 있음을 프로파일러 개체에 알립니다.|  
|[IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)|스크립팅 엔진이 DOM 함수 호출의 실행을 완료 했음을 프로파일러 개체에 알립니다.|  
  
## <a name="remarks"></a>주의  
 Internet Explorer 9를 사용 하 여 처음 릴리스된 `IActiveScriptProfilerCallback2` 인터페이스입니다.  
  
 DOM에 대 한 호출이 아닌 함수 호출에 대 한 알림은 [IActiveScriptProfilerCallback 인터페이스](../../winscript/reference/iactivescriptprofilercallback-interface.md)에서 제공 됩니다.  
  
> [!NOTE]
> 스크립트를 실행 하는 동안 프로 파일링을 시작 및 중지 하는 기능을 추가 하려면 다음 메서드를 호출 합니다. 이러한 메서드를 사용 하 여 프로 파일링을 시작 하거나 중지할 때 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 실행 되는 경우 전체 호출 스택을 가져올 수 있습니다.  
> 
> - [IActiveScriptProfilerControl2:: CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) 를 호출 하 여 프로파일러에 프로 파일링을 시작 했음을 알립니다.  
>   - [IActiveScriptProfilerControl2::P repareprofilerstop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) 를 호출 하 여 곧 프로 파일링을 중지할 프로파일러에 알립니다.  
  
## <a name="see-also"></a>참조  
 [액티브 스크립트 프로파일러 인터페이스](../../winscript/reference/active-script-profiler-interfaces.md)