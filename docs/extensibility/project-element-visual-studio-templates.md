---
title: Project 요소 (Visual Studio 템플릿) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Project
helpviewer_keywords:
- Project element [Visual Studio Templates]
- <Project> element [Visual Studio Templates]
ms.assetid: 1da15ea6-26e2-462b-a03e-584ef4996579
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 843ba7935dbddb95c9a3043deff534db9157f15b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66336044"
---
# <a name="project-element-visual-studio-templates"></a>Project 요소 (Visual Studio 템플릿)
파일 또는 프로젝트에 추가할 디렉터리를 지정 합니다.

 \<VSTemplate> \<TemplateContent> \<Project>

## <a name="syntax"></a>구문

```
<Project
    File="MyProject.proj"
    TargetFileName="MyTargetProject.proj"
    ReplaceParameters="true/false">
    IgnoreProjectParameter="$myCustomParameter$"
        ...
</Project>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|`File`|필수 특성입니다.<br /><br /> 템플릿에서 프로젝트 파일의 이름을 지정 *.zip* 파일입니다.|
|`ReplaceParameters`|선택적 특성입니다.<br /><br /> 프로젝트 파일에 프로젝트를 템플릿에서 만들면 대체 되어야 하는 매개 변수 값이 있는지 여부를 지정 하는 부울 값입니다. 기본값은 `false`여야 합니다.|
|`TargetFileName`|선택적 특성입니다.<br /><br /> 템플릿에서 프로젝트를 만들 때 프로젝트 파일의 이름을 지정 합니다.|
|`IgnoreProjectParameter`|선택적 특성입니다.<br /><br /> 프로젝트를 현재 솔루션에 추가할지 여부를 지정 합니다. 경우 사용자 지정 매개 변수 값 "$*myCustomParameter*$"가 프로젝트 매개 변수 대체 파일에서 생성 되었지만 현재 열려 있는 솔루션의 일부로 추가 되지 않습니다.|

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[폴더](../extensibility/folder-element-visual-studio-project-templates.md)|선택적 요소입니다.<br /><br /> 프로젝트에 추가할 폴더를 지정 합니다.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md)|선택적 요소입니다.<br /><br /> 프로젝트에 추가할 파일을 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|필수적 요소입니다.|

## <a name="remarks"></a>설명
 `Project`은 `TemplateContent`의 선택적 자식 요소입니다.

 `Project` 요소는 프로젝트를 지정 하는 데 사용 하 고 따라서 경우에 유효한 프로젝트 템플릿.

 `Project` 요소가 포함할 수 있는 [폴더](../extensibility/folder-element-visual-studio-project-templates.md) 자식 요소 또는 [ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md) 자식 요소가 있지만 둘 다의 혼합은 아님 `Folder` 고 `ProjectItem` 자식 요소입니다.

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 사용자가 입력 한 이름을 기반으로 프로젝트 파일 이름을 자동으로 바뀝니다 합니다 **새 프로젝트** 대화 상자. 사용 된 `TargetFileName` 템플릿을 사용 하 여 만든 프로젝트 파일에 대 한 대체 파일 이름을 제공 하려는 경우 특성입니다.

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

## <a name="see-also"></a>참고자료
- [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
- [ProjectItem 요소 (Visual Studio 프로젝트 템플릿)](../extensibility/projectitem-element-visual-studio-project-templates.md)
- [Folder 요소 (Visual Studio 프로젝트 템플릿)](../extensibility/folder-element-visual-studio-project-templates.md)