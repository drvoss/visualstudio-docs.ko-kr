---
title: SupportsMasterPage 요소 (Visual Studio 템플릿) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsMasterPage
helpviewer_keywords:
- <SupportsMasterPage> element [Visual Studio Templates]
- SupportsMasterPage element [Visual Studio Templates]
ms.assetid: ce877a6a-9bba-4fd9-92fb-0a8dfec9e75b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba409c831dd508dae796bca1ea2837674459690d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316688"
---
# <a name="supportsmasterpage-element-visual-studio-templates"></a>SupportsMasterPage 요소(Visual Studio 템플릿)
지정 여부는 **마스터 페이지 선택** 확인란이 활성화 합니다 **새 항목 추가** 대화 상자.

 \<VSTemplate> \<TemplateData> \<SupportsMasterPage>

## <a name="syntax"></a>구문

```
<SupportsMasterPage> true/false </SupportsMasterPage>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성
 없음

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|서식 파일을 분류 하 고 표시 하는 방법을 정의 하는 데이터를 지정 합니다 **새 프로젝트** 또는 **새 항목** 대화 상자.|

## <a name="text-value"></a>텍스트 값
 텍스트 값은 필수입니다.

 텍스트 여야 `true` 또는 `false`나타내는 여부는 **마스터 페이지 선택** 확인란이 활성화를 **새 항목 추가** 대화 상자.

## <a name="remarks"></a>설명
 `SupportsMasterPage`는 선택적 요소입니다. 기본값은 `false`입니다.

 `SupportsMasterPage` 요소는 웹 항목 템플릿을 사용할 수 있습니다.

## <a name="example"></a>예제
 다음 예에서는 마스터 페이지에 대 한 지원을 포함 하는 웹 프로젝트에 대 한 메타 데이터를 보여 줍니다.

```
<VSTemplate Version="3.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple Web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
        <SupportsMasterPage>true</SupportsMasterPage>
    </TemplateData>
    <TemplateContent>
        <Project File="WebApplication.webproj">
            <ProjectItem>icon.ico</ProjectItem>
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>
            <ProjectItem>Default.aspx.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>참고 항목
- [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)