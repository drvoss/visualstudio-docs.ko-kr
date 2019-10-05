---
title: ProjectTemplateLink 요소 (Visual Studio 템플릿) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectTemplateLink
helpviewer_keywords:
- <ProjectTemplateLink> element [Visual Studio Templates]
- ProjectTemplateLink element [Visual Studio Templates]
ms.assetid: b0449111-8b48-45a1-a031-ea24b765e969
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e911977156a6b750c1e15fec46ead77e1bac0204
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335854"
---
# <a name="projecttemplatelink-element-visual-studio-templates"></a>ProjectTemplateLink 요소(Visual Studio 템플릿)
경로를 지정 합니다 *.vstemplate* 다중 프로젝트 템플릿에 있는 하나의 프로젝트의 파일입니다.

 \<VSTemplate> \<TemplateContent> \<ProjectCollection> \<ProjectTemplateLink> -or- \<VSTemplate> \<TemplateContent> \<ProjectCollection> \<SolutionFolder> \<ProjectTemplateLink>

## <a name="syntax"></a>구문

```xml
<ProjectTemplateLink ProjectName="Name">
    PathToTemplateFile
</ProjectTemplateLink>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|`ProjectName`|선택적 특성입니다.<br /><br /> 다중 프로젝트 템플릿에 있는 개별 프로젝트 각각의 이름을 지정합니다. 합니다 **새 프로젝트** 대화 상자는 개별 프로젝트에 이름을 할당할 수 없습니다.|
|`CopyParameters`|각 연결된 템플릿에 복사할 기본 그룹 템플릿에서 모든 변수를 활성화할수 있습니다.<br /><br /> 연결된 템플릿의 매개 변수에는 `"$ext_*$"` 접두사가 있습니다. 예를 들어, 부모 그룹 템플릿의 매개 변수에서 작업 하는 경우 `$projectname$` 값이 **ExampleProject1**연결 된 템플릿이 실행 될 차례가 가져오면, 매개 변수 획득 `$ext_projectname$`, 합니다 의복사본인`$projectname$`부모 그룹 템플릿에서 매개 변수입니다.<br /><br /> 그에 따라 연결된 템플릿을 통해 부모 그룹 템플릿에서만 편리하게 만들 수 있는 일부 공통 매개 변수를 공유할 수 있습니다.<br /><br /> 이 특성은 선택적이며 포함되지 않은 경우 기본값이 `false`로 자동 설정됩니다.<br /><br /> 이 특성은 Visual Studio 2013 업데이트 2에서 도입되었습니다. 올바른 제품 버전을 참조 하려면 참조 [Visual Studio 2013 SDK 업데이트 2에서 제공 하는 어셈블리를 참조할](https://msdn.microsoft.com/library/42b65c3e-e42b-4c39-98c8-bea285f25ffb)합니다.|

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|다중 프로젝트 템플릿의 구성과 내용을 지정합니다.|
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|다중 프로젝트 템플릿의 프로젝트를 그룹화합니다.|

## <a name="text-value"></a>텍스트 값
 텍스트 값은 필수입니다.

 이 텍스트에 대 한 경로 지정 합니다 *.vstemplate* 템플릿의 파일입니다.

## <a name="remarks"></a>설명
 다중 프로젝트 템플릿은 두 개 이상의 프로젝트에 대한 컨테이너로 사용됩니다. 합니다 `ProjectTemplateLink` 요소는의 위치를 지정 하는 데 사용 되는 *.vstemplate* 템플릿에서 프로젝트 중 하나에 대 한 파일입니다. 합니다 *.vstemplate* 다중 프로젝트 템플릿의 파일 하나가 포함 되어 있습니다 `ProjectTemplateLink` 템플릿의 각 프로젝트에 대 한 요소입니다. 다중 프로젝트 템플릿에 대 한 자세한 내용은 참조 하세요. [방법: 다중 프로젝트 템플릿 만들기](../ide/how-to-create-multi-project-templates.md)합니다.

## <a name="example"></a>예제
 이 예제에서는 단순한 다중 프로젝트 루트를 보여 줍니다 *.vstemplate* 파일입니다. 이 예제에서 템플릿에는 `My Windows Application` 프로젝트와 `My Class Library` 프로젝트가 들어 있습니다. `ProjectName` 요소의 `ProjectTemplateLink` 특성은 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]가 이 프로젝트에 할당할 이름을 설정합니다. 경우는 `ProjectName` 의 이름 특성이 없는 합니다 *.vstemplate* 파일은 프로젝트 이름으로 사용 됩니다.

```
<VSTemplate Version="3.0.0" Type="ProjectGroup"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-Project Template Sample</Name>
        <Description>An example of a multi-project template</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectCollection>
            <ProjectTemplateLink ProjectName="My Windows Application">
                WindowsApp\MyTemplate.vstemplate
            </ProjectTemplateLink>
            <ProjectTemplateLink ProjectName="My Class Library" CopyParameters="true">
                ClassLib\MyTemplate.vstemplate
            </ProjectTemplateLink>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>참고자료
- [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
- [방법: 다중 프로젝트 템플릿 만들기](../ide/how-to-create-multi-project-templates.md)