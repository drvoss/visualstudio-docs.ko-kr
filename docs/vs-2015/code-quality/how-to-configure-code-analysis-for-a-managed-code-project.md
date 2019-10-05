---
title: '방법: 관리 코드 프로젝트에 대 한 코드 분석 구성 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
ms.assetid: 618f6ff3-db0e-46cb-b08d-dfa35e62c9e7
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a37ededab38cf27a002117f874d17d6a340000d9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63429164"
---
# <a name="how-to-configure-code-analysis-for-a-managed-code-project"></a>방법: 관리 코드 프로젝트에 대한 코드 분석 구성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] 및 [!INCLUDE[vsPro](../includes/vspro-md.md)], 코드 분석의 목록에서 선택할 수 있습니다 *규칙 집합* 관리 코드 프로젝트에 적용 합니다. 기본 규칙 집합은 Microsoft 최소 권장 규칙. 프로젝트 또는 솔루션의 모든 프로젝트를 설정 하는 다른 규칙을 적용할 수 있습니다.  
  
> [!NOTE]
> ASP.NET 웹 응용 프로그램에 대해 설정 하는 규칙을 구성 하는 방법에 대 한 정보를 참조 하세요. [방법: ASP.NET 웹 응용 프로그램에 대 한 코드 분석 구성](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)합니다.  
  
### <a name="to-configure-a-rule-set-for-a-net-framework-project"></a>.NET Framework 프로젝트에 대해 설정 하는 규칙을 구성 하려면  
  
1. **솔루션 탐색기**, 프로젝트를 클릭 합니다.  
  
2. 에 **분석** 메뉴에서 클릭 **에 대 한 코드 분석 구성** *ProjectName*합니다.  
  
3. 에 **구성** 하 고 **플랫폼** 목록에서 빌드 구성과 대상 플랫폼을 클릭 합니다.  
  
4. 선택한 구성을 사용 하 여 프로젝트를 빌드할 때마다 코드 분석을 실행 하려면 선택 합니다 **코드 빌드에 분석 사용 (CODE_ANALYSIS 상수 정의)** 확인란 합니다. 열어 코드 분석을 수동으로 실행할 수도 있습니다는 **분석** 메뉴를 클릭 하면 **에서 코드 분석 실행** *ProjectName*합니다.  
  
5. 기본적으로 외부 도구에 의해 자동으로 생성된 코드에서 발생한 경고는 코드 분석 시 보고되지 않습니다. 생성 된 코드에서 발생 한 경고를 보려면의 선택을 취소 합니다 **생성 된 코드 결과 표시 안 함** 확인란 합니다.  
  
    > [!NOTE]
    > 이 옵션을 선택하더라도 폼 및 템플릿에 오류와 경고가 나타날 경우에는 생성된 코드에서 발생한 코드 분석 오류 및 경고가 계속 표시됩니다. 폼이나 템플릿의 소스 코드를 볼 수도 있고 유지 관리할 수도 있습니다.  
  
6. 에 **이 규칙 집합 실행** 목록에서 다음 중 하나를 수행 합니다.  
  
    - 사용 하려는 규칙 집합을 클릭 합니다.  
  
    - 클릭  **\<찾아보기... >** 목록에 없는 기존 사용자 지정 규칙 집합을 지정 하려면.  
  
    - 사용할 규칙 집합을 선택합니다.  
  
         자세한 내용은 [사용자 지정 규칙 집합 만들기](../code-quality/creating-custom-code-analysis-rule-sets.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [연습: 구성 및 사용자 지정 규칙을 사용 설정](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)
