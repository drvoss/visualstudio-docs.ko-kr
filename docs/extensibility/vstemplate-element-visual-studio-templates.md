---
title: VSTemplate 요소 (Visual Studio 템플릿) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#VSTemplate
helpviewer_keywords:
- VSTemplate element [Visual Studio project templates]
ms.assetid: f8ac561b-3b0b-4246-9ec9-118d2447e9a9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cdcbde9ab8e49d439ab909b4cd5563d6b8ec3afa
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322864"
---
# <a name="vstemplate-element-visual-studio-templates"></a>VSTemplate 요소 (Visual Studio 템플릿)
프로젝트 템플릿, 항목 템플릿 또는 시작 키트에 대 한 모든 메타 데이터를 포함합니다.

## <a name="syntax"></a>구문

```csharp
<VSTemplate Type="TemplateType" Version="x.x.x">
    <TemplateData>    </TemplateData>
    <TemplateContent>    </TemplateContent>
    ...
</VSTemplate>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

| 특성 | 설명 |
|-----------| - |
| `Type` | 프로젝트 템플릿 또는 항목 템플릿을으로 템플릿을 식별합니다. 이 특성의 값을 가질 수 `Project` 또는 `Item`합니다. |
| `Version` | 템플릿에 대 한 버전 번호를 지정합니다. 템플릿 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] 하 고 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 가 `Version` 특성 값 `3.0.0`합니다. |

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|필수적 요소입니다.<br /><br /> 서식 파일을 분류 하 고 표시 하는 방법을 정의 하는 데이터를 지정 합니다 **새 프로젝트** 또는 **새 항목 추가** 대화 상자.|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|필수적 요소입니다.<br /><br /> 서식 파일의 내용을 지정합니다.|
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|선택적 요소입니다.|
|[WizardData](../extensibility/wizarddata-element-visual-studio-templates.md)|선택적 요소입니다.|

### <a name="parent-elements"></a>부모 요소
 없음

## <a name="remarks"></a>설명
 합니다 `VSTemplate` 요소는 루트 요소입니다 *.vstemplate* 파일입니다.

## <a name="example"></a>예제
 다음 예제에서는 프로젝트 템플릿에 대 한 메타 데이터는 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 응용 프로그램입니다.

```xml
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
            <ProjectItem>Form1.cs</ProjectItem>
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