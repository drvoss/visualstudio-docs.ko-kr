---
title: Visual Studio 템플릿 매니페스트 스키마 참조 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52a421986e076d2badc6dc7eb76247d243da155b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323019"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Visual Studio 템플릿 매니페스트 스키마 참조
이 스키마에는 Visual Studio 템플릿 매니페스트의 형식을 설명 합니다 ( *.vstman*) Visual Studio 프로젝트 또는 항목 템플릿에 대해 생성 되는 파일입니다. 또한 스키마 위치 및 템플릿에 대 한 기타 관련 정보를 설명합니다.

 : 있기 때문에 별도 항목 및 프로젝트 템플릿 디렉터리, 매니페스트 되지 다양 한 항목 및 프로젝트 템플릿이 있어야 합니다.

> [!IMPORTANT]
> 이 매니페스트는 Visual Studio 2017부터 사용할 수 있습니다.

## <a name="vstemplatemanifest-element"></a>VSTemplateManifest 요소
 매니페스트의 루트 요소입니다.

### <a name="attributes"></a>특성

- **버전** 템플릿 매니페스트 버전을 나타내는 문자열입니다. 필수 요소.

- **로캘**: 로캘 또는 로캘의 템플릿 매니페스트를 나타내는 문자열입니다. 로캘 값을 모든 서식 파일에 적용 됩니다. 각 로캘에 대해 별도 매니페스트를 사용 해야 합니다. 선택 사항입니다.

### <a name="child-elements"></a>자식 요소

- **VSTemplateContainer** 선택 사항입니다.

- **VSTemplateDir** 선택 사항입니다.

### <a name="parent-element"></a>부모 요소
 없음

## <a name="vstemplatecontainer"></a>VSTemplateContainer
 컨테이너 템플릿 매니페스트 요소입니다. 매니페스트를 정의 하는 각 템플릿에 대 한 하나의 템플릿 컨테이너를 있습니다.

### <a name="attributes"></a>특성
 **VSTemplateType**: 서식 파일의 형식을 지정 하는 문자열 값 (`"Project"`, `"Item"`, 또는 `"ProjectGroup"`). 필수

### <a name="child-elements"></a>자식 요소

- **RelativePathOnDisk**:  디스크에서 템플릿 파일의 상대 경로입니다. 이 위치에 표시 된 템플릿 트리에서 템플릿의 위치를 정의 합니다 **새 프로젝트** 하거나 **새 항목** 대화 합니다. 디렉터리 및 개별 파일로 배포 템플릿에 대해이 경로 템플릿 파일을 포함 하는 디렉터리를 가리킵니다. 템플릿 배포에 대 한는 *.zip* 파일을이 경로에 대 한 경로 여야 합니다 합니다 *.zip* 파일입니다.

- **VSTemplateHeader: A [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) 헤더를 설명 하는 요소입니다.

### <a name="parent-element"></a>부모 요소
 **VSTemplateManifest**

## <a name="vstemplatedir"></a>VSTemplateDir
 템플릿이 위치한 디렉터리를 설명 합니다. 매니페스트는 여러 개 포함할 수 있습니다 **VSTemplateDir** 지역화 된 이름 및 템플릿 범주 트리의 모양을 제어 하려면 디렉터리에 대 한 순서 정렬 제공 하는 항목이 있습니다.

 해당 디자인으로 인해 **VSTemplateDir** 항목 이외의 로캘 지정한 매니페스트에만 표시 됩니다.

### <a name="attributes"></a>특성
 없음

### <a name="child-elements"></a>자식 요소

- **RelativePath**: 서식 파일의 경로입니다. 모든 매니페스트에 대 한 첫 번째 것 win 됩니다 있도록 경로 당 하나의 항목 수입니다.

- **LocalizedName**: A **NameDescriptionIcon** 지역화 된 이름을 지정 하는 요소입니다. 선택 사항입니다.

- **SortOrder**: 정렬 순서를 지정 하는 문자열입니다. 선택 사항입니다.

- **ParentFolderOverrideName**: 부모 폴더의 재정의 된 이름입니다. 선택 사항입니다. 이 요소에는 **이름을** 특성 이름을 지정 하는 문자열 값입니다.

### <a name="parent-element"></a>부모 요소
 **VSTemplateManifest**

## <a name="namedescriptionicon"></a>NameDescriptionIcon
 이름과 지역화 된 템플릿 수에 대 한 설명을 지정합니다. 참조 **LocalizedName** 위에 있습니다.

### <a name="attributes"></a>특성

- **패키지**: 패키지를 지정 하는 문자열 값입니다. 선택 사항입니다.

- **ID**: Id를 지정 하는 문자열 값 선택 사항입니다.

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-element"></a>부모 요소
 **LocalizedName**

## <a name="examples"></a>예제
 다음 코드는 프로젝트 템플릿의 예로 *.vstman* 파일입니다.

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Project">
    <RelativePathOnDisk>CSharp\1033\TestProjectTemplate</RelativePathOnDisk>
    <TemplateFileName>TestProjectTemplate.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>TestProjectTemplate</Name>
        <Description>TestProjectTemplate</Description>
        <Icon>TestProjectTemplate.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <SortOrder>1000</SortOrder>
        <TemplateID>aac0aeea-7883-4003-992f-937d53d70ab1</TemplateID>
        <CreateNewFolder>true</CreateNewFolder>
        <DefaultName>TestProjectTemplate</DefaultName>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```

 다음 코드는 항목 템플릿의 예로 *.vstman* 파일입니다.

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Item">
    <RelativePathOnDisk>CSharp\1033\ItemTemplate1</RelativePathOnDisk>
    <TemplateFileName>ItemTemplate1.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>ItemTemplate1</Name>
        <Description>ItemTemplate1</Description>
        <Icon>ItemTemplate1.ico</Icon>
        <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
        <DefaultName>Class.cs</DefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```
