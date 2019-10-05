---
title: '방법: 규칙 기반 UI 컨텍스트를 사용 하 여 확장에 대 한 | Microsoft Docs'
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
caps.latest.revision: 8
ms.author: gregvanl
ms.openlocfilehash: ccdba95816d77e5282e978d508da581d9240ef06
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62425751"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>방법: Visual Studio 확장에 대해 규칙 기반 UI 컨텍스트 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에서는 특정 하는 경우 Vspackage 로드가 잘 알려진 <xref:Microsoft.VisualStudio.Shell.UIContext>가 활성화 됩니다. 그러나 이러한 UI 컨텍스트 되지 매우 정밀, 세분화 된 종료 확장 작성자가 선택 되지 않지만 지점 앞를 활성화 하는 사용 가능한 UI 컨텍스트를 선택 합니다. 그리고 원한다 VSPackage를 로드 합니다. 잘 알려진 UI 컨텍스트의 목록을 참조 하세요. <xref:Microsoft.VisualStudio.Shell.KnownUIContexts>합니다.

 패키지를 로드 성능 영향을 미칠 수 있습니다 및 모범 사례 없는 필요할 것 보다 더 빨리 로드 하기. Visual Studio 2015 규칙 기반 UI 컨텍스트를 확장 작성자는 UI 컨텍스트의 활성화 되 고 연결된 Vspackage 로드 정확한 조건을 정의할 수 있는 메커니즘의 개념이 도입 되었습니다.

## <a name="rule-based-ui-context"></a>규칙 기반 UI 컨텍스트
 새 UI 컨텍스트 (GUID) "규칙" 구성 되며 하나 이상의 "단어"를 참조 하는 부울 식을 결합 하 여 논리적 "and", "또는", "not" 작업 합니다. "조건" 런타임에 동적으로 평가 됩니다 및 용어 변경 내용을 때마다 식을 다시 평가 됩니다. 식이 true 이면 연결 된 UI 컨텍스트 활성화 됩니다. 그렇지 않으면 UI 컨텍스트가 de-activated 되었습니다.

 규칙 기반 UI 컨텍스트는 여러 가지 방법으로 사용할 수 있습니다.

1. 명령 및 도구 창에 대 한 표시 유형 제약 조건을 지정 합니다. UI 컨텍스트 규칙이 만족 될 때까지 명령/도구 창을 숨길 수 있습니다.

2. 자동으로 로드 제약 조건: 규칙이 충족 될 경우에 자동 로드 패키지

3. 지연 된 작업: 지정된 된 간격에 전달 하 고 규칙에 부합 함 계속 될 때까지 로드를 지연 합니다.

   모든 Visual Studio 확장에 의해 메커니즘을 사용할 수 있습니다.

## <a name="create-a-rule-based-ui-context"></a>규칙 기반 UI 컨텍스트 만들기
 라는 TestPackage ".config" 확장명을 가진 파일에만 적용 되는 메뉴 명령을 제공 하는 확장 있다고 가정 합니다. VS2015를 하기 전에 가장 적합 한 옵션 TestPackage 로드 된 경우 <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> UI 컨텍스트의 활성화 되었습니다. 이 로드 된 솔루션도.config 파일이 없고 있으므로 효율적이 고 하지 않습니다. 알려주세요 참조 규칙 기반 UI 컨텍스트를 사용 하 여 UI 컨텍스트의 경우.config 확장명을 가진 파일에만 활성화할 수 있습니다을 선택 하는 방법과 해당 UI 컨텍스트에서 활성화 되 면 TestPackage 로드 합니다.

1. 새 UIContext GUID를 정의 하 고 VSPackage 클래스에 추가 <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> 고 <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>입니다.

    예를 들어 새 UIContext 가정 "UIContextGuid" 추가 됩니다. 만든 GUID (도구를 클릭 하 여 GUID를 만들 수 있습니다-> guid 만들기) "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B" 됩니다. 추가한 다음 패키지 클래스 내에서:

   ```csharp
   public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";
   ```

    특성에 대해 다음을 추가 합니다. (이러한 특성의 세부 정보에 대해서는 나중)

   ```csharp
   [ProvideAutoLoad(TestPackage.UIContextGuid)]
   [ProvideUIContextRule(TestPackage.UIContextGuid,
       name: "Test auto load",
       expression: "DotConfig",
       termNames: new[] { "DotConfig" },
       termValues: new[] { "HierSingleSelectionName:.config$" })]
   ```

    이러한 메타 데이터는 새 UIContext GUID (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) 및 단일 용어에 "DotConfig"를 참조 하는 식을 정의 합니다. 정규식 패턴과 일치 하는 이름이 활성 계층 구조에서 현재 선택한 때마다 true로 평가 되는 "DotConfig" 용어 "\\.config$" (".config"로 끝나는). (기본값) 디버깅에 유용한 규칙에 대 한 선택적인 이름을 정의합니다.

    특성의 값은 나중에 빌드 시간 중에 생성 된 pkgdef에 추가 됩니다.

