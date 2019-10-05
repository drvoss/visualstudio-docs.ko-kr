---
title: 팀 프로젝트 체크 인 정책 사용 하 여 코드 품질 향상 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code quality, using check-in policies
- team-based development, enhancing code quality
ms.assetid: 0ab72c33-148a-4a8a-a7bf-046995514c84
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 86aac26819e86455c8ab5c3676c8198bbb482e43
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697190"
---
# <a name="enhancing-code-quality-with-team-project-check-in-policies"></a>팀 프로젝트 체크 인 정책을 사용하여 코드 품질 향상
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

TFVC(Team Foundation Version Control)를 사용할 때는 팀 프로젝트에 대한 체크 인 정책을 만들어 코드 품질을 향상시키고 그룹 개발을 보다 효율적으로 수행할 수 있게 해주는 방법을 적용할 수 있습니다. 체크 인 정책은 팀 프로젝트 수준에서 설정되어 코드 체크 인이 허용되기 전에 개발자 컴퓨터에서 적용되는 규칙입니다.  
  
 다음과 같은 팀 프로젝트 체크 인 정책을 지정할 수 있습니다.  
  
- **빌드**: 새 체크 인 전에 빌드 중 생성 된 빌드 중단을 수정 해야 합니다는 필요 합니다.  
  
- **변경 집합 주석**: 변경 내용을 체크 인할 때 사용자가 주석을 제공 해야 합니다.  
  
- **코드 분석**: 코드 분석 체크 인 전에 실행 되는 필요 합니다.  
  
- **작업 항목**: 하나 이상의 작업 항목 체크 인을 사용 하 여 연결 되어 있어야 합니다.  
  
> [!IMPORTANT]
> 체크 인 정책을 사용하려면 [!INCLUDE[vststfsLong](../includes/vststfslong-md.md)]에 연결해야 합니다.  
  
## <a name="common-tasks"></a>일반 작업  
  
|작업|지원 내용|  
|----------|------------------------|  
|**페이지를 만들고 체크 인 정책을 사용 합니다.** 체크 인 정책은 팀 프로젝트 설정을 사용 하 여 만든 [!INCLUDE[esprscc](../includes/esprscc-md.md)]합니다.|[품질 게이트 설정 및 적용](https://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|  
|**만들기 및 코드 분석 체크 인 정책을 사용 하 여:** 표준 코드 분석 규칙 집합에서 선택할 수 있습니다 또는 사용자 지정 집합을 만들 수 있습니다.|[코드 분석 체크 인 정책 만들기 및 사용](../code-quality/creating-and-using-code-analysis-check-in-policies.md)|  
  
## <a name="related-tasks"></a>관련 작업  
  
|작업|지원 내용|  
|----------|------------------------|  
|**개발 환경을 설정 합니다.** 작성 하거나 코드를 수정할 수 있습니다, 전에 개발을 설정 하 고 적절 한 소스 코드를 사용 하 여 환경을 테스트 해야 합니다. 데이터베이스로 작업하는 경우 해당 오프라인 표현에도 액세스할 수 있어야 합니다.|[개발 환경 설정](https://msdn.microsoft.com/7b686610-d379-4ca0-9608-73ef0e576e3a)|  
|**개발 프로세스에서 코드 분석을 사용 합니다.** 팀 멤버는 자신의 개발 컴퓨터에서 코드 분석을 실행합니다. Visual Studio에서 개발자는 개별 코드 프로젝트에 대해 코드 분석 실행을 구성 및 실행하고, 해당 실행을 통해 발견된 문제를 확인 및 분석하며, 경고에 대한 작업 항목을 만듭니다.|[애플리케이션 품질 분석](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|  
|**만들고 단위 테스트를 실행 합니다.** 단위 테스트를 통해 개발자와 테스터의 클래스 메서드에서 논리 오류를 확인 하는 빠른 방법은 C#, Visual Basic.NET 및 C++ 프로젝트. 단위 테스트를 한 번 만든 후 해당 소스 코드가 변경될 때마다 실행하여 버그가 없는지 확인할 수 있습니다.|[코드 단위 테스트](../test/unit-test-your-code.md)|  
|**작업 항목 및 결함 추적:** 작업 항목 추적 및 팀 프로젝트에 대 한 작업 및 정보 관리를 사용할 수 있습니다. 작업 항목은 [!INCLUDE[esprfound](../includes/esprfound-md.md)] 에서 작업의 할당 및 진행률을 추적하는 데 사용하는 데이터베이스 레코드입니다. 다양한 유형의 작업 항목을 사용하여 고객 요구 사항, 제품 버그 및 개발 작업과 같은 여러 유형의 작업을 추적할 수 있습니다.|[작업 추적 및 워크플로 관리 &#91;리디렉션&#93;](https://msdn.microsoft.com/d2d8637d-0ef8-4ca3-874e-a04713344032)|  
  
## <a name="external-resources"></a>외부 리소스  
  
### <a name="guidance"></a>지침  
 [Visual Studio 2012 – Chapter 2를 사용한 연속 배달 테스트: 단위 테스트: 내부 테스트](http://go.microsoft.com/fwlink/?LinkID=255188)
