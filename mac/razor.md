---
title: Razor
description: Mac용 Visual Studio의 ASP.NET Core 앱에서 Razor 지원에 대한 정보
author: sayedihashimi
ms.author: sayedha
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: F898CB6E-05ED-44CD-8DB6-427B2592CCC6
ms.openlocfilehash: a66a31d2c63fcb0e2adc4554c49a76c727f9a288
ms.sourcegitcommit: cf8c0fef2b9690595e99ce3802586cdd55fd37c2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107923"
---
# <a name="razor"></a>Razor

Mac용 Visual Studio는 IntelliSense 및 *.cshtml* 파일에서 구문 강조 표시를 비롯한 Razor 편집을 지원합니다.

![Mac용 Visual Studio의 Razor 편집](media/razor-editor.png)

이 가이드에서는 첫 번째 Razor 웹앱 만들기에 대해 소개합니다. 자세한 지침을 보려면 [.NET Core 설명서의 Razor Pages](/aspnet/core/razor-pages/index)를 참조하세요.

## <a name="creating-a-new-razor-project"></a>새 Razor 프로젝트 만들기

* 새 프로젝트를 만들려면 시작 화면에서 **새로 만들기**를 선택합니다.

![Mac용 Visual Studio 새 프로젝트](media/razor-new.png)

* 새 프로젝트 대화 상자에서 **.NET Core** > **앱** > **웹 애플리케이션**으로 이동하여 **다음** 단추를 선택합니다.

![Razor 프로젝트 템플릿](media/razor-new-project1.png)

* 필요한 .NET Core 대상 프레임워크(2.2 이상 권장)를 선택하고 **다음**을 선택합니다.  프로젝트 이름을 선택하고 필요한 경우 git 지원을 추가합니다. **만들기**를 선택하여 프로젝트를 만듭니다.

![Razor 프로젝트 이름](media/razor-new-project2.png)

Mac용 Visual Studio에서 프로젝트가 코드 레이아웃으로 열립니다.

* **Cmd-Opt-F5**를 사용하여 디버깅하지 않고 프로젝트를 실행합니다.

Visual Studio에서 [Kestral](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel)을 시작하고 `https://localhost:5001`에 브라우저를 실행하여 첫 번째 Razor 웹앱을 표시합니다.

![Safari의 Razor 웹앱](media/razor-webapp.png)

## <a name="project-anatomy"></a>프로젝트 분석

Razor 웹앱은 다음 구성 요소로 구성됩니다.

### <a name="pages-folder"></a>페이지 폴더

프로젝트 내의 Pages 폴더에서 웹 페이지를 해당 숨겨진 코드와 함께 찾을 수 있습니다.
* *HTML 표시 및 Razor 구문의 경우 *.cshtml* 파일.
* *페이지 이벤트 처리를 위한 C# 코드 숨김의 경우 *.cshtml.cs* 파일.

지원 파일에는 밑줄로 시작하는 이름이 있습니다. 예를 들어 _Layout.cshtml 파일은 모든 페이지에 공통되는 UI 요소를 구성합니다. 이 파일은 페이지 맨 위에 있는 탐색 메뉴를 설정하고 페이지 맨 아래에 저작권 표시를 설정합니다. 자세한 내용은 [ASP.NET Core의 레이아웃](https://docs.microsoft.com/aspnet/core/mvc/views/layout)을 참조하세요.

### <a name="launch-settings"></a>시작 설정

*launchSettings.json* 파일은 IIS 설정, 애플리케이션 URL 및 기타 관련 설정을 포함합니다.

### <a name="app-settings"></a>앱 설정

*appSettings,json* 파일은 연결 문자열과 같은 구성 데이터를 포함합니다.

구성에 대한 자세한 내용은 [ASP.NET 가이드의 구성](https://docs.microsoft.com/aspnet/core/fundamentals/configuration/index)을 참조하세요.

### <a name="wwwroot-folder"></a>wwwroot 폴더

HTML 파일, JavaScript 파일 및 CSS 파일과 같은 정적 파일을 포함합니다. 자세한 내용은 [ASP.NET Core의 정적 파일](https://docs.microsoft.com/aspnet/core/fundamentals/static-files)을 참조하세요.

### <a name="programcs"></a>Program.cs

프로그램의 진입점을 포함합니다. 자세한 내용은 [ASP.NET Core 웹 호스트](https://docs.microsoft.com/aspnet/core/fundamentals/host/web-host)를 참조하세요.

### <a name="startupcs"></a>Startup.cs

쿠키에 대한 동의 필요 여부 등 앱 동작을 구성하는 코드를 포함합니다. 자세한 내용은 [ASP.NET Core에서 앱 시작](https://docs.microsoft.com/aspnet/core/fundamentals/startup)을 참조하세요.

## <a name="see-aso"></a>참조

Razor 웹앱 만들기에 대한 포괄적인 지침은 [ASP.NET Core의 Razor Pages 소개](https://docs.microsoft.com/aspnet/core/razor-pages/index)를 참조하세요.
