---
title: IActiveScriptProfilerControl 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1448b394-9743-41b5-8eb9-5026a45773a4
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 86f4fb8dea97930f717800a14a27740b76eb6c2e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993061"
---
# <a name="iactivescriptprofilercontrol-interface"></a>IActiveScriptProfilerControl 인터페이스
프로 파일링을 지 원하는 스크립팅 엔진에 의해 구현 됩니다. 일반적으로 구현 하는 개체를 `IActiveScriptProfilerControl` 도 구현 합니다 [IActiveScript](../../winscript/reference/iactivescript.md) 인터페이스입니다. 이 경우에 대 한 핸들을 가져올 수 있습니다 합니다 `IActiveScriptProfilerControl` 를 호출 하 여 인터페이스를 `IUnknown::QueryInterface` 개체의 메서드를 합니다. 인터페이스를 중지 하 고 스크립팅 엔진에서 프로 파일링을 시작 하 고 필요한 메서드를 제공 합니다.  
  
## <a name="methods"></a>메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)|스크립팅 엔진에서 프로 파일링을 시작 합니다.|  
|[IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)|스크립팅 엔진에서 프로파일러 이벤트 마스크를 설정 합니다.|  
|[IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)|스크립팅 엔진에서 프로 파일링을 중지 합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [액티브 스크립트 프로파일러 인터페이스](../../winscript/reference/active-script-profiler-interfaces.md)