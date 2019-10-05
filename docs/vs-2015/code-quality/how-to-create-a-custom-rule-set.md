---
title: '방법: 사용자 지정 규칙 집합 만들기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- Development Edition, rule sets
ms.assetid: bcc42508-9592-4802-9f66-a50111641d73
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 909242aaf8dd4caaee7af75e40554aaff648df68
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201361"
---
# <a name="how-to-create-a-custom-rule-set"></a>방법: 사용자 지정 규칙 집합 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsUltShort](../includes/vsultshort-md.md)], [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)], 및 [!INCLUDE[vsPro](../includes/vspro-md.md)]를 만들고 사용자 지정을 수정할 수 있습니다 *규칙 집합* 코드 분석을 사용 하 여 연결 된 특정 프로젝트 요구 사항에 맞게 합니다. 사용자 지정 규칙 집합을 만들려면, 하나를 열면 또는 더 많은 표준 규칙 규칙 집합 편집기에서 설정 합니다. 다음 추가 하거나 특정 규칙을 제거할 수 있으며 코드 분석 규칙을 위반 했습니다 결정 하는 경우 발생 하는 동작을 변경할 수 있습니다.  
  
 새 사용자 지정 규칙 집합을 만들려면 새 파일 이름을 사용 하 여 저장 합니다. 사용자 지정 규칙 집합을 프로젝트에 자동으로 할당 됩니다.  
  
## <a name="opening-the-rule-set-editor"></a>열 규칙 집합 편집기  
  
#### <a name="to-open-an-empty-rule-set-file-in-the-rule-set-editor"></a>빈 열려는 규칙 규칙 집합 편집기에서 파일을 설정  
  
1. 에 **파일** 의 메뉴 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]를 가리킨 **새로 만들기** 클릭 하 고 **파일**합니다.  
  
2. 에 **새 파일** 대화 상자에서 클릭 **일반** 에 **설치 된 템플릿** 목록 및 선택한 **코드 분석 규칙 집합**합니다.  
  
3. 규칙 집합 편집기가 나타납니다. 규칙이 없으므로 편집기 목록에서 선택 됩니다.  
  
#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>단일 기존 규칙 집합에서 사용자 지정 규칙을 만들려면  
  
1. 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 선택한 **속성**합니다.  
  
2. 에 **속성** 탭을 클릭 **코드 분석**합니다.  
  
3. 에 **규칙 집합** 드롭 다운 목록에서 다음 중 하나를 수행 합니다.  
  
   - 사용자 지정 하려는 규칙 집합을 선택 합니다.  
  
     \- 또는 -  
  
   - 선택  **\<찾아보기... >** 목록에 없는 기존 규칙 집합을 지정 하려면.  
  
4. 클릭 **열고** 규칙 규칙 집합 편집기에 표시를 합니다.  
  
#### <a name="to-create-a-custom-rule-set-from-multiple-existing-rule-sets"></a>사용자 지정 규칙을 만드는 여러 기존 규칙 집합에서 설정  
  
1. 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 선택한 **속성**합니다.  
  
2. 에 **속성** 탭을 클릭 **코드 분석**합니다.  
  
3. 선택  **\<여러 규칙 집합 선택 >** 에서 **이 규칙 집합 실행**합니다.  
  
4. 에 **추가 또는 제거할 규칙 집합** 대화 상자에서 규칙 집합에 새 규칙 집합을 기본 하 고 클릭 하려는 **확인**합니다.  
  
5. 새 규칙 집합을 저장 합니다.  
  
     새 규칙 집합의 이름이 선택 되는 **이 규칙 집합 실행** 목록입니다. 다음 단계에서 규칙 집합의 표시 이름을 변경할 수 있습니다.  
  
6. (선택 사항) 규칙 집합의 표시 이름을 변경 하는 **뷰** 메뉴에서 클릭 **속성 창**합니다. 에 표시 이름을 입력 합니다 **이름을** 상자입니다.  
  
7. 추가할 제거 또는 새 규칙 집합에 있는 특정 코드 분석 규칙을 수정, 클릭 **열려**합니다.  
  
## <a name="modifying-a-rule-set"></a>규칙 집합을 수정합니다.  
  
#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>규칙을 수정 하려면 규칙 집합 편집기에서 설정  
  
- 규칙 집합의 표시 이름을 변경 하는 **뷰** 메뉴에서 클릭 **속성 창**합니다. 표시 이름을 입력 합니다 **이름을** 상자입니다. 표시 이름을 파일 이름에서 다를 수 있는지 확인 합니다.  
  
- 사용자 지정 규칙 집합에 그룹의 모든 규칙을 추가할 그룹의 확인란을 선택 합니다. 그룹의 모든 규칙을 제거 하려면 확인란의 선택을 취소 합니다.  
  
- 특정 규칙을 사용자 지정 규칙 집합을 추가 하려면 규칙의 확인란을 선택 합니다. 규칙 집합에서 규칙을 제거 하려면 확인란의 선택을 취소 합니다.  
  
- 코드 분석에서 규칙이 위반 될 때 수행할 동작을 변경 하려면 클릭 합니다 **동작** 규칙에 대 한 필드를 다음 값 중 하나를 선택 합니다.  
  
     **경고** -경고를 생성 합니다.  
  
     **오류** -오류를 생성 합니다.  
  
     **None** -규칙을 사용 하지 않도록 설정 합니다. 이 작업을 규칙 집합에서 규칙을 제거 하는 것 같습니다.  
  
## <a name="changing-the-rule-set-editor-display"></a>편집기 표시를 설정 하는 규칙 변경  
  
#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>그룹화, 필터링 또는 규칙을 사용 하 여 규칙 집합 편집기에서 필드를 변경 하려면 편집기 도구 모음 설정  
  
- 모든 그룹의 규칙을 확장 하려면 클릭 **모두 확장**합니다.  
  
- 모든 그룹의 규칙을 축소 하려면 클릭 **모두 축소**합니다.  
  
- 규칙에서 그룹화 되는 필드를 변경 하려면 필드를 선택 합니다 **Group By** 목록입니다. 그룹화 되지 않은 규칙을 표시 하려면 선택  **\<없음 >** 합니다.  
  
- 를 추가 하거나 규칙 열의 필드를 제거 하려면 클릭 **열 옵션**합니다.  
  
- 현재 솔루션에 적용 되지 않는 규칙을 숨기려면 **현재 솔루션에 적용 되지 않는 규칙 숨기기**합니다.  
  
- 오류 작업이 할당 되는 규칙 표시 / 숨김을 전환 하려면 클릭 **코드 분석 오류를 생성할 수 있는 규칙 표시**합니다.  
  
- 경고 작업이 할당 되어 있는 규칙 표시 / 숨김을 전환 하려면 클릭 **코드 분석 경고를 생성할 수 있는 규칙 표시**합니다.  
  
- 할당 된 규칙 표시 / 숨김을 전환 하는 **None** 작업을 클릭 **활성화 되지 않은 규칙 표시**합니다.  
  
- 를 추가 하거나 Microsoft 기본 규칙 집합을 현재 규칙 집합을 제거 하려면 클릭 **자식 규칙 집합을 추가 또는 제거**합니다.  
  
## <a name="see-also"></a>참고 항목  
 [방법: 관리 코드 프로젝트에 대 한 코드 분석 구성](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
 [코드 분석 규칙 집합 참조](../code-quality/code-analysis-rule-set-reference.md)
