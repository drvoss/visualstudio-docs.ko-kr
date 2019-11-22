---
title: Analyzing Application Quality by Using Code Analysis Tools | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.analysisresults
helpviewer_keywords:
- application quality, analyzing
- code analysis
- team-based development, analyzing application quality
ms.assetid: 21680516-ddb5-446d-90d4-19d94f6ec699
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8b85bbad909a05bacab361a49cc7e029482ad606
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74291203"
---
# <a name="analyzing-application-quality-by-using-code-analysis-tools"></a>코드 분석 도구를 사용하여 애플리케이션 품질 분석
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In This Section [Analyzing Managed Code Quality](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md) Visual Studio code analysis for managed code provides information about managed assemblies, such as violations of the programming and design rules set forth in the Microsoft .NET Framework Design Guidelines. 경고 메시지는 관련 프로그래밍 및 디자인 문제를 식별하며 가능한 경우 문제 해결 방법에 대한 정보를 제공합니다.

 [Analyzing C/C++ Code Quality by Using Code Analysis](../code-quality/analyzing-c-cpp-code-quality-by-using-code-analysis.md) The C/C++ Code Analysis tool provides information to developers about possible defects in their C/C++ source code. 이 도구를 통해 보고되는 일반적인 코딩 오류에는 버퍼 오버런, 초기화되지 않은 메모리, null 포인터 역참조, 메모리 및 리소스 누수 등이 포함됩니다.

 [Using Rule Sets to Group Code Analysis Rules](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) Select and create *rule sets* to apply to your project.

 [Code Analysis Application Errors](../code-quality/code-analysis-application-errors.md) Fix errors in the code analysis functionality.

 [Enhancing Code Quality with Team Project Check-in Policies](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md) When you use Team Foundation Version Control (TFVC), you can create check-in policies for your team projects that enforce practices that lead to better code and more efficient group development. 체크 인 정책은 팀 프로젝트 수준에서 설정되어 코드 체크 인이 허용되기 전에 개발자 컴퓨터에서 적용되는 규칙입니다.

### <a name="code-analysis-for-drivers"></a>드라이버에 대한 코드 분석
 코드 분석 도구는 드라이버 소스 코드를 체계적으로 분석하여 안정성과 드라이버의 신뢰성을 향상시킬 수 있습니다.

 [Analyzing Driver Quality by Using Code Analysis Tools](/windows-hardware/drivers/devtest/tools-for-verifying-drivers) Code Analysis for Drivers is a compile-time static verification tool that detects basic coding errors in C and C++ programs and includes a specialized module that is designed to detect errors in (primarily) kernel-mode driver code. SDV(정적 드라이버 확인 프로그램)는 Windows 커널 모드 드라이버의 소스 코드를 체계적으로 분석하는 정적 검증 도구입니다. SDV는 드라이버가 Windows 운영 체제 커널과 제대로 상호 작용하는지 여부를 결정합니다.

 [Code Analysis for Drivers Warnings](https://go.microsoft.com/fwlink/?LinkId=225920) Describes the warnings that the Code Analysis for Drivers reports when it detects a possible error in driver code.

## <a name="related-tasks"></a>관련 작업
 [Measuring Complexity and Maintainability of Managed Code](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md) Insert description here.

 [Unit Test Your Code](../test/unit-test-your-code.md) Insert description here.
