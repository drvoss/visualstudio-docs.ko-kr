---
title: 프로파일러 명령줄을 사용하여 독립 실행형 응용 프로그램에 대한 응용 프로그램 통계 수집 | Microsoft 문서
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- sampling profiling method
- profilng tools,sampling method
ms.assetid: be2dbdd0-fc88-45f9-a1d5-bcb4f64e17ad
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9841911dbb1fc9bb97eb995534af3eaec73d10e9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756967"
---
# <a name="collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line"></a>프로파일러 명령줄을 사용하여 독립 실행형 응용 프로그램에 대한 응용 프로그램 통계 수집
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 섹션에서는 명령줄 도구에서 샘플링 방법을 사용하여 클라이언트(독립 실행형) 응용 프로그램에 대한 성능 통계를 수집하기 위한 절차 및 옵션을 설명합니다.  
  
> [!NOTE]
>  Windows 8 및 Windows Server 2012의 강화된 보안 기능을 위해 Visual Studio 프로파일러가 이러한 플랫폼에서 데이터를 수집하는 방법을 상당히 변경해야 했습니다. Windows 스토어 앱에는 새로운 수집 기술도 필요합니다. [Windows 8 및 Windows Server 2012 응용 프로그램의 성능 도구](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)를 참조하세요.  
  
## <a name="common-tasks"></a>일반 작업  
  
|작업|관련 콘텐츠|  
|----------|---------------------|  
|**프로파일링을 사용하여 응용 프로그램 시작**|-   [방법: 독립 실행형 응용 프로그램을 시작하여 응용 프로그램 통계 수집](../profiling/how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line.md)|  
|**실행 중인 .NET Framework 응용 프로그램에 프로파일러 연결**|-   [방법: .NET Framework 응용 프로그램에 프로파일러 연결 및 응용 프로그램 통계 수집](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)|  
|**실행 중인 C/C++ 응용 프로그램에 프로파일러 연결**|-   [방법: 네이티브 응용 프로그램에 프로파일러 연결 및 응용 프로그램 통계 수집](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)|  
|**계층 상호 작용 데이터 추가**|-   [계층 상호 작용 데이터 수집](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## <a name="related-tasks"></a>관련 작업  
  
### <a name="profiling-stand-alone-applications"></a>독립 실행형 응용 프로그램 프로파일링  
  
|작업|관련 콘텐츠|  
|----------|---------------------|  
|**응용 프로그램 계측**|-   [계측을 사용하여 자세한 타이밍 데이터 수집](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**.NET 메모리 할당 및 가비지 수집 데이터**|-   [.NET Framework 메모리 데이터 수집](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**리소스 경합 및 스레드 실행 데이터 수집**|-   [동시성 데이터 수집](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
  
### <a name="profiling-by-using-the-sampling-method"></a>샘플링 방법을 사용하여 프로파일링  
  
|작업|관련 콘텐츠|  
|----------|---------------------|  
|**ASP.NET 웹 응용 프로그램 프로파일링**|-   [샘플링을 사용하여 응용 프로그램 통계 수집](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**서비스 프로파일링**|-   [샘플링을 사용하여 응용 프로그램 통계 수집](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md). 샘플링 방법을 사용하여 Windows 서비스에서 성능 통계를 수집하는 방법을 설명합니다.|  
  
### <a name="analyzing-sampling-data-views-and-reports"></a>샘플링 데이터 뷰 및 보고서 분석  
 [샘플링 방법 데이터 뷰](../profiling/profiler-sampling-method-data-views.md)



