---
title: 텍스트 템플릿에서 ModelBus 사용 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 5ed3e5c2-f60f-43c7-8ef4-754f511339c5
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 672efc49d712d9cd800bf53a2ca8487c96d502b6
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68871689"
---
# <a name="using-visual-studio-modelbus-in-a-text-template"></a>텍스트 템플릿에서 Visual Studio ModelBus 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ModelBus 참조를 포함 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 하는 모델을 읽는 텍스트 템플릿을 작성 하는 경우 참조를 확인 하 여 대상 모델에 액세스할 수 있습니다. 이 경우 텍스트 템플릿 및 참조 도메인 특정 언어 (Dsl)를 적용 해야 할 수도 있습니다.

- 참조의 대상이 되는 DSL 텍스트 템플릿에서 액세스에 대해 구성 된 ModelBus 어댑터가 있어야 합니다. 또한 다른 코드에서 DSL을 액세스 하는 경우 다시 구성 된 어댑터는 표준 ModelBus 어댑터 외에도 필요 합니다.

     어댑터 관리자는 [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)) 에서 상속 해야 하며 특성 `[HostSpecific(HostName)]`을 포함 해야 합니다.

- 템플릿은 [Modelbusenabledtexttransformation](/previous-versions/ee844263(v=vs.140))함께 상속 해야 합니다.

> [!NOTE]
> ModelBus 참조를 포함 하지 않는 DSL 모델 읽기 하려는 경우에 DSL 프로젝트에서 생성 된 지시문 프로세서를 사용할 수 있습니다. 자세한 내용은 [텍스트 템플릿에서 모델에 액세스](../modeling/accessing-models-from-text-templates.md)합니다.

 텍스트 템플릿에 대 한 자세한 내용은 참조 하세요. [T4 텍스트 템플릿을 사용 하 여 디자인 타임 코드 생성](../modeling/design-time-code-generation-by-using-t4-text-templates.md)합니다.

## <a name="creating-a-model-bus-adapter-for-access-from-text-templates"></a>텍스트 템플릿에서 액세스에 대 한 모델 버스 어댑터를 만들기
 텍스트 템플릿에서 ModelBus 참조를 해결 하려면 대상 DSL에 호환 되는 어댑터가 있어야 합니다. 텍스트 템플릿은 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 문서 편집기와 별도의 AppDomain에서 실행 되므로 어댑터는 DTE를 통해 액세스 하는 대신 모델을 로드 해야 합니다.

#### <a name="to-create-a-modelbus-adapter-that-is-compatible-with-text-templates"></a>텍스트 템플릿을 사용 하 여 호환 되는 ModelBus 어댑터를 만들려면

1. 대상 DSL 솔루션에 없는 경우는 **ModelBusAdapter** 프로젝트에서 Modelbus 확장 마법사를 사용 하 여 만듭니다.

    1. 아직 수행 하지 않은 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 경우 ModelBus 확장을 다운로드 하 여 설치 합니다. 자세한 내용은 [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=185579)합니다.

    2. DSL 정의 파일을 엽니다. 디자인 화면을 마우스 오른쪽 단추로 누른 **Modelbus**합니다.

    3. 대화 상자에서 선택 **ModelBus에이 DSL 표시 하려는**합니다. 이 DSL 모델에 표시 하 고 다른 Dsl에 대 한 참조를 사용 하려는 경우 두 옵션 모두를 선택할 수 있습니다.

    4. **확인**을 클릭합니다. "ModelBusAdapter"라는 새 프로젝트가 DSL 솔루션에 추가됩니다.

    5. 클릭 **모든 템플릿 변환**합니다.

    6. 솔루션을 다시 빌드합니다.