2. TestPackage의 명령에 대 한 VSCT 파일에서 적절 한 명령에 "DynamicVisibility" 플래그를 추가 합니다.

   ```xml
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

3. VSCT의 표시 유형 섹션에서는 새 UIContext # 1에 정의 된 GUID 적절 한 명령을 연결 합니다.

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="guidTestUIContext"/>
   </VisibilityConstraints>
   ```

4. Symbols 섹션에는 UIContext의 정의 추가 합니다.

   ```xml
   <GuidSymbol name="guidTestUIContext" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />
   ```

    이제 솔루션 탐색기에서 선택한 항목은 ".config" 파일 및 이러한 명령 중 하나를 선택할 때까지 패키지를 로드할 수는 경우에 *.config 파일에 대 한 상황에 맞는 메뉴 명령을 표시 됩니다.

   다음으로, 패키지만 때 기대 하는 로드를 확인 하려면 디버거를 사용해 보겠습니다. 디버깅 하려면 TestPackage:

5. 중단점을 설정 합니다 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 메서드.

6. TestPackage 빌드하고 디버깅을 시작 합니다.

7. 프로젝트를 만들거나 엽니다.

8. 이외의.config 확장명을 가진 모든 파일을 선택 합니다. 중단점이 적중 되지 해야 합니다.

9. App.Config 파일을 선택 합니다.

   TestPackage 로드 하 고 중단점에서 중지 됩니다.

## <a name="adding-more-rules-for-ui-context"></a>UI 컨텍스트에 대 한 자세한 규칙을 추가합니다.
 UI 상황에 맞는 규칙 부울 식 되므로 UI 컨텍스트에 대 한 더 제한적인된 규칙을 추가할 수 있습니다. 예를 들어, 위의 UI 컨텍스트에서 규칙이 프로젝트와 솔루션을 로드할 때만 적용 되도록 지정할 수 있습니다. 이러한 방식으로 명령을 열고 ".config" 파일을 프로젝트의 일부가 아니라 독립 실행형 파일로 표시 되지 않습니다.

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "(SingleProject | MultipleProjects) & DotConfig",
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]
```

 이제 식이 다음 세 가지 용어를 참조합니다. 처음 두 용어 "SingleProject" 및 "MultipleProjects" (해당 Guid)로 알려진 다른 UI 컨텍스트를 가리킵니다. 세 번째 용어 "DotConfig" 앞서 정의한 규칙 기반 UI 컨텍스트로 사용 됩니다.

## <a name="delayed-activation"></a>지연 된 활성화
 규칙에는 선택 사항 "지연" 있을 수 있습니다. 지연 시간을 밀리초 단위로 지정 됩니다. 있는 경우 활성화 또는 비활성화는 시간 간격으로 지연 될 규칙의 UI 컨텍스트의 지연 발생 합니다. 규칙 변경 내용을 지연 간격 이전인을 백업 하는 경우 아무 변화가 없습니다. 이 메커니즘은 "분산" 타이머 또는 유휴 상태 알림을 등록 하지 않고 일회 초기화 특히 초기화 단계에 사용할 수 있습니다.

 예를 들어 100 밀리초의 지연이 할 테스트 로드 규칙을 지정할 수 있습니다.

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "DotConfig",
    termNames: new[] { "DotConfig" },
    termValues: new[] { "HierSingleSelectionName:.config$" },
    delay: 100)]
```

## <a name="term-types"></a>용어 유형
 다양 한 유형의 용어 지원 되는 다음과 같습니다.

