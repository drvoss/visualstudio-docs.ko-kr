---
title: 관리 코드 개요에 대 한 코드 분석 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
ms.assetid: 12ec0dab-46a4-43d8-984a-440730ef37a9
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b2d84ba17fb3fd866dcd73cd2821289c40153b6d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49872670"
---
# <a name="code-analysis-for-managed-code-overview"></a>관리 코드에 대한 코드 분석 개요
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

관리 코드에 대한 코드 분석에서는 관리되는 어셈블리를 분석하고, Microsoft .NET Framework 디자인 지침에 설정된 프로그래밍 및 디자인 규칙의 위반과 같은 어셈블리 관련 정보를 보고합니다.  
  
 분석 도구는 분석하는 동안 수행하는 검사를 경고 메시지로 나타냅니다. 경고 메시지는 관련 프로그래밍 및 디자인 문제를 식별하며 가능한 경우 문제 해결 방법에 대한 정보를 제공합니다.  
  
## <a name="ide-integrated-development-environment-integration"></a>IDE(통합 개발 환경) 통합  
 개발자는 프로젝트에 대한 코드 분석을 자동으로 실행하거나 수동으로 실행할 수 있습니다.  
  
 프로젝트를 빌드할 때마다 코드 분석을 실행 하려면 선택 **코드 빌드에 분석 사용 (CODE_ANALYSIS 상수 정의)** 프로젝트의 속성 페이지. 자세한 내용은 [방법: 설정 및 자동 코드 분석 사용 안 함](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)합니다.  
  
 코드 분석 실행 하려면 수동으로 프로젝트에 대해에 **분석** 메뉴에서 클릭 **에서 코드 분석 실행**_ProjectName_합니다. 자세한 내용은 [방법: 설정 및 자동 코드 분석 사용 안 함](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)합니다.  
  
## <a name="rule-sets"></a>규칙 집합  
 관리 코드에 대 한 코드 분석 규칙 그룹화 됩니다 *규칙 집합*합니다. Microsoft 표준 규칙 집합 중 하나를 사용하거나, 특정 요구 사항에 맞게 사용자 지정 규칙 집합을 만들 수 있습니다. 자세한 내용은 [코드 분석 규칙 그룹화를 사용 하 여 규칙 집합](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)합니다.  
  
## <a name="in-source-suppression"></a>ISS  
 경고가 적용되지 않는 것으로 표시하면 유용한 경우가 많습니다. 이렇게 하면 경고를 조사한 다음 이를 표시하지 않거나 무시하도록 설정했다는 것을 개발자와 나중에 이 코드를 검토할 수 있는 다른 사람에게 알릴 수 있습니다.  
  
 경고 ISS는 사용자 지정 특성을 통해 구현됩니다. 경고를 표시하지 않으려면 다음 예제와 같이 소스 코드에 `SuppressMessage` 특성을 추가합니다.  
  
 `[System.Diagnosis.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 `Public class MyClass`  
  
 `{`  
  
 `// code`  
  
 `}`  
  
 자세한 내용은 [표시 하지 않으려면 경고 사용 하 여 SuppressMessage 특성](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)합니다.  
  
## <a name="run-code-analysis-as-part-of-check-in-policy"></a>체크 인 정책의 일부로 코드 분석 실행  
 조직에서 반드시 특정 정책에 따라 체크 인을 수행하려는 경우 특히 다음 정책을 따르는지 확인할 수 있습니다.  
  
- 체크 인할 코드에 빌드 오류가 없습니다.  
  
- 최신 빌드의 일부로 코드 분석을 실행합니다.  
  
  체크 인 정책을 지정하여 위 사항을 확인할 수 있습니다. 자세한 내용은 [팀 프로젝트 체크 인 정책 사용 하 여 코드 품질 향상](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)합니다.  
  
## <a name="team-build-integration"></a>팀 빌드 통합  
 빌드 시스템의 통합된 기능을 사용하여 빌드 프로세스의 일부로 분석 도구를 실행할 수 있습니다. 자세한 내용은 [응용 프로그램 빌드](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [코드 분석 규칙 그룹화를 설정 하는 규칙을 사용 하 여](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)   
 [방법: 자동 코드 분석 사용 설정 및 해제](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)



