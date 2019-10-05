---
title: SolutionFolder 요소 (Visual Studio 템플릿) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SolutionFolder
helpviewer_keywords:
- <SolutionFolder> element [Visual Studio Templates]
- SolutionFolder element [Visual Studio Templates]
ms.assetid: 963f0398-fb50-4d8e-879d-d48f8b7c6d80
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4fd2ce948a3e18633f4c9875fa3ec0b064a91b35
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331991"
---
# <a name="solutionfolder-element-visual-studio-templates"></a>SolutionFolder 요소(Visual Studio 템플릿)
다중 프로젝트 템플릿의 프로젝트를 그룹화합니다.

 \<VSTemplate> \<TemplateContent> \<ProjectCollection> \<SolutionFolder>

## <a name="syntax"></a>구문

```
<SolutionFolder Name="DirectoryName">
    ...
</SolutionFolder>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|`Name`|필수 특성입니다.<br /><br /> 솔루션 폴더의 기본 이름입니다.|

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|선택적 요소입니다.<br /><br /> 다중 프로젝트 템플릿에 있는 단일 프로젝트의 .vstemplate 파일에 대한 경로를 지정합니다.|
|`SolutionFolder`|선택적 요소입니다.<br /><br /> 다중 프로젝트 템플릿의 프로젝트를 그룹화합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|다중 프로젝트 템플릿의 구성과 내용을 지정합니다.|
|`SolutionFolder`|다중 프로젝트 템플릿의 프로젝트를 그룹화합니다.|

## <a name="remarks"></a>설명
 다중 프로젝트 템플릿은 두 개 이상의 프로젝트에 대한 컨테이너로 사용됩니다. `SolutionFolder` 요소는 템플릿의 프로젝트를 그룹으로 구성하는 데 사용됩니다. `SolutionFolder` 요소로 지정된 폴더는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]의 프로젝트에 솔루션 폴더로 만들어집니다. 다중 프로젝트 템플릿에 대 한 자세한 내용은 참조 하세요. [방법: 다중 프로젝트 템플릿 만들기](../ide/how-to-create-multi-project-templates.md)합니다.

## <a name="example"></a>예제
 이 예제에서는 `SolutionFolder` 요소를 사용하여 다중 프로젝트 템플릿을 `Math Classes` 및 `Graphics Classes`의 두 그룹으로 나눕니다. 이 템플릿에는 각 솔루션 폴더에 2개가 포함되는 4개의 프로젝트가 포함되어 있습니다.

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
            <SolutionFolder Name="Math Classes">
                <ProjectTemplateLink ProjectName="MathClassLib1">
                    MathClassLib1\MyTemplate.vstemplate
                </ProjectTemplateLink>
                <ProjectTemplateLink ProjectName="MathClassLib2">
                    MathClassLib2\MyTemplate.vstemplate
                </ProjectTemplateLink>
            </SolutionFolder>
            <SolutionFolder Name="Graphics Classes">
                <ProjectTemplateLink ProjectName="GraphicsClassLib1">
                    GraphicsClassLib1\MyTemplate.vstemplate
                </ProjectTemplateLink>
                <ProjectTemplateLink ProjectName="GraphicsClassLib2">
                    GraphicsClassLib2\MyTemplate.vstemplate
                </ProjectTemplateLink>
            </SolutionFolder>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>참고 항목
- [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
- [방법: 다중 프로젝트 템플릿 만들기](../ide/how-to-create-multi-project-templates.md)