|||
|-|-|
|{nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn}|GUID는 UI 컨텍스트를 가리킵니다. 용어 UI 컨텍스트가 활성 상태이 고 false이 고, 그렇지 때마다 true가 됩니다.|
|HierSingleSelectionName:\<pattern>|용어 활성 계층 구조에서 선택 항목은 단일 항목 및 선택된 된 항목의 이름을 "패턴"에서 제공 하 여.Net 정규식과 일치 될 때마다 true가 됩니다.|
|UserSettingsStoreQuery:\<query>|"query" 0이 아닌 값으로 평가 되어야 하는 사용자 설정 저장소에 전체 경로 나타냅니다. 쿼리 "collection"과 "propertyName" 마지막 슬래시에서 분할 됩니다.|
|ConfigSettingsStoreQuery:\<query>|"query" 0이 아닌 값으로 평가 되어야 하는 구성 설정 저장소에 전체 경로 나타냅니다. 쿼리 "collection"과 "propertyName" 마지막 슬래시에서 분할 됩니다.|
|ActiveProjectFlavor:\<projectTypeGuid>|현재 선택한 프로젝트 버전이 지정 된 때마다 용어 true 됩니다 (집계) 해당된 프로젝트 형식 GUID 일치 하는 버전 및 합니다.|
|ActiveEditorContentType:\<contentType>|용어 선택한 문서에 지정된 된 콘텐츠 형식 사용 하 여 텍스트 편집기는 경우 true가 됩니다.|
|ActiveProjectCapability:\<Expression>|용어 활성 프로젝트 기능에 제공 된 식과 일치 하는 경우 그렇습니다. 식을 VB와 같이 수 &#124; CSharp|
|SolutionHasProjectCapability:\<Expression>|위의 유사 하지만 용어 솔루션에는 로드 된 프로젝트 식에 일치 하는 때도 마찬가지입니다.|
|SolutionHasProjectFlavor:\<projectTypeGuid>|용어 (집계) 지원 되는 프로젝트에 솔루션과 해당된 프로젝트 형식 GUID 일치 하는 버전 때마다 true가 됩니다.|

## <a name="compatibility-with-cross-version-extension"></a>버전 간 확장을 사용 하 여 호환성
 규칙 기반된 UI 컨텍스트는 Visual Studio 2015의 새로운 기능 및 이전 버전으로 이식 되지 않은 것입니다. 이 문제 및 이전 버전의 경우 Visual Studio 2013의 자동 로드 해야 하지만 방지 되 고 자동 로드 된 Visual Studio 2015의 규칙 기반 UI 컨텍스트를 활용할 수 있는 Visual Studio의 여러 버전을 대상으로 하는 확장/패키지를 만듭니다.

 이러한 패키지를 지원 하기 위해 레지스트리에서 AutoLoadPackages 항목 이제 Visual Studio 2015 이상 항목을 건너뛰어야 함을 나타내기 위해 해당 값 필드에서 플래그를 제공할 수 있습니다. 플래그 옵션을 추가 하 여 이렇게 <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>합니다. Vspackage 이제 추가할 수 있습니다 **SkipWhenUIContextRulesActive** 옵션을 해당 <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> 이상 Visual Studio 2015에서 항목을 무시할지를 나타내는 특성입니다.

## <a name="extensible-ui-context-rules"></a>확장 가능한 UI 상황에 맞는 규칙
 경우에 따라 패키지 정적 UI 상황에 맞는 규칙을 사용할 수 없습니다. 예를 들어 패키지는 명령 상태는 형식을 기반으로 편집기 가져온된 MEF 공급자에서 지원 되는 확장성을 지원 해야 합니다. 현재 편집 형식을 지 원하는 확장인 경우 명령이 활성화 됩니다. 이러한 경우 패키지 자체 용어 확장을 사용할 수 있는 MEF에 따라 변경 되므로 정적 UI 상황에 맞는 규칙을 사용할 수 없습니다.

 이러한 패키지를 지원 하기 위해 규칙 기반 UI 컨텍스트는 하드 코드 된 식 지원 "*" 모든 아래의 조건을 사용 하 여 참여할 수를 나타내는 또는 합니다. 이 컨텍스트에 명령 상태를 연결 및 마스터 패키지 정의 알려진된 규칙 기반 UI 컨텍스트 수 있습니다. 그런 다음 마스터 패키지를 대상으로 하는 모든 MEF 확장 마스터 식이나 다른 용어를 영향을 주지 않고 지원 되는 편집기에 대 한 해당 용어를 추가할 수 있습니다.

 생성자 <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> 설명서에는 확장 가능한 UI 상황에 맞는 규칙에 대 한 구문을 보여 줍니다.
