---
title: TemplateData 요소 (Visual Studio 템플릿) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateData
helpviewer_keywords:
- TemplateData element [Visual Studio project templates]
ms.assetid: db17ec9b-bfdf-46b1-bbe7-5ccc140056e2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f9647330aaca2c2ae91aa7e461da17cf4dc3f8c3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316669"
---
# <a name="templatedata-element-visual-studio-templates"></a>TemplateData 요소(Visual Studio 템플릿)
템플릿을 분류하고 **새 프로젝트** 또는 **새 항목 추가** 대화 상자에서 템플릿이 표시되는 방식을 정의합니다.

 \<VSTemplate> \<TemplateData>

## <a name="syntax"></a>구문

```
<TemplateData>
    <Name> ... </Name>
    <Description> ... </Description>
    <Icon> ... </Icon>
    <ProjectType> ... </ProjectType>
    ...
</TemplateData>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성
 없음

### <a name="child-elements"></a>자식 요소

| 요소 | 설명 |
| - | - |
| [이름](../extensibility/name-element-visual-studio-templates.md) | 필수적 요소입니다.<br /><br /> 표시 된 대로 템플릿의 이름을 지정 합니다 **새 프로젝트** 또는 **새 항목 추가** 대화 상자. |
| [설명](../extensibility/description-element-visual-studio-templates.md) | 필수적 요소입니다.<br /><br /> 표시 된 대로 템플릿의 설명을 지정 합니다 **새 프로젝트** 또는 **새 항목 추가** 대화 상자. |
| [아이콘](../extensibility/icon-element-visual-studio-templates.md) | 필수적 요소입니다.<br /><br /> 경로 중에 나타나는 아이콘으로 사용 되는 이미지 파일의 파일 이름을 지정 합니다 **새 프로젝트** 또는 **새 항목 추가** 템플릿에 대 한 대화 상자. |
| [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) | 필수적 요소입니다.<br /><br /> 지정 된 그룹에 나타나도록 프로젝트 템플릿을 분류 합니다 **새 프로젝트** 대화 상자. |
| [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) | 선택적 요소입니다.<br /><br /> 지정 된 하위 범주에 표시 되도록 프로젝트 템플릿을 분류 합니다 **새 프로젝트** 대화 상자. |
| [TemplateID](../extensibility/templateid-element-visual-studio-templates.md) | 선택적 요소입니다.<br /><br /> 템플릿 ID를 지정합니다. |
| [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) | 선택적 요소입니다.<br /><br /> 템플릿 그룹 ID를 지정합니다. |
| [SortOrder](../extensibility/sortorder-element-visual-studio-templates.md) | 선택적 요소입니다.<br /><br /> 표시 된 대로 동일한 범주의 다른 템플릿 간에 템플릿을 정렬 하는 데 사용 되는 값을 지정 합니다 **새 프로젝트** 하거나 **새 항목 추가** 대화 상자. |
| [CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md) | 선택적 요소입니다.<br /><br /> 포함 된 폴더를 프로젝트의 인스턴스화에 만들어지는지 여부를 지정 합니다. |
| [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) | 선택적 요소입니다.<br /><br /> 만들 때 프로젝트 또는 항목에 대 한 Visual Studio 프로젝트 시스템에서 생성 하는 이름을 지정 합니다. |
| [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) | 선택적 요소입니다.<br /><br /> 만들어질 때 Visual Studio 프로젝트 시스템에서 프로젝트 또는 항목에 대 한 기본 이름을 생성할 됩니다 있는지 여부를 지정 합니다. |
| [PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md) | 선택적 요소입니다.<br /><br /> 임시 프로젝트 (Visual Studio 2017만)로 프로젝트를 만들 수 있는지 여부를 지정 합니다. |
| [EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md) | 선택적 요소입니다.<br /><br /> 지정 여부를 합니다 **찾아보기** 단추를 사용할 수는 **새 프로젝트** 대화 상자에서 사용자가 새 프로젝트를 저장 된 기본 디렉터리를 쉽게 수정할 수 있도록 합니다. |
| [숨김](../extensibility/hidden-element-visual-studio-templates.md) | 선택적 요소입니다.<br /><br /> 템플릿 중 하나에 표시할지 여부를 지정 합니다 **새 프로젝트** 하거나 **새 항목 추가** 대화 상자. |
| [NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md) | 선택적 요소입니다.<br /><br /> 부모 범주에 템플릿 표시 하는 횟수를 지정 합니다 **새 프로젝트** 대화 상자. |
| [LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md) | 선택적 요소입니다. |
| [LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md) | 선택적 요소입니다.<br /><br /> 지정 여부는 **위치** 텍스트 상자에 **새 프로젝트** 대화 상자는 활성화, 비활성화 또는 프로젝트 템플릿에 대 한 숨겨진 합니다. |
| [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) | 선택적 요소입니다.<br /><br /> 템플릿은 특정 최소 버전 및.NET Framework의 이후 버전 에서만 지원 되는 경우이 요소를 사용 합니다. |
| [SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md) | 선택적 요소입니다.<br /><br /> 템플릿을 웹 프로젝트에 대 한 마스터 페이지를 지원 하는지 여부를 지정 합니다. |
| [SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md) | 선택적 요소입니다.<br /><br /> 지정 템플릿을 웹 프로젝트용 코드 분리 또는 코드 숨김 페이지 모델을 지원 하는지 여부입니다. |
| [SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md) | 선택적 요소입니다.<br /><br /> 템플릿이 적용 되는 여러 언어에 대해 동일한 여부를 지정 합니다 **언어** 옵션에서 사용할 수는 **새 프로젝트** 대화 상자. |
| [TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md) | 선택적 요소입니다.<br /><br /> 프로젝트 템플릿의 대상 플랫폼을 지정합니다. 이 요소를 만드는 프로젝트 템플릿을 사용 되도록 지정 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 앱. |

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|필수적 요소입니다.<br /><br /> 프로젝트 템플릿, 항목 템플릿 또는 시작 키트에 대 한 모든 메타 데이터를 포함합니다.|

## <a name="remarks"></a>설명
 `TemplateData` 필수 요소가입니다.

 선택적 요소를 포함 하지 않은 경우에 해당 요소에 대 한 기본값이 사용 됩니다.

## <a name="example"></a>예제
 다음 예제에서는 프로젝트 템플릿에 대 한 메타 데이터는 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 응용 프로그램입니다.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyStarterKit.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>참고 항목
- [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)