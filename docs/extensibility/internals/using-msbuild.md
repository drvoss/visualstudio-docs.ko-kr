---
title: MSBuild 사용 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab089a7a37acb377a043ec2c3a4db2c6538e6312
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344708"
---
# <a name="using-msbuild"></a>MSBuild 사용
MSBuild를 완벽 하 게 빌드할 수, 작업, 빌드 및 빌드 구성 프로젝트 항목을 설명 하는 프로젝트 파일 만들기에 대 한 잘 정의 되 고 확장 가능한 XML 형식으로 제공 합니다.

## <a name="general-msbuild-considerations"></a>일반 MSBuild 고려 사항
 MSBuild 프로젝트 파일, 예를 들어 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] .csproj 및 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] .vbproj 파일을 빌드 시 사용 되지만 디자인 타임에 사용 되는 데이터를 포함할 수 있는 데이터를 포함 합니다. 빌드 시간 데이터는 포함 하 여 MSBuild 기본 요소를 사용 하 여 저장 됩니다 [Item 요소 (MSBuild)](../../msbuild/item-element-msbuild.md) 하 고 [Property 요소 (MSBuild)](../../msbuild/property-element-msbuild.md)합니다. 프로젝트 형식 및 모든 관련된 프로젝트 하위 형식에 관련 된 데이터는 디자인 타임 데이터에 대 한 예약 된 자유 형식 XML에 저장 됩니다.

 MSBuild는 구성 개체에 대 한 기본 지원을 없지만 구성 관련 데이터를 지정 하는 것에 대 한 조건부 특성을 제공 하는 합니다. 예를 들어:

```xml
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>
```

 조건부 특성에 대 한 자세한 내용은 참조 하세요. [조건부 구문](../../msbuild/msbuild-conditional-constructs.md)합니다.

### <a name="extending-msbuild-for-your-project-type"></a>MSBuild 프로젝트 형식에 대 한 확장
 MSBuild 인터페이스 및 Api의 이후 버전에서 변경 사항이 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]합니다. 따라서 것에서 변경 내용을 보호를 제공 하기 때문에 관리 되는 패키지 프레임 워크 (MPF) 클래스를 사용 하는 것이 좋습니다.

 프로젝트 (MPFProj)에 대 한 관리 되는 패키지 프레임 워크는 만들고 새로운 프로젝트 시스템을 관리 하기 위한 도우미 클래스를 제공 합니다. 소스 코드와 컴파일 지침을 찾을 수 있습니다 [프로젝트용-Visual Studio 2013 MPF](https://github.com/tunnelvisionlabs/MPFProj10)합니다.

 프로젝트별 MPF 클래스는 다음과 같습니다.

|클래스|구현|
|-----------|--------------------|
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|

 `Microsoft.VisualStudio.Package.ProjectElement` 클래스는 MSBuild 항목에 대 한 래퍼입니다.

#### <a name="single-file-generators-vs-msbuild-tasks"></a>단일 파일 생성기 vs입니다. MSBuild 작업
 단일 파일 생성기 디자인 타임에 액세스할 수 있고 디자인 타임 및 빌드 시간에 MSBuild 작업을 사용할 수 있습니다. 최대 유연성을 변환 하 고 코드를 생성 하려면 따라서 MSBuild 작업을 사용 합니다. 자세한 내용은 [사용자 지정 도구](../../extensibility/internals/custom-tools.md)합니다.

## <a name="see-also"></a>참고 항목
- [MSBuild 참조](../../msbuild/msbuild-reference.md)
- [MSBuild](../../msbuild/msbuild.md)
- [사용자 지정 도구](../../extensibility/internals/custom-tools.md)