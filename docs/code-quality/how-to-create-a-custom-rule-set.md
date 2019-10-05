---
title: 사용자 지정 코드 분석 규칙 집합 만들기
ms.date: 11/02/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- rule sets
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f2f642ea8e41e4a9ccf2b35f432df528fc5e81d0
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65676560"
---
# <a name="customize-a-rule-set"></a>규칙 집합을 사용자 지정

코드 분석을 위한 특정 프로젝트 요구 사항에 맞게 설정 사용자 지정 규칙을 만들 수 있습니다.

## <a name="create-a-custom-rule-set-from-an-existing-rule-set"></a>기존 규칙 집합을 설정 하는 사용자 지정 규칙 만들기

사용자 지정 규칙 집합을 만들려면, 기본 제공 규칙 집합에 열 수 있습니다 합니다 **규칙 집합 편집기**합니다. 여기에서 추가 하거나 특정 규칙을 제거할 수 있습니다 및 규칙이 위반 될 때 발생 하는 동작을 변경할 수 있습니다&mdash;예를 들어, 경고 또는 오류를 표시 합니다.

1. **솔루션 탐색기**프로젝트를 마우스 오른쪽 단추로 클릭 하 고 선택한 **속성**합니다.

2. 에 **속성** 페이지를 선택 합니다 **코드 분석** 탭 합니다.

3. 에 **이 규칙 집합 실행** 드롭 다운 목록에서 다음 중 하나를 수행 합니다.

   - 사용자 지정 하려는 규칙 집합을 선택 합니다.

     \- 또는 -

   - 선택  **\<찾아보기... >** 목록에 없는 기존 규칙 집합을 지정 하려면.

4. 선택 **열고** 규칙 규칙 집합 편집기에 표시를 합니다.

> [!NOTE]
> .NET Core 또는.NET Standard 프로젝트에 있는 경우 프로세스는 방법은 약간 다릅니다. 있기 때문에 없습니다 **코드 분석** 속성 탭 합니다. 다음 단계에 따라 [프로젝트를 설정 하 고 활성 규칙 집합으로 설정 하는 미리 정의 된 규칙을 복사](analyzer-rule-sets.md)합니다. 규칙 집합을 복사한 후 수 있습니다 [규칙 집합 편집기는 Visual Studio에서 편집](working-in-the-code-analysis-rule-set-editor.md) 에서 열어 **솔루션 탐색기**합니다.

## <a name="create-a-new-rule-set"></a>새 규칙 집합 만들기

새 규칙 집합 파일을 만들어야 합니다 **새 파일** 대화:

1. 선택 **파일** > **새로 만들기** > **파일**를 누르거나 **Ctrl**+**N**.

2. 에 **새 파일** 대화 상자를 선택 합니다 **일반** 왼쪽의 범주 선택한 후 **코드 분석 규칙 집합**.

3. **열기**를 선택합니다.

   새 *.ruleset* 파일이 규칙 집합 편집기에서 열립니다.

## <a name="create-a-custom-rule-set-from-multiple-rule-sets"></a>사용자 지정 규칙 집합에서 여러 규칙 집합

> [!NOTE]
> 다음 절차 않은.NET Core 프로젝트에 적용 되지 않습니다는 **코드 분석** 속성 탭 합니다.

1. **솔루션 탐색기**프로젝트를 마우스 오른쪽 단추로 클릭 하 고 선택한 **속성**합니다.

2. 에 **속성** 페이지를 선택 합니다 **코드 분석** 탭 합니다.

3. 선택  **\<여러 규칙 집합 선택 >** 에서 **이 규칙 집합 실행**합니다.

4. 에 **추가 또는 제거할 규칙 집합** 대화 상자에서 규칙 집합 선택 하려면 새 규칙 집합에 포함 합니다.

   ![추가 또는 제거 규칙 집합 대화 상자](media/add-remove-rule-sets.png)

5. 선택 **다른 이름으로 저장**에 대 한 이름을 입력 합니다 *.ruleset* 파일을 선택한 후 **저장**합니다.

   새 규칙 집합을 선택 합니다 **이 규칙 집합 실행** 목록입니다.

6. 선택 **엽니다** 를 규칙 집합 편집기에서 설정 하 고 새 규칙을 엽니다.

## <a name="rule-precedence"></a>규칙 우선 순위

- 동일한 규칙을 나열 된 두 경우 또는 번 더 다양 한 심각도 사용 하 여 설정 하는 규칙에서 컴파일러 오류가 발생 합니다. 예를 들어:

   ```xml
   <RuleSet Name="Rules for ClassLibrary21" Description="Code analysis rules for ClassLibrary21.csproj." ToolsVersion="15.0">
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Warning" />
       <Rule Id="CA1021" Action="Error" />
     </Rules>
   </RuleSet>
   ```

- 동일한 규칙을 나열 된 두 이거나 번 더 사용 하 여 설정 규칙에는 *동일한* 심각도에 다음 경고가 표시 될 수 있습니다 합니다 **오류 목록**:

   **CA0063 : 규칙 집합 파일을 로드 하지 못했습니다 '\[에].ruleset ' 또는 해당 종속 규칙 중 하나가 파일을 설정 합니다. 파일 규칙 집합 스키마에 맞지 않습니다.**

- 규칙 집합을 사용 하 여 설정 하는 자식 규칙을 포함 하는 경우는 **Include** 태그 및 자식 및 부모 규칙 집합에는 모두 동일한 규칙을 나열 하지만 서로 다른 심각도 사용 하 여 다음에서 부모 규칙 집합 심각도 우선 적용 됩니다. 예를 들어:

   ```xml
   <!-- Parent rule set -->
   <?xml version="1.0" encoding="utf-8"?>
   <RuleSet Name="Rules for ClassLibrary21" Description="Code analysis rules for ClassLibrary21.csproj." ToolsVersion="15.0">
     <Include Path="classlibrary_child.ruleset" Action="Default" />
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Warning" /> <!-- Overrides CA1021 severity from child rule set -->
     </Rules>
   </RuleSet>

   <!-- Child rule set -->
   <?xml version="1.0" encoding="utf-8"?>
   <RuleSet Name="Rules from child" Description="Code analysis rules from child." ToolsVersion="15.0">
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Error" />
     </Rules>
   </RuleSet>
   ```

## <a name="name-and-description"></a>이름 및 설명

편집기에서 열려 있는 규칙 집합의 표시 이름을 변경 하려면 합니다 **속성** 를 선택 하 여 창 **뷰** > **속성 창** 메뉴 모음에서. 표시 이름을 입력 합니다 **이름을** 상자입니다. 또한 규칙 집합에 대 한 설명을 입력할 수 있습니다.

## <a name="next-steps"></a>다음 단계

규칙 집합을 설정 했으므로 다음 단계를 추가 하거나 규칙을 제거 하거나 규칙 위반의 심각도 수정 하 여 규칙을 사용자 지정할 경우

> [!div class="nextstepaction"]
> [규칙 집합 편집기에서 규칙 수정](../code-quality/working-in-the-code-analysis-rule-set-editor.md)

## <a name="see-also"></a>참고자료

- [방법: 관리 코드 프로젝트에 대 한 코드 분석 구성](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)
- [코드 분석 규칙 집합 참조](../code-quality/rule-set-reference.md)