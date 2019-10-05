---
title: 시작 확장을 개발 하는 중 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6d8050ea7447a67f50f42157d57c17d3f1f8a329
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68160592"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Visual Studio Extensions 확장 기능 개발 시작
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

전에 Visual Studio 확장을 써 본 적, 아마도 경우 몇 가지 질문입니다. 몇 가지 가장 일반적인 위협을 여기 나열 되어 있습니다. 피드백 단추를 사용 하 여 원하는 정보를 표시 되지 않는 경우 (**이 페이지가 도움이 되었나요?** 화면의 맨 아래에서) 원하는 요청 합니다.

## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>소프트웨어 Visual Studio 확장 개발 하나요?
 Visual Studio 확장을 개발 하려면 Visual Studio 2015 외에도 Visual Studio 2015 SDK를 설치 해야 합니다.   일반 설치의 일부로 Visual Studio 2015 SDK를 설치할 수 있습니다 하거나 나중에 설치할 수 있습니다. Visual Studio SDK를 설치 하는 방법에 대 한 자세한 내용은 참조 하세요. [Visual Studio SDK](../extensibility/visual-studio-sdk.md)합니다.

## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>어떤 종류의 Visual Studio 확장을 사용 하 여 합니까?
 무궁무진 하더라도 다른 Visual Studio 확장을 상상 일 뿐입니다. 물론, 대부분의 확장 코드를 작성 하는와 관련이 없지만 경우 없는 합니다. 종류의 확장을 만들 수 있는 몇 가지 예는 다음과 같습니다.

- 구문 색 지정, IntelliSense 및 컴파일러 및 디버그 지원을 사용 하 여 Visual Studio에 포함 되지 않은 언어에 대 한 지원

- 추가 템플릿, 코드 리팩터링, 새 대화 상자 또는 도구 창을 사용 하 여 핵심을 확장 하는 생산성 도구 IDE 환경

