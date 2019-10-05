---
title: Visual Studio 2015 SDK의 새로운 기능 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1d51474f2e242f764a84edaa9f2712418c859460
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63408705"
---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>새로운&#39;Visual Studio 2015 SDK의 새로운
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio SDK는 Visual Studio 2015, 업데이트 하는 Visual Studio 2015 및 Visual Studio 2017에 대 한 다음 새로운 및 업데이트 된 기능.

## <a name="visual-studio-2017"></a>Visual Studio 2017

Visual Studio 2017부터 사용자 지정 프로젝트 및 항목 템플릿에 대 한 검사는 더 이상 수행 됩니다. 대신 확장 이러한 서식 파일의 설치 위치를 설명 하는 템플릿 매니페스트 파일을 제공 해야 합니다. VSIX 확장을 업데이트 하려면 Visual Studio 2017을 사용할 수 있습니다. MSI를 사용 하 여 확장을 배포 하는 경우 손으로 템플릿 매니페스트 파일을 생성 해야 합니다. 자세한 내용은 [사용자 지정 프로젝트 업그레이드 및 Visual Studio 2017에 대 한 항목 템플릿](/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017?view=vs-2015)합니다. 템플릿 매니페스트 스키마에 설명 되어 있습니다 [Visual Studio 템플릿 매니페스트 스키마 참조](/visualstudio/extensibility/visual-studio-template-manifest-schema-reference)합니다.

## <a name="vs-2015-sdk-update-1"></a>VS 2015 SDK 업데이트 1
 업데이트 1에는 색 테마 및 Visual Studio 이미지 서비스에 잘 작동 하 여 확장 하는 데는 도구가 포함 됩니다.

 이러한 항목은는 [VSSDK 유틸리티](../extensibility/internals/vssdk-utilities.md) 섹션:

- 합니다 [색 테마 도구](../extensibility/internals/color-theming-tools.md) 만들고 Visual Studio에 대 한 사용자 지정 색을 편집할 수 있도록 합니다.

- 합니다 [이미지 서비스 도구](../extensibility/internals/image-service-tools.md) Visual Studio 이미지에 대 한 매니페스트 파일을 작업할 수 있도록 합니다.

## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Visual Studio에 Visual Studio SDK를 추가 하는 새로운 방법
 Visual Studio 2015부터 Visual Studio SDK를 별도로 다운로드할 필요가 없습니다. 대신 일반 설치 프로세스의 일부로 설치할 수 있습니다 하거나 나중에 설치할 수 있습니다. VSIX 솔루션을 만들거나 열 때 Visual Studio는 Visual Studio 확장성 도구를 설치 하도록 묻습니다. 자세한 내용은 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)합니다.

## <a name="new-ways-of-creating-extensions"></a>확장을 만드는 새로운 방법
 사용 중인 프로그래밍 언어에 따라 확장을 만들기 위한 다른 옵션을 Visual Studio 2015 SDK에서 시작 해야 합니다.

### <a name="visual-c-and-visual-basic"></a>Visual C# 및 Visual Basic
 C# 및 Visual Basic의 경우에 Vspackage, 메뉴 명령, 도구 창, 편집기 분류자, 편집기 도구 영역 및 편집기 여백 확장을 만들 수 있도록 하는 프로젝트 항목 템플릿의 전체 범위. 이러한 표준 VSIX 프로젝트 중 일부 또는 모두를 추가할 수 있습니다. 자세한 내용은 다음을 참조하세요.

- [메뉴 명령을 사용하여 확장 만들기](../extensibility/creating-an-extension-with-a-menu-command.md)

- [도구 창으로 확장 만들기](../extensibility/creating-an-extension-with-a-tool-window.md)

