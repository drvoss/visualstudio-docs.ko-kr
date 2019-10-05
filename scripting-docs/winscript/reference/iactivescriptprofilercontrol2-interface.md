---
title: IActiveScriptProfilerControl2 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerControl2 interface
ms.assetid: 89455276-5c23-420b-a7e0-804a32635291
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 11987054ed934f4004333f136ea35696ff6c394f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993036"
---
# <a name="iactivescriptprofilercontrol2-interface"></a>IActiveScriptProfilerControl2 인터페이스
시작 하거나 스크립트를 실행 중일 때 프로 파일링을 중지 하는 기능을 추가 하는 메서드를 제공 합니다.  
  
## <a name="methods"></a>메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)|모든 적용 가능한 스크립팅 엔진에서 프로 파일링 시작 했다고 프로파일러에 알립니다. 이렇게 하면 전체 호출 스택을 확인할 수 있습니다 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 프로 파일링을 시작할 때 실행 됩니다.|  
|[IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)|모든 적용 가능한 스크립팅 엔진에서 프로 파일링을 중지 하려는 프로파일러에 알립니다. 이렇게 하면 전체 호출 스택을 확인할 수 있습니다 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 프로 파일링을 중지 하면 실행 됩니다.|  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScriptProfilerControl 인터페이스](../../winscript/reference/iactivescriptprofilercontrol-interface.md)   
 [액티브 스크립트 프로파일러 인터페이스](../../winscript/reference/active-script-profiler-interfaces.md)