2. 및 명령 등의 다른 코드 둘 다 텍스트 템플릿에서 DSL에 액세스 하려는 경우 중복 된 **ModelBusAdapter** 프로젝트:

    1. Windows 탐색기에서 복사 하 고 포함 된 폴더에 붙여 넣습니다 **ModelBusAdapter.csproj**합니다.

    2. 프로젝트 파일의 이름을 바꿉니다 (예를 들어 **T4ModelBusAdapter.csproj**).

    3. **솔루션 탐색기**솔루션 노드를 마우스 오른쪽 단추로 클릭, 가리킨 **추가**를 클릭 하 고 **기존 프로젝트**합니다. 새 어댑터 프로젝트를 찾습니다 **T4ModelBusAdapter.csproj**합니다.

    4. 각 `*.tt` 파일을 새 프로젝트의 네임 스페이스를 변경 합니다.

    5. 솔루션 탐색기에서 새 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 속성을 클릭 합니다. 속성 편집기에서 생성된 된 어셈블리 및 기본 네임 스페이스의 이름을 변경 합니다.

    6. DslPackage 프로젝트에서 두 어댑터 모두에 대 한 참조가 포함 되도록 새 어댑터 프로젝트에 대 한 참조를 추가 합니다.

    7. DslPackage\source.extension.tt에서 새 어댑터 프로젝트를 참조 하는 줄을 추가 합니다.

        ```
        <MefComponent>|T4ModelBusAdapter|</MefComponent>
        ```

    8. **모든 템플릿 변환** 는 솔루션을 다시 빌드합니다. 빌드 오류가 발생 해야 합니다.

3. 새 어댑터 프로젝트에서 다음 어셈블리에 대 한 참조를 추가 합니다.

    - Microsoft.VisualStudio.TextTemplating.11.0

         Microsoft.VisualStudio.TextTemplating.Modeling.11.0

4. AdapterManager.tt:

    - [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140))에서 상속 하도록 AdapterManagerBase의 선언을 변경 합니다.

         `public partial class <#= dslName =>AdapterManagerBase :`

         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`

    - 파일 끝 근처 AdapterManager 클래스 앞 HostSpecific 특성을 대체 합니다. 다음 줄을 제거 합니다.

         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`

         다음 줄을 삽입 합니다.

         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

         이 특성을 어댑터에 대 한 modelbus 소비자를 검색할 때 사용할 수 있는 어댑터 집합을 필터링 합니다.

5. **모든 템플릿 변환** 는 솔루션을 다시 빌드합니다. 빌드 오류가 발생 해야 합니다.

## <a name="writing-a-text-template-that-can-resolve-modelbus-references"></a>ModelBus 참조를 확인할 수 있는 텍스트 템플릿 작성
 일반적으로 읽고 "원본" DSL에서에서 파일을 생성 하는 템플릿으로 시작할 수도 있습니다. 에 설명 된 방식으로 원본 모델 파일을 읽을 소스 DSL 프로젝트에서 생성 된 지시문을 사용 하 여이 템플릿을 [텍스트 템플릿에서 모델에 액세스](../modeling/accessing-models-from-text-templates.md)합니다. 그러나 소스 DSL "대상" DSL ModelBus 참조를 포함합니다. 따라서 참조를 확인 및 대상 DSL에 액세스 하는 템플릿 코드를 사용 하도록 설정 하려고 합니다. 따라서 다음이 단계를 수행 하 여 템플릿을 조정 해야 합니다.

- 템플릿의 기본 클래스를 [Modelbusenabledtexttransformation](/previous-versions/ee844263(v=vs.140))으로 변경 합니다.

- 포함 `hostspecific="true"` template 지시문에 있습니다.

- ModelBus를 사용 하도록 설정 하 고 대상 DSL 및 해당 어댑터에 어셈블리 참조를 추가 합니다.

- 대상 DSL의 일부로 생성 되는 지시문이 필요가 없습니다.

