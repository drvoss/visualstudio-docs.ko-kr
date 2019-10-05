---
title: 프로젝트 및 구성 속성에 대 한 지원 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, supporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f0428e2af6e273e961815ec2521ae26afb5e844d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322395"
---
# <a name="support-for-project-and-configuration-properties"></a>프로젝트 및 구성 속성 지원
합니다 **속성** 창에는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 통합된 개발 환경 (IDE) 프로젝트 및 구성 속성을 표시할 수 있습니다. 사용자는 응용 프로그램에 대 한 속성을 설정할 수 있도록 고유한 프로젝트 형식에 대 한 속성 페이지를 제공할 수 있습니다.

 프로젝트 노드를 선택 하 여 **솔루션 탐색기** 클릭 한 다음 **속성** 에 **프로젝트** 메뉴에서 프로젝트 및 구성을 포함 하는 대화 상자를 열 수 있습니다 속성입니다. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 하 고 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)],이 대화 상자에 탭 페이지로 표시 됩니다. 이러한 언어에서 파생 된 형식 프로젝트를 [일반, 환경, 옵션 대화 상자](../../ide/reference/general-environment-options-dialog-box.md). 자세한 내용은 참조 하세요. [빌드에 없음: 연습: 프로젝트 및 구성 속성을 노출 (C#)](https://msdn.microsoft.com/library/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)합니다.

 프로젝트 (MPFProj)에 대 한 관리 되는 패키지 프레임 워크는 만들고 새로운 프로젝트 시스템을 관리 하기 위한 도우미 클래스를 제공 합니다. 소스 코드와 컴파일 지침을 찾을 수 있습니다 [프로젝트용-Visual Studio 2013 MPF](https://github.com/tunnelvisionlabs/MPFProj10)합니다.

## <a name="persistence-of-project-and-configuration-properties"></a>프로젝트 및 구성 속성의 지 속성
 프로젝트 및 구성 속성은 모든 프로젝트 형식의 경우, 예를 들어 연관 파일 이름 확장명,.csproj,.vbproj, 및.myproj 있는 프로젝트 파일에서 유지 됩니다. 언어 프로젝트는 일반적으로 프로젝트 파일을 생성 하는 템플릿 파일을 사용 합니다. 그러나 실제로 여러 가지 프로젝트 형식 및 서식 파일을 연결 합니다. 자세한 내용은 참조 하세요. [템플릿 디렉터리 설명 (합니다. Vsdir) 파일](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)합니다.

 프로젝트 및 구성 속성은 템플릿 파일에 항목을 추가 하 여 생성 됩니다. 이러한 속성은 다음이 템플릿을 사용 하는 프로젝트 유형을 사용 하 여 만든 프로젝트에 사용할 수 있습니다. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 프로젝트 및 둘 다 사용 하 여 MPFProj는 [빌드에 없음: MSBuild 개요](/previous-versions/visualstudio/visual-studio-2008/ms171452(v=vs.90)) 템플릿 파일에 대 한 스키마입니다. 이러한 파일은 각 구성에 대 한 PropertyGroup 섹션입니다. 프로젝트의 속성 구성 인수가 null 문자열로 설정 하는 첫 번째 PropertyGroup 섹션에서 일반적으로 유지 됩니다.

 다음 코드에서는 기본 MSBuild 프로젝트 파일의 시작 부분을 보여 줍니다.

```
<Project MSBuildVersion="2.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
    <Name>SomeProjectSix</Name>
    <SchemaVersion>2.0</SchemaVersion>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
    <Optimize>false</Optimize>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">
    <Optimize>true</Optimize>
```

 이 프로젝트 파일에서 `<Name>` 하 고 `<SchemaVersion>` 속성은 프로젝트 속성 및 `<Optimize>` 구성 속성입니다.

 이 프로젝트 파일의 프로젝트 및 구성 속성을 유지 하려면 프로젝트의 경우입니다.

> [!NOTE]
> 프로젝트는 기본값에서 다른 유지만 속성 값에 따라 지 속성을 최적화할 수 있습니다.

## <a name="support-for-project-and-configuration-properties"></a>프로젝트 및 구성 속성 지원
 `Microsoft.VisualStudio.Package.SettingsPage` 클래스는 프로젝트 및 구성 속성 페이지를 구현 합니다. 기본 구현을 `SettingsPage` 제네릭 속성 표에 사용자에 게 공용 속성을 제공 합니다. 합니다 `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` 에서 파생 된 클래스를 선택 하는 메서드 `SettingsPage` 프로젝트 속성 그리드의 합니다. 합니다 `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` 에서 파생 된 클래스를 선택 하는 메서드 `SettingsPage` 구성 속성 그리드의 합니다. 프로젝트 형식이 적절 한 속성 페이지를 선택 하려면 이러한 메서드를 재정의 해야 합니다.

 합니다 `SettingsPage` 클래스 및 `Microsoft.VisualStudio.Package.ProjectNode` 클래스는 프로젝트 및 구성 속성을 유지 하기 위해 이러한 메서드를 제공 합니다.

- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` 및 `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` 프로젝트 속성을 유지 합니다.

- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` 및 `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` 구성 속성을 유지 합니다.

  > [!NOTE]
  > 구현 합니다 `Microsoft.VisualStudio.Package.SettingsPage` 및 `Microsoft.VisualStudio.Package.ProjectNode` 클래스를 사용 하 여는 `Microsoft.Build.BuildEngine` (MSBuild) 및 메서드를 가져올 프로젝트 파일에서 프로젝트 및 구성 속성을 설정 합니다.

  파생 클래스 `SettingsPage` 구현 해야 합니다 `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` 및 `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` 프로젝트나 구성 속성이 프로젝트 파일의 유지 되도록 합니다.

## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute 및 레지스트리 경로
 클래스에서 파생 된 `SettingsPage` 은 Vspackage를 공유할 수 있도록 합니다. VSPackage에서 파생 된 클래스를 만들 수 있도록 `SettingsPage`, 추가 `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` 에서 파생 된 클래스에 `Microsoft.VisualStudio.Shell.Package`입니다.

 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]

 특성 연결 되는 VSPackage 중요 하지 않습니다. VSPackage를 사용 하 여 등록 될 때 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]를 만들 수 있는 모든 개체의 클래스 id (CLSID)가 등록 되도록에 대 한 호출 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> 만들 수 있습니다.

 만들 수 있는 개체의 레지스트리 경로 결합 하 여 결정 됩니다 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, 단어, CLSID, 및 개체 유형의 guid입니다. 경우 `MyProjectPropertyPage` 클래스에는 {3c693da2-5bca-49b3-bd95-ffe0a39dd723}의 guid는 UserRegistryRoot HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, 됩니다 하 고 레지스트리 경로 HKEY_CURRENT_USER\Software\Microsoft\VisualStudio 것 \8.0Exp\CLSID\\{3c693da2-5bca-49b3-bd95-ffe0a39dd723}.

## <a name="project-and-configuration-property-attributes-and-layout"></a>프로젝트 및 구성 속성 특성 및 레이아웃
 합니다 <xref:System.ComponentModel.CategoryAttribute>, <xref:System.ComponentModel.DisplayNameAttribute>, 및 <xref:System.ComponentModel.DescriptionAttribute> 특성 결정 레이아웃, 레이블 지정 및 일반 속성 페이지에서 프로젝트 및 구성 속성에 대해 설명 합니다. 이러한 특성 범주를 확인, 각각 표시 이름 및 옵션을 설명 합니다.

> [!NOTE]
> 해당 특성, SRCategory, LocDisplayName, SRDescription, 지역화 문자열 리소스를 사용 하 여 및에 정의 된 [프로젝트용-Visual Studio 2013 MPF](https://github.com/tunnelvisionlabs/MPFProj10)합니다.

 다음과 같은 코드 조각을 생각해 봅시다.

 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]

 `MyConfigProp` 구성 속성으로 구성 속성 페이지에 나타납니다 **구성 속성에 내** 범주에서 **My Category**합니다. 옵션을 선택 하는 경우 설명을 **내 설명**, 설명 창에 표시 됩니다.

## <a name="see-also"></a>참고 항목
- [속성 페이지 추가 및 제거](../../extensibility/adding-and-removing-property-pages.md)
- [프로젝트](../../extensibility/internals/projects.md)
- [템플릿 디렉터리 설명(.Vsdir) 파일](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
