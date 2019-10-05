---
title: 코드 분석 체크 인 정책 만들기 및 사용 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: 3fa5a849-e05f-4e31-8ba3-b014c889d94d
caps.latest.revision: 41
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3a8015eb672e87431a1d225221ff2321c41e041a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697047"
---
# <a name="creating-and-using-code-analysis-check-in-policies"></a>코드 분석 체크 인 정책 만들기 및 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Team Foundation 버전 제어 (TFVC)를 사용 하면.NET Framework 및 네이티브 코드 분석 체크 인 정책을 만들 수 있습니다 (C /C++) 코드를 팀 프로젝트의 프로젝트입니다. 제어 코드 베이스에 체크 인 된 코드의 품질을 개선 하는 코드 분석 체크 인 정책에 따라 사용할 수 있습니다.  
  
 정책을 로컬 빌드가 최신 및 가장 최근의 소스 파일에 대해 코드 분석이 실행 된 경우에 전달 합니다. 최소한 코드 프로젝트에서 사용 되는 코드 분석 규칙 팀 프로젝트 체크 인 정책에 정의 된 것과 동일한 규칙을 포함 해야 합니다. 팀 프로젝트 설정에서 오류로 지정 된 규칙 코드 프로젝트에서 오류로 지정 해야 합니다.  
  
> [!IMPORTANT]
> 코드 분석 체크 인 정책은 웹 사이트 프로젝트에 적용할 수 없습니다. 웹 응용 프로그램 프로젝트에 적용할 수 있습니다.  
  
 팀 프로젝트 설정을 사용 하 여 코드 분석 체크 인 정책을 만들 [!INCLUDE[esprscc](../includes/esprscc-md.md)]합니다. 체크 인 정책에 지정 되 고, 팀 프로젝트에 적용 되지만 코드 분석 실행 구성 되 고 로컬 개발 컴퓨터에서 개별 코드 프로젝트에 대해 실행 합니다. 이 섹션에는 팀 프로젝트에 대 한 코드 분석 체크 인 정책을 지정 하는 방법과 관리 코드에 대 한 사용자 지정 코드 분석 정책을 구현 하는 방법을 설명 합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [방법: 표준 코드 분석 체크 인 정책 만들기 또는 업데이트](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)  
 설정 하 고 팀 프로젝트에 대 한 코드 분석 정책을 수정 하는 데 사용할 수 있는 단계를 설명 합니다.  
  
 [관리 코드에 대한 사용자 지정 체크 인 정책 구현](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)  
 사용 하 여 사용자 지정 규칙 집합을 팀 프로젝트 체크 인 정책에 대 한 체크 인 정책을 사용 하 여 팀 프로젝트의 코드 프로젝트를 동기화 하는 단계를 설명 합니다.  
  
 [코드 분석 체크 인 정책에 대한 버전 호환성](../code-quality/version-compatibility-for-code-analysis-check-in-policies.md)  
 버전 간의 코드 분석 체크 인 호환성 문제에 설명 [!INCLUDE[vstsLong](../includes/vstslong-md.md)]합니다.  
  
 [방법: 코드 분석 사전 사용자 지정](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
 코드 분석 명명 규칙에서 참조 되는 사전에 단어 및 토큰을 추가 하는 방법에 설명 합니다.  
  
## <a name="related-sections"></a>관련 단원  
 [품질 게이트 설정 및 적용](https://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)  
  
 [팀 프로젝트 체크 인 정책을 사용하여 코드 품질 향상](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)
