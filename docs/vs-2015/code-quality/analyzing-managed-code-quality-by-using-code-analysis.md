---
title: 코드 분석을 사용 하 여 관리 코드 품질 분석 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis,managed code
- managed code analyis
ms.assetid: 68510a55-da51-4381-81a5-0feba76b8b4f
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5d8740b79b026ade7f3da19aa4a89cacd94df17d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157129"
---
# <a name="analyzing-managed-code-quality-by-using-code-analysis"></a>코드 분석을 사용하여 관리 코드 품질 분석
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에서 코드 분석 도구를 사용하면 비보안 데이터 액세스, 사용 위반 및 디자인 문제와 같은 코드에서 잠재적인 문제를 검색할 수 있습니다. .NET Framework, 네이티브 분석 작동 코드 (C 및 C++), 및 응용 프로그램 데이터베이스입니다. 관리 코드에 대 한 코드 분석 규칙 구성 *규칙 집합* 코딩과 특정 대상으로 하는 합니다.  
  
## <a name="common-tasks"></a>일반 작업  
  
|일반 작업|지원 내용|  
|------------------|------------------------|  
|**실습 가져오기:** 간단한.NET Framework 응용 프로그램에서 결함을 수정 하 여 코드 분석의 기본 사항을 알아봅니다.|-   [연습: 코드 오류에 대한 관리 코드 분석](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)|  
|**프로젝트에 대 한 코드 분석을 구성 합니다.** 관리 코드에 대 한 규칙은 보안 및 디자인 같은 특정 영역을 대상으로 하는 규칙 집합으로 구성 됩니다. Microsoft 표준 규칙을 설정 하거나 직접 만들 중 하나를 사용할 수 있습니다.|-   [관리 코드 개요에 대 한 코드 분석](../code-quality/code-analysis-for-managed-code-overview.md)<br />-   [코드 분석 규칙 그룹화를 설정 하는 규칙을 사용 하 여](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)<br />-   [SuppressMessage 특성을 사용 하 여 경고 표시 안 함](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)|  
|**코드 분석을 실행 합니다.** 프로젝트 구성을 구축 된 때마다 자동으로 실행할 코드 분석을 지정할 수 있습니다 하 고 프로젝트에서 코드 분석을 수동으로 실행할 수 있습니다.|-   [방법: 자동 코드 분석 사용 설정 및 해제](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)<br />-   [방법: 수동으로 코드 분석 실행](../code-quality/how-to-run-code-analysis-manually-for-managed-code.md)|  
|**코드 분석 결과 분석 합니다.** 코드 분석 경고 및 오류 코드 분석 창에 나열 됩니다. 경고 또는 오류 제목을 선택하면 해당 경고에 대한 추가 정보가 표시되고 해당 규칙을 실행시킨 소스 코드 줄이 강조 표시됩니다. 경고 ID를 선택해서 MSDN 라이브러리에서 제공되는 정보 및 문제 해결 방법 예제가 포함된 세부 정보를 표시할 수 있습니다.|-   [방법: 관리 코드 오류 보기](../code-quality/how-to-view-managed-code-defects.md)<br />-   [관리 코드 경고에 대 한 코드 분석](../code-quality/code-analysis-for-managed-code-warnings.md)<br />-   [CheckId 별 경고](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)<br />-   [무명 메서드 및 코드 분석](../code-quality/anonymous-methods-and-code-analysis.md)|  
|**프로그램 개발 수명 주기를 사용 하 여 코드 분석을 통합 합니다.** 체크 인 정책에 [!INCLUDE[esprscc](../includes/esprscc-md.md)] 사용 개발 팀이 모든 코드 체크 인 되었는지 확인 하는 일반적인 코드 분석 표준 집합을 충족 합니다. 코드 분석 규칙 위반에 대 한 작업 항목 만들기는 오류 목록 창에서 수행할 수 있는 단순 프로시저입니다.|-   [팀 프로젝트 체크 인 정책 사용 하 여 코드 품질 향상](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)<br />-   [방법: 코드 프로젝트 규칙 집합을 팀 프로젝트 체크 인 정책과 동기화](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)<br />-   [방법: 관리 코드 오류에 대 한 작업 항목 만들기](../code-quality/how-to-create-a-work-item-for-a-managed-code-defect.md)|
