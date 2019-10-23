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
ms.openlocfilehash: 8bf0581eee4fade779d89143f4633f1b87d3ce0f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723152"
---
# <a name="support-for-project-and-configuration-properties"></a>프로젝트 및 구성 속성 지원
@No__t_1 IDE (통합 개발 환경)의 **속성** 창에서는 프로젝트 및 구성 속성을 표시할 수 있습니다. 사용자가 응용 프로그램에 대 한 속성을 설정할 수 있도록 고유한 프로젝트 형식에 대 한 속성 페이지를 제공할 수 있습니다.

 **솔루션 탐색기** 에서 프로젝트 노드를 선택한 다음 **프로젝트** 메뉴에서 **속성** 을 클릭 하 여 프로젝트 및 구성 속성이 포함 된 대화 상자를 열 수 있습니다. 이러한 언어에서 파생 된 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 및 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 및 프로젝트 형식에서이 대화 상자는 [일반, 환경, 옵션 대화 상자](../../ide/reference/general-environment-options-dialog-box.md)에서 탭 페이지로 표시 됩니다. 자세한 내용은 [빌드에 없음: 연습: 프로젝트 및 구성 속성 노출 (C#)](https://msdn.microsoft.com/library/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)을 참조 하세요.

 프로젝트에 대 한 관리 패키지 프레임 워크 (MPFProj)는 새 프로젝트 시스템을 만들고 관리 하기 위한 도우미 클래스를 제공 합니다. [프로젝트에 대 한 MPF](https://github.com/tunnelvisionlabs/MPFProj10)에서 소스 코드 및 컴파일 지침-Visual Studio 2013를 찾을 수 있습니다.

## <a name="persistence-of-project-and-configuration-properties"></a>프로젝트 및 구성 속성의 지 속성
 프로젝트 및 구성 속성은 프로젝트 형식 (예: .csproj, .vbproj 및 .csproj)과 연결 된 파일 이름 확장명을 가진 프로젝트 파일에 저장 됩니다. 언어 프로젝트는 일반적으로 템플릿 파일을 사용 하 여 프로젝트 파일을 생성 합니다. 그러나 실제로는 여러 가지 방법으로 프로젝트 형식과 템플릿을 연결할 수 있습니다. 자세한 내용은 [템플릿 디렉터리 설명 (을 참조 하세요. Vsdir) 파일](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).

 프로젝트 및 구성 속성은 템플릿 파일에 항목을 추가 하 여 만듭니다. 그런 다음이 템플릿을 사용 하는 프로젝트 형식을 사용 하 여 만든 모든 프로젝트에서 이러한 속성을 사용할 수 있습니다. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 프로젝트와 MPFProj는 모두 [빌드에 없음:](/previous-versions/visualstudio/visual-studio-2008/ms171452(v=vs.90)) 템플릿 파일에 대해 MSBuild 개요 스키마를 사용 합니다. 이러한 파일에는 각 구성에 대 한 PropertyGroup 섹션이 있습니다. 일반적으로 프로젝트의 속성은 null 문자열로 설정 된 구성 인수를 포함 하는 첫 번째 PropertyGroup 섹션에 저장 됩니다.

 다음 코드에서는 기본 MSBuild 프로젝트 파일의 시작을 보여 줍니다.

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

 이 프로젝트 파일에서 `<Name>` 및 `<SchemaVersion>`는 프로젝트 속성 이며 `<Optimize>`는 구성 속성입니다.

 프로젝트와 프로젝트 파일의 구성 속성을 유지 하는 것은 프로젝트의 책임입니다.

> [!NOTE]
> 프로젝트는 기본값과 다른 속성 값만 유지 하 여 지 속성을 최적화할 수 있습니다.

## <a name="support-for-project-and-configuration-properties"></a>프로젝트 및 구성 속성 지원
 @No__t_0 클래스는 프로젝트 및 구성 속성 페이지를 구현 합니다. @No__t_0의 기본 구현에서는 일반 속성 표에서 사용자에 게 공용 속성을 제공 합니다. @No__t_0 메서드는 프로젝트 속성 표에 대해 `SettingsPage`에서 파생 된 클래스를 선택 합니다. @No__t_0 메서드는 구성 속성 표에 대해 `SettingsPage`에서 파생 된 클래스를 선택 합니다. 프로젝트 형식은 이러한 메서드를 재정의 하 여 적절 한 속성 페이지를 선택 해야 합니다.

 @No__t_0 클래스 및 `Microsoft.VisualStudio.Package.ProjectNode` 클래스는 다음 메서드를 제공 하 여 프로젝트 및 구성 속성을 유지 합니다.

- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` 및 `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` persist 프로젝트 속성입니다.

- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` 하 고 구성 속성을 유지 `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` 합니다.

  > [!NOTE]
  > @No__t_0 및 `Microsoft.VisualStudio.Package.ProjectNode` 클래스의 구현은 MSBuild (`Microsoft.Build.BuildEngine`) 메서드를 사용 하 여 프로젝트 파일에서 프로젝트 및 구성 속성을 가져오고 설정 합니다.

  @No__t_0에서 파생 되는 클래스는 `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges`를 구현 하 고 프로젝트 파일의 프로젝트 또는 구성 속성을 유지 하려면 `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` 해야 합니다.

## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute 및 레지스트리 경로
 @No__t_0에서 파생 된 클래스는 Vspackage 간에 공유 되도록 디자인 되었습니다. VSPackage가 `SettingsPage`에서 파생 된 클래스를 만들 수 있도록 하려면 `Microsoft.VisualStudio.Shell.Package`에서 파생 된 클래스에 `Microsoft.VisualStudio.Shell.ProvideObjectAttribute`를 추가 합니다.

 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]

 특성이 연결 된 VSPackage는 중요 하지 않습니다. @No__t_0에 VSPackage를 등록 하면 만들 수 있는 개체의 CLSID (클래스 id)가 등록 되어 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A>를 호출 하 여 해당 개체를 만들 수 있습니다.

 만들 수 있는 개체의 레지스트리 경로는 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, 단어, CLSID 및 개체 형식의 guid를 결합 하 여 결정 됩니다. @No__t_0 클래스의 guid가 {3c693da2-5bca-49b3-bd95-ffe0a39dd723}이 고 UserRegistryRoot가 HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp 이면 레지스트리 경로는 HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\입니다. 8.0 exp \ CLSID \\ {3c693da2-5bca-49b3-bd95-ffe0a39dd723}.

## <a name="project-and-configuration-property-attributes-and-layout"></a>프로젝트 및 구성 속성 특성 및 레이아웃
 @No__t_0, <xref:System.ComponentModel.DisplayNameAttribute> 및 <xref:System.ComponentModel.DescriptionAttribute> 특성은 일반 속성 페이지에서 프로젝트 및 구성 속성의 레이아웃, 레이블 지정 및 설명을 결정 합니다. 이러한 특성은 옵션에 대 한 범주, 표시 이름 및 설명을 각각 결정 합니다.

> [!NOTE]
> 동일한 특성, SRCategory, LocDisplayName 및 Srcategory은 지역화에 문자열 리소스를 사용 하 고, [프로젝트의 경우 MPF](https://github.com/tunnelvisionlabs/MPFProj10)에 정의 된 Visual Studio 2013 합니다.

 다음과 같은 코드 조각을 생각해 봅시다.

 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]

 구성 속성 페이지의 구성 속성 페이지에 내 **범주**범주에 있는 **내** 구성 속성으로 `MyConfigProp` 구성 속성이 표시 됩니다. 이 옵션을 선택 하면 설명 패널에 설명, **내 설명이**표시 됩니다.

## <a name="see-also"></a>참조
- [속성 페이지 추가 및 제거](../../extensibility/adding-and-removing-property-pages.md)
- [프로젝트](../../extensibility/internals/projects.md)
- [템플릿 디렉터리 설명(.Vsdir) 파일](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