- [편집기 항목 템플릿을 사용하여 확장 만들기](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- [로 확장 만들기](../extensibility/creating-an-extension-with-a-vspackage.md)

     VSPackage 마법사는 더 이상 C# 또는 Visual Basic에서 확장을 만듭니다.

### <a name="c"></a>C++
 에 대 한 C++를 VSPackage 마법사 지원 메뉴 명령, 도구 창 및 사용자 지정 편집기입니다. 이 **새 프로젝트** 대화 상자에서 **시각적 C++ / 확장성**합니다.

## <a name="vs-sdk-reference-assemblies-via-nuget"></a>NuGet 통해 VS SDK 참조 어셈블리
 향상 된 이식성 및 확장성 프로젝트의 공유에 대 한 VS SDK 참조 어셈블리의 NuGet 버전을 사용할 수 있습니다.  다운로드할 수 있습니다 [nuget.org](http://www.nuget.org) 공개한 [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) 프로젝트 또는 Visual Studio를 통해 솔루션을 쉽게 추가할 수 있습니다 및 **참조 / 관리 NuGet 패키지** 대화 합니다. 특정 확장성 어셈블리에 대 한 개별 참조를 추가 하거나 VS SDK를 모두 한 번에 VS SDK를 사용 하 여 어셈블리 참조를 추가할 수 있습니다 [메타 패키지가](http://www.nuget.org/packages/VSSDK_Reference_Assemblies)합니다. NuGet에 대 한 자세한 내용은 참조 하세요 [NuGet 개요](http://docs.nuget.org/) 하 고 [대화 상자를 사용 NuGet 패키지 관리](http://docs.nuget.org/Consume/Package-Manager-Dialog)합니다.

 VS SDK 참조 어셈블리의 NuGet 버전을 사용 하면 다른 사용자를 열고 프로젝트를 빌드 하려는 VS SDK를 설치할 필요가 없습니다.  NuGet 참조 어셈블리 및 VS SDK 빌드 도구를 자동으로 해당 프로젝트에 대 한 컴퓨터에 설치 됩니다.

 VS SDK 항목 템플릿은 해당 참조에 대해 NuGet을 사용 하 고 기본적으로 NuGet의 혜택을 받을 수 있도록 도구를 빌드합니다.

> [!NOTE]
> 참조 어셈블리를 설치 하는 VS SDK를 사용 하 여 프로젝트와 함께 할 수 있습니다 (아래에 있는 \<Visual Studio 설치 위치 > \ VSSDK\VisualStudioIntegration\Common\Assemblies) 되도록 기존 확장성 프로젝트 필요 하지 않습니다 NuGet 패키지를 사용 하도록 업그레이드 합니다.  프로젝트 **참조] / [참조 추가** 대화 계속 참조 어셈블리를 설치 하는 VS SDK를 사용 합니다.
>
> NuGet을 사용 하도록 기존 프로젝트를 수정 하려는 경우 [방법: Visual Studio 2015에서 Vspackage로](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) 확장성 프로젝트에 NuGet 패키지 업데이트에 대 한 섹션이 있는 합니다.

## <a name="light-bulbs"></a>전구
 확장 프로그램 코드를 작성 하는 가장 흥미로운 새로운 방법 중 하나는 Roslyn 프로젝트에서 제공 됩니다. 자세한 내용은 [Roslyn](https://github.com/dotnet/Roslyn)합니다.

 전구는 VSSDK 함께 제공 되는 새로운 기능입니다. 기본 제공 코드 분석기에 의해 식별 된 문제에 대 한 수정 또는 코드 리팩터링 작업 집합을 표시 하도록 확장 하는 Visual Studio 편집기에 사용 되는 아이콘입니다. 자세한 내용은 [연습: Displaying Light Bulb Suggestions](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)합니다.

## <a name="updated-user-experience-guidelines"></a>업데이트 된 사용자 환경 지침
 Visual Studio에 대 한 새 확장 또는 기능을 디자인? 업데이트 및 확장 된 확인해 [Visual Studio User Experience Guidelines](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)합니다.  확인할 수는 [토큰 색](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md), [글꼴 크기](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)를 [대화 상자 레이아웃 사양](../extensibility/ux-guidelines/layout-for-visual-studio.md), 및 Visual Studio를 사용 하 여 새 UI를 원활 하 게 통합 하는 데 필요한 다른 지침.
