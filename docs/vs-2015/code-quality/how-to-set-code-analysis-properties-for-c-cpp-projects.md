---
title: '방법: C-에 대 한 코드 분석 속성 설정C++ 프로젝트 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.native
- VC.Project.VCCLCompilerTool.EnablePrefast
- VC.Project.VCFxCopTool.EnablePREfast
- VC.Project.VCFxCopTool.IgnoreGeneratedCode
helpviewer_keywords:
- properties, C/C++ Code Analysis
- properties, Code Analysis
- code analysis properties
- C/C++ code analysis properties
ms.assetid: 7af52097-6d44-4785-9b9f-43b7a7d447d7
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: 4ebed266924861dac4bfc9e316a56907dbd11534
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201313"
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>방법: C/C++ 프로젝트의 코드 분석 속성 설정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

프로젝트의 각 구성에 있는 코드를 분석 하려면 코드 분석 도구를 사용 하는 규칙을 구성할 수 있습니다. 또한 생성 하 고 타사 도구에서 프로젝트에 추가 된 코드에서 발생 한 경고를 표시 하지 않으려면 코드 분석을 보낼 수 있습니다.  
  
## <a name="code-analysis-property-page"></a>코드 분석 속성 페이지  
 합니다 **코드 분석** 속성 페이지를 프로젝트에 대 한 모든 코드 분석 구성 설정이 포함 되어 있습니다. 프로젝트의 코드 분석 속성 페이지를 열려면 **솔루션 탐색기**프로젝트를 마우스 오른쪽 단추로 클릭 하 고 클릭 **속성**합니다. 다음으로 확장 **구성 속성** 선택 합니다 **코드 분석** 탭 합니다.  
  
## <a name="project-configuration-and-platform"></a>프로젝트 구성 및 플랫폼  
 합니다 **Configuration** 목록 및 **플랫폼** 목록을 통해 다양 한 프로젝트 구성 및 플랫폼 조합에 다른 코드 분석 설정을 적용할 수 있습니다. 예를 들어, 디버그에 대 한 프로젝트에 규칙의 집합을 적용 하는 코드 분석을 빌드하고 빌드 릴리스에 대 한 다양 한 집합을 보낼 수 있습니다.  
  
## <a name="enabling-code-analysis"></a>코드 분석을 사용 하도록 설정  
 선택 하 여 프로젝트에 대 한 코드 분석을 사용할지 여부를 결정할 수 있습니다 **활성화 코드 분석에 대 한 C /C++ 빌드에서**합니다. 와 함께에서 합니다 **구성** 목록 결정할 수 있습니다, 예를 들어 디버그 빌드 및 릴리스 빌드에 사용에 대 한 코드 분석을 사용 하지 않도록 설정 합니다.  
  
 관리 되는 코드를 포함 하는 프로젝트를 선택 하 여 코드 분석을 사용할지 여부를 결정할 수 있습니다 **빌드에 코드 분석 사용**합니다.  
  
 코드 분석은 코드의 품질을 개선 하 고 일반적인 문제를 피할 수 있도록 설계 되었습니다. 따라서 신중 하 게 고려해 야 코드 분석의 비활성화 여부. 규칙 집합을 사용 하지 않도록 설정 하는 것이 좋습니다 또는 개별 규칙을 원하지 않는 프로젝트에 적용 합니다.  
  
## <a name="generated-code"></a>생성된 코드  
 개발자는 자주 응용 프로그램을 신속 하 게 개발 하는 데 도구를 사용 합니다. 이러한 도구는 프로젝트에 추가 되는 코드를 생성할 수 있습니다. 생성 된 코드에서 코드 분석을 검색 하는 규칙 위반을 확인 하려는 합니다. 그러나 코드를 유지 관리 하지 않으려는 경우이 참조 하지 않을 수 있습니다.  
  
 합니다 **생성 된 코드 결과 표시 안 함** 확인란 합니다 **일반** 속성 페이지에서 타사 도구에서 생성 되는 관리 코드에서 코드 분석 경고를 표시 하려는 지 여부를 선택할 수 있습니다 .  
  
## <a name="rule-sets"></a>규칙 집합  
 관리 코드를 포함 하는 프로젝트, 코드 분석에서에서 규칙 집합을 선택 하 여 적용할 규칙을 선택할 수 있습니다 합니다 **이 규칙 집합 실행** 목록입니다.  
  
## <a name="see-also"></a>관련 항목  
 [관리 코드 품질 분석](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [C/C++용 코드 분석 경고](../code-quality/code-analysis-for-c-cpp-warnings.md)
