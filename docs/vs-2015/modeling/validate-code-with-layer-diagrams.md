---
title: Validate code with layer diagrams | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, validating
- validation, layer diagrams
- validation, code
- code exploration, validating
- architecture, validating
- Visual Studio Ultimate, validating code
- validation, architecture
- validation, dependencies
- MSBuild, tasks
- MSBuild, layer diagrams
- MSBuild, validating code
ms.assetid: 70cbe55d-4b33-4355-b0a7-88c770a6f75c
caps.latest.revision: 84
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 596711c5c59738d5356437bb761e80caeddfbd6b
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301356"
---
# <a name="validate-code-with-layer-diagrams"></a>레이어 다이어그램에 대해 코드 유효성 검사
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

코드가 디자인과 충돌하지 않는지 확인하기 위해 Visual Studio에서 레이어 다이어그램을 사용하여 코드의 유효성을 검사할 수 있습니다. 이 경우 다음에 도움이 됩니다.

- 코드의 종속성과 레이어 다이어그램의 종속성 사이의 충돌을 찾을 수 있습니다.

- 제안된 변경 내용의 영향을 받을 수 있는 종속성을 찾습니다.

   예를 들어 레이어 다이어그램을 편집하여 잠재적인 아키텍처 변경을 나타낸 다음, 코드의 유효성을 검사하여 영향을 받는 종속성을 확인할 수 있습니다.

- 코드를 다른 디자인으로 리팩터링 또는 마이그레이션합니다.

   코드를 다른 아키텍처로 이동할 때 아직 작업이 필요한 코드 또는 종속성을 찾을 수 있습니다.

  **Requirements**

- Visual Studio

- Team Foundation Build를 사용하여 자동으로 코드의 유효성을 검사하는 Team Foundation Build 서버의 Visual Studio

