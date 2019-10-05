---
title: Visual Studio 2017에 대 한 사용자 지정 프로젝트 및 항목 템플릿 업그레이드
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: d375dfc4a53015f57546f7cbfcc8b940fa81bd0b
ms.sourcegitcommit: 74c5360186731de07828764eb32ea1033a8c2275
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67559753"
---
# <a name="upgrade-custom-project-and-item-templates-for-visual-studio-2017"></a>사용자 지정 프로젝트 및 항목 템플릿을 Visual Studio 2017에 대 한 업그레이드

Visual Studio 2017부터 Visual Studio는 이전 버전 Visual Studio의 다른 방식으로.vsix 또는.msi 설치 된 프로젝트 및 항목 템플릿을 검색 합니다. 사용자 지정 프로젝트 또는 항목 템플릿을 사용 하는 확장을 소유 하는 경우 확장을 업데이트 해야 합니다. 이 문서에서는 수행 해야 합니다.

이 변경에는 Visual Studio 2017에만 적용 됩니다. 이전 버전의 Visual Studio에는 영향을 주지 않습니다.

VSIX 확장의 일부로 프로젝트 또는 항목 템플릿을 만들려는 경우 참조 [사용자 지정 프로젝트 및 항목 템플릿 만들기](../extensibility/creating-custom-project-and-item-templates.md)합니다.

## <a name="template-scanning"></a>템플릿 검색

이전 버전의 Visual Studio **devenv /setup** 하거나 **devenv /installvstemplates** 프로젝트 및 항목 템플릿을 찾으려면 로컬 디스크를 검색 합니다. Visual Studio 2017부터 검색 사용자 수준 위치에 대해서만 수행 됩니다. 기본 사용자 수준 위치가 **%USERPROFILE%\Documents\\< Visual Studio 버전\>\Templates\\** 합니다. 이 위치를 사용 하 여 생성 된 템플릿에 대 한 합니다 **프로젝트** > **템플릿 내보내기...**  명령 경우 합니다 **자동으로 템플릿을 Visual Studio로 가져오기** 마법사에서 옵션을 선택 합니다.

기타 (비 사용자) 위치에 대 한 서식 파일의 다른 특성과 위치를 지정 하는 manifest(.vstman) 파일을 포함 해야 합니다. .Vstman 파일은 템플릿에 사용.vstemplate 파일과 함께 생성 됩니다. .Vsix를 사용 하 여 확장을 설치 하면 Visual Studio 2017에서 확장을 다시 컴파일하여이 수행할 수 있습니다. 하지만.msi를 사용 하는 경우 수동으로 변경 해야 합니다. 이러한 변경을 수행 하기 위해 필요한 목록은 참조 하세요. **와 함께 설치 된 확장에 대 한 업그레이드를 합니다. MSI** 나중에이 페이지입니다.

## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>프로젝트 또는 항목 템플릿을 VSIX 확장을 업데이트 하는 방법

1. Visual Studio 2017에서 솔루션을 엽니다. 코드를 업그레이드 하 라는 메시지가 표시 됩니다. **확인**을 클릭합니다.

2. 업그레이드를 완료 한 후에 설치 대상 버전을 변경 하는 것이 해야 합니다. VSIX 프로젝트에서 source.extension.vsixmanifest 파일을 열고 선택 합니다 **설치 대상** 탭 합니다. 경우는 **버전 범위** 필드가 **[14.0]** , 클릭 **편집** Visual Studio 2017을 포함 하도록 변경 합니다. 로를 설정 하는 예를 들어 **[14.0,15.0]** 또는 Visual Studio 2015 또는 Visual Studio 2017 확장을 설치 하려면 **[15.0]** 방금 Visual Studio 2017을 설치 합니다.

3. 코드를 다시 컴파일해야 합니다.

4. Visual Studio를 닫습니다.

5. VSIX를 설치 합니다.

6. 다음을 수행 하 여 업데이트를 테스트할 수 있습니다.

    1. 파일 변경 검색 다음 레지스트리 키에 의해 활성화 됩니다.

         **reg add hklm\software\microsoft\visualstudio\15.0\VSTemplate /v DisableTemplateScanning /t REG_DWORD /d 1 /reg:32**

    2. 키를 추가한 후 실행할 **devenv /installvstemplates**합니다.

    3. Visual Studio를 다시 엽니다. 필요한 위치에 템플릿을 찾아야 합니다.

    > [!NOTE]
    > Visual Studio 확장성 프로젝트 템플릿 레지스트리 키가 존재 하는 경우 사용할 수 없는 경우 레지스트리 키를 삭제 해야 합니다 (다시 실행 하십시오 **devenv /installvstemplates**) 사용 합니다.

## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>프로젝트 및 항목 템플릿을 배포 하기 위한 기타 권장 사항

- 압축 된 템플릿 파일을 사용 하지 마십시오. 템플릿 파일에 리소스와 콘텐츠를 검색 하기 위해 압축 된 필요한 압축 되므로 될 데 비용이 많이 들기 합니다. 대신 자신의 디렉터리 템플릿 초기화 속도를 개별 파일로 프로젝트 및 항목 템플릿을 배포 해야 합니다. VSIX 확장에 대 한 SDK 빌드 작업은 자동으로 압축을 풉니다 압축된 템플릿을 VSIX 파일을 만드는 동안.

