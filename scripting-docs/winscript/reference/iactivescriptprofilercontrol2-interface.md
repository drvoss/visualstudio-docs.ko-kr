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
ms.openlocfilehash: 7059868ae65c5093b24f342bd303ec70172171c0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571537"
---
# <a name="iactivescriptprofilercontrol2-interface"></a>IActiveScriptProfilerControl2 인터페이스
스크립트를 실행 하는 경우 프로 파일링을 시작 하거나 중지 하는 기능을 추가 하는 메서드를 제공 합니다.  
  
## <a name="methods"></a>메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)|해당 하는 모든 스크립팅 엔진에서 프로 파일링을 시작 했음을 프로파일러에 알립니다. 이렇게 하면 프로 파일링을 시작할 때 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 실행 되는 경우 전체 호출 스택을 가져올 수 있습니다.|  
|[IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)|해당 하는 모든 스크립팅 엔진에서 프로 파일링을 중지 하도록 프로파일러에 알립니다. 이렇게 하면 프로 파일링을 중지할 때 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 실행 되는 경우 전체 호출 스택을 가져올 수 있습니다.|  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScriptProfilerControl 인터페이스](../../winscript/reference/iactivescriptprofilercontrol-interface.md)   
 [액티브 스크립트 프로파일러 인터페이스](../../winscript/reference/active-script-profiler-interfaces.md)