---
title: Visual Studio Desktop Express 2017 워크로드 및 구성 요소 ID
titleSuffix: ''
description: 작업 및 구성 요소 ID를 사용하여 명령줄로 Visual Studio를 설치하거나 VSIX 매니페스트에서 종속성으로 지정합니다.
keywords: ''
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.date: 2/12/2019
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: include
ms.openlocfilehash: 4da1fcce5d959c3c5a46902dc4e425524b041b10
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62422761"
---
## <a name="express-for-windows-desktop"></a>Express for Windows Desktop

**ID:** Microsoft.VisualStudio.Workload.WDExpress

**설명:** 구문 인식 코드 편집, 소스 코드 제어, 작업 항목 관리로 WPF, WinForms, Win32와 같은 네이티브 및 관리 애플리케이션을 빌드합니다. C#, Visual Basic, Visual C++에 대한 지원이 포함됩니다.

### <a name="components-included-by-this-workload"></a>이 작업에 포함되는 구성 요소

구성 요소 ID | name | 버전 | 종속성 유형
--- | --- | --- | ---
Microsoft.Component.ClickOnce | ClickOnce 게시 도구 | 15.8.27825.0 | 필수
Microsoft.Component.HelpViewer | 도움말 뷰어 | 15.9.28307.421 | 필수
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | 필수
Microsoft.Component.VC.Runtime.OSSupport | UWP용 Visual C++ 런타임 | 15.6.27406.0 | 필수
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 타기팅 팩 | 15.6.27406.0 | 필수
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 타기팅 팩 | 15.6.27406.0 | 필수
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 타기팅 팩 | 15.6.27406.0 | 필수
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | 필수
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 타기팅 팩 | 15.6.27406.0 | 필수
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 타기팅 팩 | 15.6.27406.0 | 필수
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 타기팅 팩 | 15.6.27406.0 | 필수
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 개발 도구 | 15.8.27825.0 | 필수
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 개발 도구 | 15.6.27406.0 | 필수
Microsoft.VisualStudio.Component.Common.Azure.Tools | 연결 및 게시 도구 | 15.9.28107.0 | 필수
Microsoft.VisualStudio.Component.CoreEditor | Visual Studio 핵심 편집기 | 15.8.27729.1 | 필수
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 도구 | 15.6.27406.0 | 필수
Microsoft.VisualStudio.Component.NuGet | NuGet 패키지 관리자 | 15.9.28016.0 | 필수
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 및 Visual Basic Roslyn 컴파일러 | 15.6.27309.0 | 필수
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 및 Visual Basic | 15.8.27729.1 | 필수
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL 런타임 | 15.6.27406.0 | 필수
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server용 CLR 데이터 형식 | 15.0.26208.0 | 필수
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server 명령줄 유틸리티 | 15.0.26208.0 | 필수
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server 지원용 데이터 원본 | 15.0.26621.2 | 필수
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | 필수
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | 필수
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | 필수
Microsoft.VisualStudio.Component.Static.Analysis.Tools | 정적 분석 도구 | 15.0.26208.0 | 필수
Microsoft.VisualStudio.Component.TextTemplating | 텍스트 템플릿 변환 | 15.0.26208.0 | 필수
Microsoft.VisualStudio.Component.VC.CLI.Support | C++/CLI 지원 | 15.6.27309.0 | 필수
Microsoft.VisualStudio.Component.VC.Tools.ARM | ARM용 Visual C++ 컴파일러 및 라이브러리 | 15.8.27825.0 | 필수
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | ARM64용 Visual C++ 컴파일러 및 라이브러리 | 15.9.28230.55 | 필수
Microsoft.VisualStudio.Component.VisualStudioData | 데이터 원본 및 서비스 참조 | 15.6.27406.0 | 필수
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK(10.0.14393.0) | 15.6.27406.0 | 필수
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK(10.0.17763.0) | 15.9.28307.102 | 필수

## <a name="unaffiliated-components"></a>독립적 구성 요소

이러한 구성 요소는 작업에 포함되지 않지만 개별 구성 요소로 선택할 수 있습니다.

구성 요소 ID | name | 버전
--- | --- | ---
N/A | N/A | N/A
