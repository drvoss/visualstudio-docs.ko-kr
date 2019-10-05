---
title: 대체 가능 매개 변수 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, tokens
- tokens [SharePoint development in Visual Studio]
- replaceable parameters [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, replaceable parameters
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload: office
ms.openlocfilehash: 165ef1256a0150e0942d85c4f876c8b3f5e15c72
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63422910"
---
# <a name="replaceable-parameters"></a>대체 가능 매개 변수
  대체 가능 매개 변수 또는 *토큰*, 실제 값을 갖는 디자인 타임에 알려지지 않은 SharePoint 솔루션 항목에 대 한 값을 제공 하려면 프로젝트 파일 내에서 사용할 수 있습니다. 표준 비슷합니다 함수에서 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 템플릿 토큰입니다. 자세한 내용은 [템플릿 매개 변수](../ide/template-parameters.md)합니다.

## <a name="token-format"></a>토큰 형식
 토큰 시작 및 달러 기호 ($) 문자로 끝나야 합니다. 배포에서 사용 되는 모든 토큰 값으로 대체 됩니다 실제 프로젝트는 SharePoint 솔루션 패키지를 패키지화 하는 경우 (*.wsp* 파일). 예를 들어, 토큰 **$SharePoint.Package.Name$** "테스트 SharePoint 패키지" 문자열을 해결할 수 있습니다.

## <a name="token-rules"></a>토큰 규칙
 토큰에 다음 규칙이 적용 됩니다.

- 줄의 아무 곳 이나 토큰을 지정할 수 있습니다.

- 토큰 여러 줄으로 나누어 입력할 수 없습니다.

- 같은 줄에 동일한 파일에서 동일한 토큰을 두 번 이상 지정할 수 있습니다.

- 같은 줄에 서로 다른 토큰을 지정할 수 있습니다.

  이러한 규칙을 따르지 않는 토큰 무시 되 고 경고 또는 오류를 발생 하지 않습니다.

  토큰 문자열 값으로 대체 매니페스트를 변환한 후 즉시 수행 됩니다. 이 대체 토큰을 사용 하 여 매니페스트 템플릿을 편집할 수 있습니다.

### <a name="token-name-resolution"></a>토큰 이름 확인
 대부분의 경우에서 토큰 포함 된 위치에 관계 없이 특정 값을 확인 합니다. 그러나 토큰에 패키지 또는 기능에 관련 되는 토큰의 값 포함 되어 있습니다.에 따라 다릅니다. 예를 들어 기능이 상태인 경우, 토큰 패키지 `$SharePoint.Package.Name$` "Package A." 값을 확인 동일한 기능 인지 B 패키지에 다음 `$SharePoint.Package.Name$` "패키지 b" 확인

## <a name="tokens-list"></a>토큰 목록
 다음 표에서 사용 가능한 토큰을 보여 줍니다.

|이름|설명|
|----------|-----------------|
|$SharePoint.Project.FileName$|이름을 포함 하는 프로젝트 파일을 같은 *NewProj.csproj*합니다.|
|$SharePoint.Project.FileNameWithoutExtension$|파일 이름 확장명 없이 포함 하는 프로젝트 파일의 이름입니다. 예를 들어, "NewProj"가 있습니다.|
|$SharePoint.Project.AssemblyFullName$|포함 하는 프로젝트의 표시 이름 (강력한 이름)의 어셈블리를 출력 합니다.|
|$SharePoint.Project.AssemblyFileName$|포함 하는 프로젝트의 출력 어셈블리의 이름입니다.|
|$SharePoint.Project.AssemblyFileNameWithoutExtension$|이름을 포함 하는 프로젝트의 파일 이름 확장명을 제외한 어셈블리의 출력입니다.|
|$SharePoint.Project.AssemblyPublicKeyToken$|포함 하는 프로젝트의 공개 키 토큰을 문자열로 변환 된 어셈블리의 출력입니다. ("x2"에서 16 자 16 진수 형식입니다.)|
|$SharePoint.Package.Name$|포함 하는 패키지의 이름입니다.|
|$SharePoint.Package.FileName$|포함 하는 패키지 정의 파일의 이름입니다.|
|$SharePoint.Package.FileNameWithoutExtension$|포함 하는 패키지 정의 파일의 확장명을 제외한 이름입니다.|
|$SharePoint.Package.Id$|파일의 SharePoint ID를 포함 하는 패키지입니다. 둘 이상의 패키지에는 기능을 사용 하는 경우이 값이 변경 됩니다.|
|$SharePoint.Feature.FileName$|이름을 포함 하는 정의 파일의 기능을 같은 *Feature1.feature*합니다.|
|$SharePoint.Feature.FileNameWithoutExtension$|파일 이름 확장명이 없는 기능 정의 파일의 이름입니다.|
|$SharePoint.Feature.DeploymentPath$|패키지에 기능을 포함 하는 폴더의 이름입니다. 이 토큰 기능 디자이너에서 "배포 경로" 속성에는 것과 같습니다. 값의 예는 "Project1_Feature1"입니다.|
|$SharePoint.Feature.Id$|포함 된 기능의 SharePoint ID입니다. 이 토큰을 모든 기능 수준 토큰을 사용 하 여 기능을 통해 패키지에 포함 된 파일에 의해서만 사용 될 수 없습니다 직접 추가 기능을 외부에서 패키지를.|
|$SharePoint.ProjectItem.Name$|가져온 (해당 파일 이름이 아님), 프로젝트 항목의 이름을 **ISharePointProjectItem.Name**합니다.|
|$SharePoint.Type.\<GUID>.AssemblyQualifiedName$|토큰의 [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)]와 일치하는 형식의 정규화된 어셈블리 이름입니다. [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)]의 형식은 소문자이며 Guid.ToString("D") 형식과 일치합니다(즉, xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|
|$SharePoint.Type.\<GUID>.FullName$|토큰에 GUID와 일치 하는 형식의 전체 이름입니다. GUID의 형식은 소문자 이며 Guid.ToString("D") 형식에 해당 (즉, xxxxxxxx xxxx-xxxx-자).|

## <a name="add-extensions-to-the-token-replacement-file-extensions-list"></a>토큰 바꾸기 파일 확장명 목록에 확장 추가
 기본적으로 패키지에 포함 된 항목을 SharePoint 프로젝트에 속하는 모든 파일에 토큰 이론적으로 사용할 수 있지만 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 패키지 파일, 매니페스트 파일 및 파일 확장명이 있는 경우에 토큰을 검색 합니다.

- [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]

- ASCX

- ASPX

- 웹 파트

- DWP

  이러한 확장에 의해 정의 됩니다는 `<TokenReplacementFileExtensions>` 에 있는 Microsoft.VisualStudio.SharePoint.targets 파일의 요소는... \\< 프로그램 파일\>\MSBuild\Microsoft\VisualStudio\v11.0\SharePointTools 폴더입니다.

  그러나 목록에 추가 파일 확장명을 추가할 수 있습니다. 추가 된 `<TokenReplacementFileExtensions>` 앞에 정의 된 SharePoint 프로젝트 파일에서 모든 PropertyGroup 요소는 \<가져오기 > SharePoint 대상 파일의 합니다.

> [!NOTE]
> 토큰 교체는 프로젝트를 컴파일한 후 발생 때문에 컴파일되는와 같은 파일 형식의 파일 확장명에 추가 해서는 안 *.cs*를 *.vb* 하거나 *.resx*합니다. 토큰은 컴파일되지 않는 파일에만 대체 됩니다.

 예를 들어, 파일 이름 확장명을 추가 하려면 (*.myextension* 하 고 *.yourextension*) 토큰 대체 파일 이름 확장명의 목록에 추가한 다음 프로젝트에 (*.csproj* ) 파일:

```xml
<Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
    <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
.
.
.
    <!-- Define the following property to add your extension to the list of token replacement file extensions.  -->
<TokenReplacementFileExtensions>myextension;yourextension</TokenReplacementFileExtensions>
</PropertyGroup>
```

 대상에 직접 확장을 추가할 수 있습니다 (*.targets*) 파일입니다. 그러나 뿐만 아니라 확장 변경 로컬 시스템에 패키지 하는 모든 SharePoint 프로젝트 확장명 목록에 추가 사용자 고유의 합니다. 시스템에서 유일한 개발자 또는 대부분의 프로젝트에 필요한 경우에이 확장 편리할 수 있습니다. 그러나 시스템 관련 인이 방법은 이식 가능 하지 않습니다.이 고 따라서 것이 좋습니다 때문에 추가한 확장 프로젝트 파일에 대신 합니다.

## <a name="see-also"></a>참고자료
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
