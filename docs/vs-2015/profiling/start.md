---
title: Start | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b85d0fe9-f67a-4b7c-8d48-7eecf3f2dfe9
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6c2f52a000cdf5eaa1a1ef4b9afeb141500f1911
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724182"
---
# <a name="start"></a>시작
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Start** 옵션은 지정된 프로파일링 방법으로 프로파일러를 초기화하는 VSPerfCmd.exe 옵션입니다.  
  
## <a name="syntax"></a>구문  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### <a name="parameters"></a>매개 변수  
 `Method`  
 다음 키워드 중 하나여야 합니다.  
  
-   **TRACE** - 계측 방법을 지정합니다.  
  
-   **SAMPLE** - 샘플링 방법을 지정합니다.  
  
-   **COVERAGE** - 코드 검사를 지정합니다.  
  
-   **CONCURRENCY** - 리소스 경합 방법을 지정합니다.  
  
## <a name="required-options"></a>필수 옵션  
 명령줄에서 **Start**를 지정할 때는 **Output** 옵션을 지정해야 합니다.  
  
 **Output:** `filename`  
 출력 파일 이름을 지정합니다.  
  
## <a name="exclusive-options"></a>전용 옵션  
 다음 옵션은 명령줄에서 **Start** 옵션과 함께 사용해야 합니다.  
  
 **CrossSession**&#124;**CS**  
 프로세스 간 프로파일링을 활성화합니다. 옵션 이름 **CrossSession** 및 **CS**가 둘 다 지원됩니다.  
  
 **User:**[`domain\`]`username`  
 클라이언트가 지정한 계정에서 모니터에 액세스할 수 있습니다.  
  
 **WinCounter:** `Path` [**Automark**:`n`]  
 **WinCounter**는 프로파일링 데이터 파일의 표시로 포함할 Windows 성능 카운터를 지정합니다. **AutoMark**는 데이터 파일의 수집 간 간격(밀리초)을 지정합니다.  
  
## <a name="invalid-options"></a>잘못된 옵션  
 다음 옵션은 명령줄에서 **Start** 옵션과 함께 사용할 수 없습니다.  
  
 **Status**  
 **Status**는 프로파일링되는 프로세스에 적용되며 프로세스 및 스레드와 해당 현재 프로필 상태(On/Off) 목록을 표시합니다. 예를 들어 프로세스가 중지되더라도 보고서에서 **Status**에는 해당 상태가 나타나지 않습니다. 즉, **Status**는 프로세스가 프로파일링되었는지 여부를 표시합니다.  
  
 **Shutdown**[**:**`Timeout`]  
 프로파일러를 해제합니다.  
  
## <a name="example"></a>예제  
 다음 예제에서는 VSPerfCmd.exe **Start** 옵션을 사용하여 프로파일러를 초기화하는 방법을 보여 줍니다.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## <a name="see-also"></a>참고 항목  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [독립 실행형 응용 프로그램 프로파일링](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET 웹 응용 프로그램 프로파일링](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [서비스 프로파일링](../profiling/command-line-profiling-of-services.md)