- 레이어 다이어그램을 사용하는 모델링 프로젝트가 포함된 솔루션 이 레이어 다이어그램은 유효성 검사를 하려는 Visual C# .NET 또는 Visual Basic .NET 프로젝트의 아티팩트에 연결해야 합니다. See [Create layer diagrams from your code](../modeling/create-layer-diagrams-from-your-code.md).

  이 기능을 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.

  Visual Studio의 열린 레이어 다이어그램 또는 명령 프롬프트에서 코드 유효성 검사를 수동으로 수행할 수 있습니다. 또한 로컬 빌드 또는 Team Foundation Build를 실행할 때 자동으로 코드 유효성 검사를 실행할 수도 있습니다. See [Channel 9 Video: Design and validate your architecture using layer diagrams](https://go.microsoft.com/fwlink/?LinkID=252073).

> [!IMPORTANT]
> Team Foundation Build를 사용하여 레이어 유효성 검사를 실행하려면 빌드 서버에 동일한 버전의 Visual Studio를 설치해야 합니다.

- [See if an item supports validation](#SupportsValidation)

- [Include other .NET assemblies and projects for validation](#IncludeReferences)

- [Validate code manually](#ValidateManually)

- [Validate code automatically](#ValidateAuto)

- [Troubleshoot layer validation issues](#TroubleshootingValidation)

- [Understand and resolve layer validation errors](#UnderstandingValidationErrors)

## <a name="SupportsValidation"></a> See if an item supports validation
 레이어를 웹 사이트, Office 문서, 일반 텍스트 파일 및 여러 앱에서 공유되는 프로젝트의 파일에 연결할 수는 있지만, 유효성 검사 프로세스에는 레이어가 포함되지 않습니다. 별도의 레이어에 연결된 프로젝트 또는 어셈블리의 경우에는 해당 레이어 간에 종속성이 나타나지 않아도 유효성 검사 오류가 나타나지 않습니다. 이러한 참조는 코드에서 사용하지 않는 한 종속성으로 처리되지 않습니다.

1. On the layer diagram, select one or more layers, right-click your selection, and then click **View Links**.

2. In **Layer Explorer**, look at the **Supports Validation** column. 값이 false일 경우 해당 항목은 유효성 검사를 지원하지 않습니다.

## <a name="IncludeReferences"></a> Include other .NET assemblies and projects for validation
 When you drag items to the layer diagram, references to the corresponding .NET assemblies or projects are added automatically to the **Layer References** folder in the modeling project. 이 폴더에는 유효성 검사 중 분석되는 프로젝트와 어셈블리에 대한 참조가 포함되어 있습니다. 유효성을 검사할 다른 .NET 어셈블리와 프로젝트는 수동으로 레이어 다이어그램으로 끌어 놓지 않고도 포함할 수 있습니다.

1. In **Solution Explorer**, right-click the modeling project or the **Layer References** folder, and then click **Add Reference**.

2. In the **Add Reference** dialog box, select the assemblies or projects, and then click **OK**.

## <a name="ValidateManually"></a> Validate code manually
 If you have an open layer diagram that is linked to solution items, you can run the **Validate** shortcut command from the diagram. You can also use the command prompt to run the **msbuild** command with the **/p:ValidateArchitecture** custom property set to **True**. 예를 들어, 코드를 변경할 때 종속성 충돌을 빠르게 찾을 수 있도록 레이어 유효성 검사를 정기적으로 수행합니다.

#### <a name="to-validate-code-from-an-open-layer-diagram"></a>열려 있는 레이어 다이어그램에서 코드 유효성을 검사하려면

1. Right-click the diagram surface, and then click **Validate Architecture**.

    > [!NOTE]
    > By default, the **Build Action** property on the layer diagram (.layerdiagram) file is set to **Validate** so that the diagram is included in the validation process.

     The **Error List** window reports any errors that occur. For more information about validation errors, see [Understand and resolve layer validation errors](#UnderstandingValidationErrors).

2. To view the source of each error, double-click the error in the **Error List** window.

    > [!NOTE]
    > [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서는 오류 소스 대신 코드 맵이 표시될 수도 있습니다. 레이어 다이어그램에 지정되지 않은 어셈블리에 대한 종속성이 코드에 있거나 레이어 다이어그램에 지정된 종속성이 코드에 없는 경우 종속성 그래프가 표시됩니다. 이 경우 코드 맵이나 코드를 검토하여 종속성이 있어야 하는지 여부를 확인합니다. For more information about code maps, see [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md).

3. To manage errors, see [Manage validation errors](#ManageErrors).

#### <a name="to-validate-code-at-the-command-prompt"></a>명령 프롬프트에서 코드 유효성을 검사하려면

1. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 명령 프롬프트를 엽니다.

2. 다음 중 하나를 선택합니다.

   - 솔루션의 특정 모델링 프로젝트를 기준으로 코드 유효성을 검사하려면 다음 사용자 지정 속성을 사용하여 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]를 실행합니다.

     ```
     msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
     ```

     - 또는

       모델링 프로젝트 파일(.modelproj)과 레이어 다이어그램이 포함된 폴더로 이동한 후 다음 사용자 지정 속성을 사용하여 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]를 실행합니다.

     ```
     msbuild /p:ValidateArchitecture=true
     ```

   - 솔루션의 모든 모델링 프로젝트를 기준으로 코드 유효성을 검사하려면 다음 사용자 지정 속성을 사용하여 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]를 실행합니다.

     ```
     msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
     ```

     - 또는

       솔루션 폴더로 이동한 후 다음 사용자 지정 속성을 사용하여 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]를 실행합니다. 이 솔루션 폴더에는 레이어 다이어그램이 포함된 모델링 프로젝트가 들어 있어야 합니다.

     ```
     msbuild /p:ValidateArchitecture=true
     ```

     발생하는 모든 오류가 나열됩니다. For more information about [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], see [MSBuild](../msbuild/msbuild.md) and [MSBuild Task](../msbuild/msbuild-task.md).

   For more information about validation errors, see [Understand and resolve layer validation errors](#UnderstandingValidationErrors).

### <a name="ManageErrors"></a> Manage validation errors
 개발 과정에서 유효성 검사 중 보고된 충돌 문제 중 일부를 표시하지 않을 수 있습니다. 예를 들어 이미 해결되었거나 특정 시나리오와 관계가 없는 오류를 표시하지 않을 수 있습니다. 오류를 표시하지 않는 경우에는 [!INCLUDE[esprfound](../includes/esprfound-md.md)]에 작업 항목을 기록하는 것이 좋습니다.

> [!WARNING]
> 작업 항목을 만들거나 작업 항목에 연결하려면 TFS SCC(소스 코드 제어)에 이미 연결되어 있어야 합니다. 다른 TFS SCC에 대한 연결을 열려고 하면 Visual Studio가 자동으로 현재 솔루션을 닫습니다. 작업 항목을 만들거나 작업 항목에 연결하기 전에 적절한 SCC에 이미 연결되어 있는지 확인합니다. Visual Studio의 이후 릴리스에서는 SCC에 연결되어 있지 않으면 메뉴 명령을 사용할 수 없습니다.

##### <a name="to-create-a-work-item-for-a-validation-error"></a>유효성 검사 오류에 대한 작업 항목을 만들려면

- In the **Error List** window, right-click the error, point to **Create Work Item**, and then click the type of work item that you want to create.

  Use these tasks to manage validation errors in the **Error List** window:

|**대상**|**Follow these steps**|
|------------|----------------------------|
|선택한 오류를 유효성 검사 중에 표시 안 함|Right-click the one or multiple selected errors, point to **Manage Validation Errors**, and then click **Suppress Errors**.<br /><br /> 표시되지 않는 오류는 취소선 서식을 사용하여 나타납니다. 다음에 유효성 검사를 실행하면 이러한 오류가 나타나지 않습니다.<br /><br /> 표시되지 않는 오류는 해당하는 레이어 다이어그램 파일의 .suppressions 파일에서 추적됩니다.|
|선택한 오류 표시 안 함 중지|Right-click the selected suppressed error or errors, point to **Manage Validation Errors**, and then click **Stop Suppressing Errors**.<br /><br /> 다음에 유효성 검사를 실행하면 표시하지 않도록 선택한 오류는 나타나지 않습니다.|
|Restore all suppressed errors in the **Error List** window|Right-click anywhere in the **Error List** window, point to **Manage Validation Errors**, and then click **Show All Suppressed Errors**.|
|Hide all suppressed errors from the **Error List** window|Right-click anywhere in the **Error List** window, point to **Manage Validation Errors**, and then click **Hide All Suppressed Errors**.|

## <a name="ValidateAuto"></a> Validate code automatically
 로컬 빌드를 실행할 때마다 레이어 유효성 검사를 수행할 수 있습니다. 팀에서 Team Foundation Build를 사용하는 경우, 사용자 지정 MSBuild 작업을 생성하여 지정할 수 있는 제어된 체크 인을 사용하여 유효성 검사를 수행하고 빌드 보고서를 사용하여 유효성 검사 오류를 수집할 수 있습니다. To create gated check-in builds, see [Use a gated check-in build process to validate changes](https://msdn.microsoft.com/library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec).

#### <a name="to-validate-code-automatically-during-a-local-build"></a>로컬 빌드 중 자동으로 코드의 유효성을 검사하려면

- 텍스트 편집기를 사용하여 모델링 프로젝트 파일(.modelproj)을 열고 다음 속성을 포함합니다.

```
<ValidateArchitecture>true</ValidateArchitecture>
```

 \- 또는 -

1. In **Solution Explorer**, right-click the modeling project that contains the layer diagram or diagrams, and then click **Properties**.

2. In the **Properties** window, set the modeling project's **Validate Architecture** property to **True**.

    이렇게 하면 모델링 프로젝트가 유효성 검사 프로세스에 포함됩니다.

3. In **Solution Explorer**, click the layer diagram (.layerdiagram) file that you want to use for validation.

4. In the **Properties** window, make sure that the diagram's **Build Action** property is set to **Validate**.

    이렇게 하면 레이어 다이어그램이 유효성 검사 프로세스에 포함됩니다.

   To manage errors in the Error List window, see [Manage Validation Errors](#ManageErrors).

#### <a name="to-validate-code-automatically-during-a-team-foundation-build"></a>Team Foundation Build 중 자동으로 코드의 유효성을 검사하려면

1. In **Team Explorer**, double-click the build definition, and then click **Process**.

2. Under **Build process parameters**, expand **Compilation**, and type the following in the **MSBuild Arguments** parameter:

    `/p:ValidateArchitecture=true`

   For more information about validation errors, see [Understand and resolve layer validation errors](#UnderstandingValidationErrors). [!INCLUDE[esprbuild](../includes/esprbuild-md.md)]에 대한 자세한 내용은 다음을 참조하십시오.

- [애플리케이션 빌드](/azure/devops/pipelines/index)

- [Use the Default Template for your build process](https://msdn.microsoft.com/library/43930b12-c21b-4599-a980-2995e3d16e31)

- [Modify a Legacy Build that is Based on UpgradeTemplate.xaml](https://msdn.microsoft.com/library/ee1a8259-1dd1-4a10-9563-66c5446ef41c)

- [빌드 프로세스 템플릿 사용자 지정](https://msdn.microsoft.com/library/b94c58f2-ae6f-4245-bedb-82cd114f6039)

- [Monitor Progress of a Running Build](https://msdn.microsoft.com/library/e51e3bad-2d1d-4b7b-bfcc-c43439c6c8ef)

## <a name="TroubleshootingValidation"></a> Troubleshoot layer validation issues
 다음 표에서는 레이어 유효성 검사 문제와 해결 방법에 대해 설명합니다. 이 문제는 코드와 디자인 간의 충돌로 인해 발생하는 오류와 다릅니다. For more information about these errors, see [Understand and resolve layer validation errors](#UnderstandingValidationErrors).

|**문제**|**Possible Cause**|**해결**|
|---------------|------------------------|--------------------|
|유효성 검사 오류가 예상대로 발생하지 않습니다.|같은 모델링 프로젝트에 있는 레이어 다이어그램과 솔루션 탐색기의 다른 다이어그램에서 복사한 레이어 다이어그램에 대해서는 유효성 검사가 수행되지 않습니다. 이렇게 복사한 레이어 다어어그램은 원본 레이어 다이어그램과 동일한 참조를 포함합니다.|모델링 프로젝트에 새 레이어 다이어그램을 추가합니다.<br /><br /> 소스 레이어 다이어그램에서 새 다이어그램으로 요소를 복사합니다.|

## <a name="UnderstandingValidationErrors"></a> Understanding and Resolving Layer Validation Errors
 레이어 다이어그램에서 코드의 유효성을 검사할 때 코드가 디자인과 충돌하면 유효성 검사 오류가 발생합니다. 예를 들어, 다음과 같은 조건에서 유효성 검사 오류가 발생할 수 있습니다.

- 잘못된 레이어에 아티팩트가 할당되었습니다. 이 경우 아티팩트를 이동합니다.

- 클래스 등의 아티팩트가 아키텍처에 맞지 않는 방식으로 다른 클래스를 사용합니다. 이 경우 코드를 리팩터링하여 종속성을 제거합니다.

  이러한 오류를 해결하려면 유효성 검사 중 더 이상 오류가 나타나지 않을 때까지 코드를 업데이트합니다. 이 작업은 반복적으로 수행할 수 있습니다.

  다음 섹션에서는 이러한 오류에 사용되는 구문과 이러한 오류의 의미를 설명하고 오류의 해결 및 관리 방법을 제안합니다.

|**구문**|**설명**|
|----------------|---------------------|
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN* is an artifact that is associated with a layer on the layer diagram.<br /><br /> *ArtifactTypeN* is the type of *ArtifactN*, such as a **Class** or **Method**, for example:<br /><br /> MySolution.MyProject.MyClass.MyMethod(메서드)|
|*NamespaceNameN*|네임스페이스의 이름입니다.|
|*LayerNameN*|레이어 다이어그램에 있는 레이어의 이름입니다.|
|*DependencyType*|The type of dependency relationship between *Artifact1* and *Artifact2*. For example, *Artifact1* has a **Calls** relationship with *Artifact2*.|

|**Error Syntax**|**Error Description**|
|----------------------|---------------------------|
|AV0001: Invalid Dependency: *Artifact1*(*ArtifactType1*) --> *Artifact2*(*ArtifactType2*)<br /><br /> Layers: *LayerName1*, *LayerName2* &#124; Dependencies: *DependencyType*|*Artifact1* in *LayerName1* should not have a dependency on *Artifact2* in *LayerName2* because *LayerName1* does not have a direct dependency on *LayerName2*.|
|AV1001: Invalid Namespace: *Artifact*<br /><br /> Layer: *LayerName* &#124; Required Namespace: *NamespaceName1* &#124; Current Namespace: *NamespaceName2*|*LayerName* requires that its associated artifacts must belong to *NamespaceName1*. *Artifact* is in *NamespaceName2*, not *NamespaceName1*.|
|AV1002: Depends on Forbidden Namespace: *Artifact1*(*ArtifactType1*) &#124; *Artifact2*(*ArtifactType2*)<br /><br /> Layer: *LayerName* &#124; Forbidden Namespace: *NamespaceName* &#124; Dependencies: *DependencyType*|*LayerName* requires that its associated artifacts must not depend on *NamespaceName*. *Artifact1* cannot depend on *Artifact2* because *Artifact2* is in *NamespaceName*.|
|AV1003: In Forbidden Namespace: *Artifact*(*ArtifactType*)<br /><br /> Layer: *LayerName* &#124; Forbidden Namespace: *NamespaceName*|*LayerName* requires that its associated artifacts cannot belong to *NamespaceName*. *Artifact* belongs to *NamespaceName*.|
|AV3001: Missing Link: Layer '*LayerName*' links to '*Artifact*' which cannot be found. 어셈블리 참조가 있는지 확인하세요.|*LayerName* links to an artifact that cannot be found. 예를 들어 모델링 프로젝트에 클래스가 포함된 어셈블리에 대한 참조가 없어서 해당 클래스에 대한 링크가 없을 수 있습니다.|
|AV9001: 아키텍처 유효성 검사에서 내부 오류가 발생했습니다. 결과가 불완전할 수 있습니다. 자세한 내용은 상세 빌드 이벤트 로그를 참조하세요.|자세한 내용은 빌드 이벤트 로그 또는 출력 창을 참조하세요.|

## <a name="security"></a>보안

## <a name="see-also"></a>관련 항목:
 [개발하는 동안 시스템 유효성 검사](../modeling/validate-your-system-during-development.md)