```
<#@ template debug="true" hostspecific="true" language="C#"
inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>
<#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>
<#@ output extension=".txt" #>
<#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>
<#@ assembly name = "Company.TargetDsl.Dsl.dll" #>
<#@ assembly name = "Company.TargetDsl.T4ModelBusAdapter.dll" #>
<#@ assembly name = "System.Core" #>
<#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>
<#@ import namespace="Company.TargetDsl" #>
<#@ import namespace="Company.TargetDsl.T4ModelBusAdapters" #>
<#@ import namespace="System.Linq" #>
<#
  SourceModelRoot source = this.ModelRoot; // Usual access to source model.
  // In the source DSL Definition, the root element has a model reference:
  using (TargetAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as TargetAdapter)
  {if (adapter != null)
   {
      // Get the root of the target model:
      TargetRoot target = adapter.ModelRoot;
    // The source DSL Definition has a class "SourceElement" embedded under the root.
    // (Let’s assume they’re all in the same model file):
    foreach (SourceElement sourceElement in source.Elements)
    {
      // In the source DSL Definition, each SourceElement has a MBR property:
      ModelBusReference elementReference = sourceElement.ReferenceToTarget;
      // Resolve the target model element:
      TargetElement element = adapter.ResolveElementReference<TargetElement>(elementReference);
#>
     The source <#= sourceElement.Name #> is linked to: <#= element.Name #> in target model: <#= target.Name #>.
<#
    }
  }}
  // Other useful code: this.Host.ResolvePath(filename) gets an absolute filename
  // from a path that is relative to the text template.
#>

```

 이 텍스트 템플릿을 실행 하는 경우는 `SourceDsl` 파일을 로드 하는 지시문 `Sample.source`합니다. 서식 파일에서 시작 하는 모델의 요소에 액세스할 수 `this.ModelRoot`입니다. 코드는 도메인 클래스 및 해당 하는 DSL의 속성을 사용할 수 있습니다.

 또한 템플릿을 ModelBus 참조를 확인할 수 있습니다. 참조가 대상 모델을 가리키는 경우 어셈블리 지시문을 사용 하면 코드에서 해당 모델의 DSL의 도메인 클래스 및 속성을 사용할 수 있습니다.

- DSL 프로젝트에서 생성 되는 지시문을 사용 하지 않는 경우 다음 포함도 해야 합니다.

    ```
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>
    ```

- 사용 하 여 `this.ModelBus` ModelBus에 대 한 액세스를 가져오려고 합니다.

## <a name="walkthrough-testing-a-text-template-that-uses-modelbus"></a>연습: ModelBus를 사용 하는 텍스트 템플릿 테스트
 이 연습에서는 다음이 단계를 수행 합니다.

1. 두 Dsl을 생성 합니다. 한 DSL에서는 합니다 *소비자*에 `ModelBusReference` 다른 DSL을 참조할 수 있는 속성을 *공급자*.

2. 공급자의 두 ModelBus 어댑터 만들기: 텍스트 템플릿, 일반 코드에 대 한 다른 액세스에 대 한 합니다.

3. 단일 실험 프로젝트에서 Dsl의 인스턴스 모델을 만듭니다.

4. 다른 모델을 가리키도록 하나의 모델에서 도메인 속성을 설정 합니다.

5. 모델을 가리키는 열리는 두 번 클릭 처리기를 작성 합니다.

6. 첫 번째 모델을 로드, 다른 모델에 대 한 참조를 수행 하 고 다른 모델을 읽을 수 있는 텍스트 템플릿을 작성 합니다.

#### <a name="construct-a-dsl-that-is-accessible-to-modelbus"></a>DSL을 ModelBus에 액세스할 수 있는 생성

1. 새 DSL 솔루션을 만듭니다. 예를 들어 작업 흐름 솔루션 템플릿에서 선택 합니다. 언어 이름으로 `MBProvider` 및 파일 이름 확장명 ".provide"입니다.