- 템플릿 검색 하는 동안 불필요 한 리소스 어셈블리 로드를 방지 하기 위해 미리 보기 또는 템플릿 이름, 설명, 아이콘, 패키지/리소스 ID 항목을 사용 하지 않습니다. 대신, 속성 또는 지역화 된 이름을 사용 하는 각 로캘에 대해 템플릿 항목을 만드는 지역화 된 매니페스트를 사용할 수 있습니다.

- 템플릿을 있는 그대로 파일 항목을 포함 하는 경우 매니페스트 생성 얻지 못할 수도 있습니다 하면 예상된 된 결과가 있습니다. 이 경우 VSIX 프로젝트를 수동으로 생성 된 매니페스트를 추가 해야 합니다.

## <a name="file-changes-in-project-and-item-templates"></a>프로젝트 및 항목 템플릿 파일 변경 내용
새 파일을 올바르게 작성할 수 있도록 지점 차이 Visual Studio 2015 및 Visual Studio 2017 버전 템플릿 파일을 보여 줍니다.

 Visual Studio 2015에서 만든 기본 프로젝트.vstemplate 파일은 다음과 같습니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">
  <TemplateData>
    <Name>ProjectTemplate1</Name>
    <Description>ProjectTemplate1</Description>
    <Icon>ProjectTemplate1.ico</Icon>
    <ProjectType>CSharp</ProjectType>
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
    <SortOrder>1000</SortOrder>
    <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>
    <CreateNewFolder>true</CreateNewFolder>
    <DefaultName>ProjectTemplate1</DefaultName>
    <ProvideDefaultName>true</ProvideDefaultName>
  </TemplateData>
  <TemplateContent>
    <Project File="ProjectTemplate.csproj" ReplaceParameters="true">
      <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>
      <ProjectItem ReplaceParameters="true" OpenInEditor="true">Class1.cs</ProjectItem>
    </Project>
  </TemplateContent>
</VSTemplate>

```

 VSIX 프로젝트를 다시 작성에서 발생 시킨.vstman 파일 (찾을 수 있습니다 VSIX 프로젝트의 매니페스트 디렉터리)는 다음과 같습니다.

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Project">
    <RelativePathOnDisk>CSharp\1033\ProjectTemplate1</RelativePathOnDisk>
    <TemplateFileName>ProjectTemplate1.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>ProjectTemplate1</Name>
        <Description>ProjectTemplate1</Description>
        <Icon>ProjectTemplate1.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <SortOrder>1000</SortOrder>
        <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>
        <CreateNewFolder>true</CreateNewFolder>
        <DefaultName>ProjectTemplate1</DefaultName>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```

 제공한 정보는 [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) 요소 동일 하 게 유지 합니다. 합니다 **\<VSTemplateContainer>** 요소 관련 템플릿의.vstemplate 파일을 가리킵니다.

 Visual Studio 2015에서 만든 기본 항목.vstemplate 파일은 다음과 같습니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">
  <TemplateData>
    <Name>ItemTemplate1</Name>
    <Description>ItemTemplate1</Description>
    <Icon>ItemTemplate1.ico</Icon>
    <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>
    <ProjectType>CSharp</ProjectType>
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
    <DefaultName>Class.cs</DefaultName>
  </TemplateData>
  <TemplateContent>
    <References>
      <Reference>
        <Assembly>System</Assembly>
      </Reference>
    </References>
    <ProjectItem ReplaceParameters="true">Class.cs</ProjectItem>
  </TemplateContent>
</VSTemplate>

```

 VSIX 프로젝트를 다시 작성에서 발생 시킨.vstman 파일 (찾을 수 있습니다 VSIX 프로젝트의 매니페스트 디렉터리)는 다음과 같습니다.

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

 제공한 정보는  **\<TemplateData >** 요소 동일 하 게 유지 합니다. 합니다 **\<VSTemplateContainer>** 요소 관련 템플릿의.vstemplate 파일을 가리킵니다.

 .Vstman 파일의 다양 한 요소에 대 한 자세한 내용은 참조 하세요. [Visual Studio 템플릿 매니페스트 스키마 참조](../extensibility/visual-studio-template-manifest-schema-reference.md)합니다.

## <a name="upgrades-for-extensions-installed-with-an-msi"></a>와 함께 설치 된 확장에 대 한 업그레이드를 합니다. MSI

다음 디렉터리와 같은 일반적인 템플릿 위치에 템플릿을 배포 하는 일부 MSI 기반 확장:

- **\<Visual Studio 설치 디렉터리 > \Common7\IDE\\< ProjectTemplates/Itemtemplate\>**

- **\<Visual Studio 설치 디렉터리 > \Common7\IDE\Extensions\\< ExtensionName\>\\< 프로젝트/Itemtemplate\>**

MSI 기반 배포를 수행 하는 확장 프로그램을 하는 경우 템플릿 매니페스트를 수동으로 생성 및 확장 설치에 포함 되어 있는지 확인 해야 합니다. 위에 나열 된.vstman 예제를 비교 하며 [Visual Studio 템플릿 매니페스트 스키마 참조](../extensibility/visual-studio-template-manifest-schema-reference.md)합니다.

프로젝트 및 항목 템플릿에 대 한 별도 매니페스트를 만들고 루트 템플릿 지정 된 대로 위의 디렉터리를 가리키도록 해야 합니다. 확장 및 로캘 당 하나의 매니페스트를 만듭니다.

## <a name="see-also"></a>참고자료

- [템플릿 검색 문제 해결](troubleshooting-template-discovery.md)
- [사용자 지정 프로젝트 및 항목 템플릿 만들기](creating-custom-project-and-item-templates.md)
