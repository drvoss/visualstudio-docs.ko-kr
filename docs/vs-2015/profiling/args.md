---
title: Args | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 65759da4363891c713f906e6cb10f00443bcbceb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68197906"
---
# <a name="args"></a>Args
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCmd.exe **Args** 옵션은 **Launch** 하위 명령의 대상 애플리케이션에 전달되는 인수 목록을 지정합니다.  
  
 명령줄에서 **Launch**도 지정한 경우에만 **Args**를 사용할 수 있습니다. **Launch**가 지정된 경우 **Args**는 선택 사항입니다.  
  
## <a name="syntax"></a>구문  
  
```  
VSPerfCmd.exe /Launch:AppName /Args:Arguments [Options]  
```  
  
#### <a name="parameters"></a>매개 변수  
 `Arguments`  
 **Launch** 명령의 대상 애플리케이션에 대한 인수 목록입니다.  
  
## <a name="required-options"></a>필수 옵션  
 **Launch:** `AppName`  
 지정된 애플리케이션을 시작하고 샘플링 방법으로 프로파일링을 시작합니다.  
  
## <a name="example"></a>예  
 다음 예제에서는 **Args** 옵션을 사용하여 TestApp.exe에 인수를 전달합니다.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Args:"123, 'Hello World'"  
```  
  
## <a name="see-also"></a>참고 항목  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [독립 실행형 애플리케이션 프로파일링](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET 웹 애플리케이션 프로파일링](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [서비스 프로파일링](../profiling/command-line-profiling-of-services.md)