2. DSL 정의 다이어그램에서 위쪽에 없는 다이어그램의 빈 부분을 마우스 오른쪽 단추로 클릭 하 고 클릭 **Modelbus**합니다.

   - 표시 되지 않으면 **Modelbus**를 다운로드 하 고 VMSDK ModelBus 확장을 설치 해야 합니다. VMSDK 사이트에서 찾을 수 있습니다. [시각화 및 모델링 SDK](http://go.microsoft.com/fwlink/?LinkID=185579).

3. 에 **Modelbus** 대화 상자에서 **이 Dsl을 ModelBus**를 클릭 하 고 **확인**합니다.

    새 프로젝트를 `ModelBusAdapter`를 솔루션에 추가 됩니다.

   이제 DSL 텍스트 템플릿에서 ModelBus 통해 액세스할 수 있습니다. 명령, 이벤트 처리기 또는 모델 파일 편집기의 AppDomain에서 작동 하는 모든 규칙의 코드에 대 한 참조를 해결할 수 있습니다. 그러나 텍스트 템플릿을 별도 AppDomain에서 실행 하 고 편집 하는 경우 모델에 액세스할 수 없습니다. 텍스트 템플릿에서이 DSL ModelBus 참조에 액세스 하려는 경우에 별도 ModelBusAdapter를 해야 합니다.

#### <a name="to-create-a-modelbus-adapter-that-is-configured-for-text-templates"></a>텍스트 템플릿에 대 한 구성 된 ModelBus 어댑터를 만들려면

1. Windows 탐색기에서 복사한 ModelBusAdapter.csproj 포함 된 폴더에 붙여 넣습니다.

    T4ModelBusAdapter 폴더를 이름을 지정 합니다.

    T4ModelBusAdapter.csproj 프로젝트 파일을 이름을 바꿉니다.

2. 솔루션 탐색기에서 T4ModelBusAdapter MBProvider 솔루션에 추가 합니다. 솔루션 노드를 마우스 오른쪽 **추가**를 클릭 하 고 **기존 프로젝트**합니다.

3. T4ModelBusAdapter 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 속성을 클릭 합니다. 프로젝트 속성 창에서 변경 합니다 **어셈블리 이름** 하 고 **Default Namespace** 에 `Company.MBProvider.T4ModelBusAdapters`.

4. T4ModelBusAdapter 각 *.tt 파일에서 다음과 유사한 줄 수 있도록 "T4" 네임 스페이스의 마지막 부분에 삽입 합니다.

    `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`

5. 에 `DslPackage` 프로젝트를 프로젝트 참조를 추가 `T4ModelBusAdapter`합니다.

6. DslPackage\source.extension.tt, 아래에 다음 줄 추가 `<Content>`합니다.

    `<MefComponent>|T4ModelBusAdapter|</MefComponent>`

7. `T4ModelBusAdapter` 프로젝트에서에 대 한 참조를 추가 합니다. **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**

8. Open T4ModelBusAdapter\AdapterManager.tt:

   1. AdapterManagerBase의 기본 클래스를 [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140))로 변경 합니다. 이제 파일의이 부분 다음과 같습니다.

       ```
       namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters
       {
           /// <summary>
           /// Adapter manager base class (double derived pattern) for the <#= dslName #> Designer
           /// </summary>
           public partial class <#= dslName #>AdapterManagerBase
           : Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager
           {

       ```

   2. 파일 끝 근처 AdapterManager 클래스 앞에 다음 추가 특성을 삽입 합니다.

        `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

        결과 다음과 같습니다.

       ```
       /// <summary>
       /// ModelBus modeling adapter manager for a <#= dslName #>Adapter model adapter
       /// </summary>
       [Mef::Export(typeof(DslIntegration::ModelBusAdapterManager))]
       [Mef::ExportMetadata(DslIntegration::CompositionAttributes.AdapterIdKey,<#= dslName #>Adapter.AdapterId)]
       [DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]
       [Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]
       public partial class <#= dslName #>AdapterManager : <#= dslName #>AdapterManagerBase
       {
       }

       ```

9. 클릭 **모든 템플릿 변환** 의 제목 표시줄의 솔루션 탐색기.

10. 솔루션을 다시 빌드합니다. F5 키를 클릭 합니다.

11. F5 키를 눌러 DSL이 작동 하는지 확인 합니다. 실험적 프로젝트를 열고 `Sample.provider`합니다. 실험적 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 인스턴스를 닫습니다.

    텍스트 템플릿 및 일반 코드에서이 DSL ModelBus 참조 이제 해결할 수 있습니다.

#### <a name="construct-a-dsl-with-a-modelbus-reference-domain-property"></a>DSL을 ModelBus 참조 도메인 속성 구성

1. 최소 언어 솔루션 템플릿을 사용 하 여 새 DSL을 만듭니다. MBConsumer 언어 이름을 지정 하 고 파일 이름 확장명 ".consume"을 설정 합니다.

2. DSL 프로젝트에서 MBProvider DSL 어셈블리에 대 한 참조를 추가 합니다. 마우스 오른쪽 단추로 클릭 `MBConsumer\Dsl\References` 을 클릭 한 다음 **참조 추가**합니다. 에 **찾아보기** 탭, 찾기 `MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`

    이 옵션을 사용 하면 다른 DSL을 사용 하는 코드를 만들 수 있습니다. 여러 Dsl에 대 한 참조를 만들려는 경우에 추가 합니다.

3. DSL 정의 다이어그램에서 다이어그램을 마우스 오른쪽 단추로 클릭 하 고 클릭 **ModelBus**합니다. 대화 상자에서 선택 **ModelBus를 사용 하려면이 DSL을 사용 하도록 설정**합니다.

4. 클래스의 `ExampleElement`, 새 도메인 속성을 추가할 `MBR`, 속성 창에서 해당 형식으로 설정 하 고 `ModelBusReference`입니다.

5. 다이어그램에서 도메인 속성을 마우스 오른쪽 단추로 누른 **ModelBusReference 관련 속성 편집**합니다. 대화 상자에서 선택 **모델 요소**합니다.

    다음으로 파일 대화 상자 필터를 설정 합니다.

    `Provider File|*.provide`

    뒤의 부분 문자열 "&#124;" 파일 선택 대화 상자에 대 한 필터입니다. 사용 하 여 모든 파일을 허용 하도록 설정할 수 있습니다 *.\*

    에 **모델 요소 형식** 목록 공급자 (예를 들어 Company.MBProvider.Task) DSL에서에서 하나의 자세한 이상의 도메인 클래스의 이름을 입력 합니다. 추상 클래스가 될 수 있습니다. 목록을 비워 두면 사용자는 모든 요소에 대 한 참조를 설정할 수 있습니다.

6. 대화 상자 닫기 및 **모든 템플릿 변환**합니다.

   다른 DSL에서 요소에 대 한 참조를 포함할 수 있는 DSL을 만들었습니다.

#### <a name="create-a-modelbus-reference-to-another-file-in-the-solution"></a>솔루션에서 다른 파일에 대 한 ModelBus 참조 만들기

1. MBConsumer 솔루션에서 ctrl+f5를 누릅니다. 의 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 실험적 인스턴스가 **MBConsumer\Debugging** 프로젝트에서 열립니다.

2. Sample.provide에 복사본을 추가 합니다 **MBConsumer\Debugging** 프로젝트입니다. ModelBus 참조를 동일한 솔루션에서 파일을 참조 해야 하기 때문에 이것이 필요한입니다.

   1. 디버깅 프로젝트를 마우스 오른쪽 **추가**를 클릭 하 고 **기존 항목**합니다.

   2. 에 **항목 추가** 대화 상자에서 필터를 설정 **모든 파일 (\*.\*)** .

   3. 이동할 `MBProvider\Debugging\Sample.provide` 을 클릭 한 다음 **추가**합니다.

3. `Sample.consume`를 엽니다.

4. 예제에서는 셰이프를 두 개를 클릭 하 고 속성 창에서 클릭 **[...]**  MBR 속성에서입니다. 대화 상자에서 클릭 **찾아보기** 선택한 `Sample.provide`합니다. 요소 창에서 작업 형식을 확장 하 고 요소 중 하나를 선택 합니다.

5. 파일을 저장합니다.

    (의 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]실험적 인스턴스를 아직 닫지 마세요.)

   다른 모델의 요소에 대 한 ModelBus 참조를 포함 하는 모델을 만든 것입니다.

#### <a name="resolve-a-modelbus-reference-in-a-text-template"></a>텍스트 템플릿에서 ModelBus 참조를 해결 하기

1. 실험적 인스턴스에서 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]샘플 텍스트 템플릿 파일을 엽니다. 내용을 다음과 같이 설정 합니다.

    ```
    <#@ template debug="true" hostspecific="true" language="C#"
    inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>
    <#@ MBConsumer processor="MBConsumerDirectiveProcessor" requires="fileName='Sample.consume'" #>
    <#@ output extension=".txt" #>
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>
    <#@ assembly name = "Company.MBProvider.Dsl.dll" #>
    <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>
    <#@ import namespace="Company.MBProvider" #>
    <#
      // Property provided by the Consumer directive processor:
      ExampleModel consumerModel = this.ExampleModel;
      // Iterate through Consumer model, listing the elements:
      foreach (ExampleElement element in consumerModel.Elements)
      {
    #>
       <#= element.Name #>
    <#
        if (element.MBR != null)
      using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(element.MBR))
      {
              // If we allowed multiple types or DSLs in the MBR, discover type here.
        Task task = adapter.ResolveElementReference<Task>(element.MBR);
    #>
            <#= element.Name #> is linked to Task: <#= task==null ? "(null)" : task.Name #>
    <#
          }
      }
    #>

    ```

     다음 사항을 확인합니다.

    1. 합니다 `hostSpecific` 및 `inherits` 의 특성을 `template` 지시문을 설정 해야 합니다.

    2. 소비자 모델은 해당 DSL에서 생성 된 지시문 프로세서를 통해 일반적인 방식으로 액세스 됩니다.

    3. 어셈블리 및 import 지시문 DSL 공급자 형식과 ModelBus를 액세스할 수 있어야 합니다.

    4. 많은 Mbr 동일한 모델에 연결 됩니다 있는지를 알고 있으면 CreateAdapter 한 번만 호출 하는 것이 좋습니다.

2. 템플릿을 저장하는 경우 결과 텍스트 파일이 다음과 유사한 지 확인 합니다.

    ```

    ExampleElement1
    ExampleElement2
         ExampleElement2 is linked to Task: Task2

    ```

#### <a name="resolve-a-modelbus-reference-in-a-gesture-handler"></a>제스처 처리기에 대 한 ModelBus 참조를 확인 합니다.

1. 실행 중인 경우의 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]실험적 인스턴스를 닫습니다.

2. MBConsumer\Dsl\Custom.cs 라는 이며 다음으로 해당 콘텐츠를 설정 하는 파일을 추가 합니다.

    ```

    namespace Company.MB2Consume
    {
      using Microsoft.VisualStudio.Modeling.Integration;
      using Company.MB3Provider;

      public partial class ExampleShape
      {
        public override void OnDoubleClick(Microsoft.VisualStudio.Modeling.Diagrams.DiagramPointEventArgs e)
        {
          base.OnDoubleClick(e);
          ExampleElement element = this.ModelElement as ExampleElement;
          if (element.MBR != null)
          {
            IModelBus modelbus = this.Store.GetService(typeof(SModelBus)) as IModelBus;
            using (ModelBusAdapter adapter = modelbus.CreateAdapter(element.MBR))
            {
              Task task = adapter.ResolveElementReference<Task>(element.MBR);
              // Open a window on this model:
              ModelBusView view = adapter.GetDefaultView();
              view.Show();
              view.SetSelection(element.MBR);
            }
          }
        }
      }
    }

    ```

3. Ctrl+F5를 누릅니다.

4. 실험적 인스턴스에서 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]를 엽니다 `Debugging\Sample.consume`.

5. 모양을 두 번 클릭 합니다.

     해당 요소에는 MBR을 설정한 경우 참조 되는 모델 열리고 참조 된 요소를 선택 합니다.

## <a name="see-also"></a>참고 항목
 [Visual Studio를 사용 하 여 모델 통합 Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) [코드 생성 및 T4 텍스트 템플릿](../modeling/code-generation-and-t4-text-templates.md)
