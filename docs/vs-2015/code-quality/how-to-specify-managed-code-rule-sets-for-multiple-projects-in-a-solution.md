---
title: '방법: 솔루션의 여러 프로젝트에 대 한 관리 코드 규칙 집합 지정 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.solution
ms.assetid: 92dc3250-a010-4396-b515-f03a0b30cd2a
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 555f8cb0ace4386a3fba7730980295dc16e58b2a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63426667"
---
# <a name="how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution"></a>방법: 솔루션의 여러 프로젝트에 대 한 관리 코드 규칙 집합 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

솔루션의 관리 되는 모든 프로젝트는 Microsoft 최소 권장 규칙 코드 분석을 할당 하는 데 기본적으로 *규칙 집합*합니다. 솔루션에 대 한 속성 대화 상자에서 솔루션의 프로젝트에 할당 되는 규칙 집합을 변경할 수 있습니다.  
  
> [!NOTE]
> 기본적으로 코드 분석 프로젝트를 빌드 단계 실행 되지 않습니다. 분석을 사용 하도록 코드를 빌드 단계를 참조 하세요. [방법: 관리 코드 프로젝트에 대 한 코드 분석 구성](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)합니다.  
  
### <a name="to-specify-a-rule-set-for-multiple-projects-in-a-managed-code--solution"></a>규칙을 지정 하는 관리 코드 솔루션의 여러 프로젝트에 대 한 설정  
  
1. [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]합니다. [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] 또는 [!INCLUDE[vsPro](../includes/vspro-md.md)]에서 솔루션을 엽니다.  
  
2. 에 **분석** 메뉴에서 클릭 **솔루션에 대 한 코드 분석 구성**합니다.  
  
3. 필요한 경우 확장 **공용 속성**를 클릭 하 고 **코드 분석 설정**합니다.  
  
4. 하나 이상의 프로젝트에 대해 설정 하는 규칙을 지정할 수 있습니다.  
  
    - 개별 프로젝트에 대해 설정 하는 규칙을 지정 하려면 프로젝트 이름을 클릭 합니다.  
  
    - 여러 프로젝트를 설정 하는 규칙을 지정 하려면 ctrl 키를 누른 하 고 프로젝트 이름을 클릭 합니다.  
  
    - 솔루션의 모든 프로젝트를 지정 하려면 shift 키 및 프로젝트 목록에서 클릭 합니다.  
  
5. 클릭 합니다 **규칙 집합** 프로젝트 및 적용 하려는 규칙의 이름을 설정 하는 클릭 한 다음의 필드입니다.