- 데이터 디자인 또는 클라우드 지원 등의 시나리오에 대 한 도메인 관련 디자이너

  확장의 예제를 확인 합니다 [Visual Studio Marketplace](https://marketplace.visualstudio.com/)합니다. 또한 살펴보겠습니다 수 [Visual Studio 오픈 소스 확장](https://github.com/Microsoft/extendvs/blob/master/CommunityExtensions.md)합니다.

## <a name="which-visual-studio-features-can-i-extend"></a>Visual Studio 기능을 확장할 수 있나요?
 이론적으로 Visual Studio의 거의 모든 부분을 확장할 수 있습니다: 메뉴, 도구 모음, 명령, windows, 솔루션, 프로젝트, 편집기 및 등입니다.

 실제로 대부분의 사람들이 확장 기능 명령, 메뉴 및 도구 모음, windows, IntelliSense 및 프로젝트는 발견 했습니다. 관련 섹션에 대 한 링크는 다음과 같습니다.

- [메뉴 및 명령 확장](../extensibility/extending-menus-and-commands.md): Visual Studio 메뉴 및 도구 모음에 사용자 고유의 항목을 추가 합니다. 새 Visual Studio 기능 또는 자신의 외부 도우미 응용 프로그램을 시작 하 고 사용할 수 있습니다. 메뉴 항목에 대 한 사용자 지정 바로 가기 키를 제공할 수도 있습니다.

- [확장 및 사용자 지정 도구 Windows](../extensibility/extending-and-customizing-tool-windows.md): 기존 도구 창 확장 또는 사용자 고유의 도구 창을 만들 수 있습니다. 예를 들어, 새 속성을 추가할 수 있습니다 합니다 **속성**, 또는 추가 기능을 추가 하는 새 도구 창을 만들 수 있습니다.

- [편집기 및 언어 서비스 확장](../extensibility/editor-and-language-service-extensions.md): 새 프로그래밍 언어에 대 한 지원을 만들거나 사용자 고유의 사용자 지정 Visual Studio 언어에 대 한 제공 되는 IntelliSense를 추가 합니다. 새 문 완성, 제안 및 QuickInfo 도구 설명 표시를 새로 만들 수 있습니다. 전구를 사용 하 여 리팩터링 제안을 추가 하 고 새 프로그래밍 언어를 지원 하기 위해 코드를 수정 합니다.

- [프로젝트 확장](../extensibility/extending-projects.md)

- [사용자 설정 및 옵션 확장](../extensibility/extending-user-settings-and-options.md)

- [속성 및 속성 창 확장](../extensibility/extending-properties-and-the-property-window.md)

- [Visual Studio의 다른 부분 확장](../extensibility/extending-other-parts-of-visual-studio.md)

- [Visual Studio Shell(격리)](../extensibility/visual-studio-isolated-shell.md)

## <a name="BKMK_ProjectTemplate"></a> 프로젝트 템플릿은 무엇 VSSDK에서 제공 하는?
 확장의 두 가지 주요 유형은 Vspackage 및 MEF 확장입니다. 일반적으로 VSPackage 확장을 사용 하거나 명령, 도구 창 및 프로젝트를 확장 하는 확장에 사용 됩니다. MEF 확장은 확장 하거나 Visual Studio 편집기 사용자 지정 하는 데 사용 됩니다.

 Visual C# 및 Visual Basic 확장용 VSSDK 메뉴 명령, 도구 창 및 편집기 확장을 만드는 새 항목 템플릿을 함께 사용할 수 있는 빈 VSIX 프로젝트 템플릿을 제공 합니다. 자세한 내용은 [What's New in Visual Studio 2015 SDK](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md)합니다. 또한 다른 사용자에 게 배포에 대 한이 서식 파일을 패키지 프로젝트 템플릿, 코드 조각 및 기타 아티팩트를 사용할 수 있습니다.

 에 대 한 C++를 VSPackage 마법사는 메뉴 명령, 도구 창 및 사용자 지정 편집기를 추가 하는 코드를 제공 합니다.

 격리 셸 템플릿 버전의 브랜딩 및 사용자 고유의으로 배포할 수 있는 Visual Studio shell에서 확장 패키지에 사용 됩니다. 다음 항목에서는 각 유형의 확장을 사용 하 여 시작 하는 방법을 보여 줍니다.

- 메뉴 명령: [메뉴 명령을 사용하여 확장 만들기](../extensibility/creating-an-extension-with-a-menu-command.md)

- 도구 창: [도구 창으로 확장 만들기](../extensibility/creating-an-extension-with-a-tool-window.md)

- 편집기 확장: [편집기 항목 템플릿을 사용하여 확장 만들기](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- 기본 Vspackage의 경우: [로 확장 만들기](../extensibility/creating-an-extension-with-a-vspackage.md)

- VSIX 프로젝트 템플릿: [VSIX 프로젝트 템플릿 시작](../extensibility/getting-started-with-the-vsix-project-template.md)

- Visual Studio 격리 셸: [연습: 기본 격리 셸 애플리케이션 만들기](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)

## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Visual Studio 처럼 my 확장 가져오기
 확장에 대 한 UI를 디자인 하기 위한 유용한 팁을 얻을 [Visual Studio User Experience Guidelines](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)합니다.

## <a name="where-can-i-find-examples-of-vssdk-code"></a>VSSDK 코드 예제는 어디서 찾을 수 있습니까?
 이전 섹션에서 나열 된 링크의 각 특정 기능을 구현 하는 방법을 보여 주는 단계별 연습을 있습니다. 찾을 수도 있습니다 오픈 소스에서 GitHub에서 VSSDK 샘플 [Visual Studio 샘플](https://aka.ms/vs2015sdksamples)합니다.

## <a name="how-can-i-distribute-my-extension"></a>My 확장을 배포할 수는 방법
 다른 컴퓨터에 확장을 설치 하거나.vsix 파일을 두 번 클릭 하 여 설치 파일로 친구에 게 보낼 수 있습니다. VSIX 패키지에 대 한 자세한 내용을 확인할 수 있습니다 [Visual Studio 확장 전달](../extensibility/shipping-visual-studio-extensions.md)합니다.

 또한 많은 수의 Visual Studio 고객에 게 표시 하는 Visual Studio 갤러리에서 확장 프로그램을 게시할 수 있습니다. 갤러리에 대 한 확장 패키지의 예제를 참조 하세요. [연습: Visual Studio 확장 기능 게시](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)합니다. 갤러리에 게시 하기 위해 수행 해야 하는 방법에 대 한 자세한 내용은 참조 하세요. [제품 및 Visual Studio 용 확장](https://visualstudiogallery.msdn.microsoft.com/)합니다.
