---
title: 프로젝트 설정에 대 한는 C# 디버그 구성 | Microsoft Docs
ms.custom: seodec18
ms.date: 11/21/2018
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debug configurations, C#
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debugging [C#], debugger settings
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a5108e195e5df245c72436752316e8ee91781e7d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62904064"
---
# <a name="project-settings-for--c-debug-configurations"></a>C# 디버그 구성을 위한 프로젝트 설정

변경할 수 있습니다 C# 프로젝트 디버그 설정에는 [디버그 탭](#debug-tab) 하 고 [빌드 탭](#build-tab) 프로젝트 속성 페이지의 합니다.

속성 페이지를 열려면에서 프로젝트를 선택 **솔루션 탐색기** 를 선택한 합니다 **속성** 아이콘을 또는 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 선택 **속성**합니다.

자세한 내용은 [디버그 및 릴리스 구성](how-to-set-debug-and-release-configurations.md)을 참조하세요.

>[!IMPORTANT]
>.NET Core, ASP.NET 또는 UWP 앱에 이러한 설정이 적용 되지 않습니다. UWP 앱에 대 한 디버그 설정을 구성 하려면 [UWP 앱에 대 한 디버깅 세션을 시작](start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)합니다.

## <a name="debug-tab"></a>디버그 탭

|설정|설명|
|-------------------------------------| - |
| **구성** | 앱을 빌드하기 위한 모드를 설정 합니다. 선택 **활성 (디버그)**, **디버그**를 **릴리스**, 또는 **구성을 모두** 드롭다운 목록에서. |
| **시작 작업** | 선택 하면 동작을 지정 **시작** 디버그 구성에서 합니다.<br />기본값인 - **시작 프로젝트**를 선택하면 디버깅을 위한 시작 프로젝트가 실행됩니다. 자세한 내용은 [시작 프로젝트 선택](/previous-versions/visualstudio/visual-studio-2010/0s590bew(v=vs.100))합니다.<br />- **시작 외부 프로그램** 시작 하 고 연결 되지 않은 응용 프로그램의 일부를 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로젝트. 자세한 내용은 [디버거를 사용 하 여 실행 중인 프로세스에 연결](attach-to-running-processes-with-the-visual-studio-debugger.md)합니다.<br />- **URL로 브라우저 시작** 웹 앱을 디버깅할 수 있습니다. |
| **시작 옵션** > **명령줄 인수** | 디버그 중인 앱에 대 한 명령줄 인수를 지정 합니다. 명령 이름은에 지정 된 앱 이름 **시작 외부 프로그램**합니다. |
| **시작 옵션** > **작업 디렉터리** | 디버그 중인 앱의 작업 디렉터리를 지정 합니다. C#, 작업 디렉터리입니다. *\bin\debug* 기본적으로 합니다.
| **시작 옵션** > **원격 컴퓨터 사용**|원격 디버깅을 위해이 옵션을 선택 하 고 원격 디버깅 대상의 이름을 입력 요소나 [Msvsmon 서버 이름](../debugger/remote-debugging.md)합니다. <br />원격 컴퓨터에서 앱의 위치에서 지정 됩니다는 **출력 경로** 속성을 **빌드** 탭 합니다. 이 위치는 원격 컴퓨터의 공유할 수 있는 디렉터리여야 합니다.
| **디버거 엔진** > **비관리 코드 디버깅 사용** | 관리 되는 앱에서 네이티브 (비관리) Win32 코드에 대 한 호출을 디버깅 합니다. |
| **디버거 엔진** > **SQL Server 디버깅 사용** | SQL Server 데이터베이스 개체를 디버깅 합니다. |

## <a name="build-tab"></a>빌드 탭

|설정|설명|
|-------------|-----------------|
|**일반적인** > **조건부 컴파일 기호**|선택한 경우에 DEBUG 및 TRACE 상수를 정의 합니다.<br /><br /> 이 상수를 사용하면 조건에 따라 [Debug 클래스](/dotnet/api/system.diagnostics.debug)와 [Trace 클래스](/dotnet/api/system.diagnostics.trace)를 컴파일할 수 있습니다. 이 상수를 정의하면 Debug 및 Trace 클래스 메서드의 결과가 [출력 창](../ide/reference/output-window.md)에 표시됩니다. 이 상수를 정의하지 않으면 Debug 및 Trace 클래스 메서드가 컴파일되지 않으므로 결과가 생성되지 않습니다.<br /><br />일반적으로 디버그 빌드의 디버그 버전에서 정의 되 고 릴리스 버전에서 정의 되지 않았습니다. 추적은 디버그 및 릴리스 버전에서 정의 됩니다.|
|**일반적인** > **코드 최적화**|버그 최적화 된 코드에만 표시 됩니다, 하지 않는 한이 설정은 디버그 빌드에 대 한 선택 취소 된 상태로 둡니다. 최적화 된 코드 디버깅 하기 어렵습니다, 명령이 소스 코드에서 문에 직접 대응 되지 않기 때문입니다.|
|**출력** > **출력 경로**|디버깅 작업에서는 일반적으로 *bin\Debug*로 설정합니다.|
|**고급** 단추|고급 디버깅 옵션에 대 한 자세한 내용은 [고급 빌드 설정 대화 상자 (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md)합니다. 기호에 대 한 이식 가능한 형식 (*.pdb*) 파일은.NET Core 앱에 대 한 최신 크로스 플랫폼 형식입니다.

## <a name="see-also"></a>참고자료
- [디버거 설정 및 준비](../debugger/debugger-settings-and-preparation.md)