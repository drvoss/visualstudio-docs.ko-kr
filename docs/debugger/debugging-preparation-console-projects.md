---
title: 콘솔 프로젝트 디버깅 준비 | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], console applications
- debugging console applications
- console applications, debugging
ms.assetid: 9641f1d9-2d5a-48b1-8731-6525e8f67892
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be22786a78c16dc9ffa05aba38075e4762485d2d
ms.sourcegitcommit: 9cfd3ef6c65f671a26322320818212a1ed5955fe
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68533313"
---
# <a name="debugging-preparation-console-projects-c-c-visual-basic-f"></a>디버깅 준비 중: 콘솔 프로젝트 (C#, C++, Visual Basic, F#)

콘솔 프로젝트 디버깅을 준비 하는 것은 Windows 프로젝트 디버깅을 준비 하는 것과 유사 합니다. 명령줄 인수 설정 및 디버깅을 위해 응용 프로그램을 일시 중지 하는 방법 등의 몇 가지 추가 고려 사항이 있습니다. 자세한 내용은 [Windows Forms 응용 프로그램](../debugger/debugging-preparation-windows-forms-applications.md)및 [디버깅 준비를 참조 하세요. 응용 프로그램 (.NET)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/sez9z95a(v=vs.100))을 Windows Forms 합니다. 콘솔 애플리케이션은 모두 비슷하므로 이 항목에서는 다음과 같은 프로젝트 형식을 다룹니다.

- C#, Visual Basic 및 F# 콘솔 응용 프로그램

- C++ 콘솔 애플리케이션(.NET)

- C++ 콘솔 애플리케이션(Win32)

  콘솔 애플리케이션은 **콘솔** 창을 사용하여 입력을 받고 출력 메시지를 표시합니다. **콘솔** 창에 쓰려면 응용 프로그램에서 Debug 개체 대신 **console** 개체를 사용 해야 합니다. 단, **Visual Studio 출력** 창에 결과를 표시하려는 경우에는 보통 때처럼 Debug 개체를 사용합니다. 사용자는 애플리케이션에서 출력하는 위치를 정확하게 알아야 합니다. 정확한 위치를 모르면 잘못된 위치에서 메시지를 찾을 수 있습니다. 자세한 내용은 [Console 클래스](/dotnet/api/system.console), [Debug 클래스](/dotnet/api/system.diagnostics.debug) 및 [출력 창](../ide/reference/output-window.md)을 참조하세요.

## <a name="set-command-line-arguments"></a>명령줄 인수 설정

콘솔 애플리케이션에 대한 명령줄 인수를 지정해야 할 수도 있습니다. 자세한 내용은 디버그 구성에 대 한 [프로젝트 설정 C++ ](../debugger/project-settings-for-a-cpp-debug-configuration.md), [Visual Basic 디버그 구성](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)에 대 한 프로젝트 설정 또는 [디버그 구성에 대 한 C# 프로젝트](../debugger/project-settings-for-csharp-debug-configurations.md)설정을 참조 하세요.

모든 프로젝트 속성과 마찬가지로 이러한 인수도 디버그 세션 사이와 Visual Studio 세션 사이에 지속적으로 적용됩니다. 따라서 이전에 디버깅한 콘솔 애플리케이션인 경우에는 이전 세션에서 **\<Project>속성 페이지** 대화 상자에 입력한 인수가 있을 수 있습니다.

## <a name="start-the-application"></a>응용 프로그램 시작

 일부 콘솔 애플리케이션은 시작되면 완료될 때까지 실행된 다음 종료됩니다. 이 동작은 실행을 중단하고 디버깅할 충분한 시간을 제공하지 않을 수 있습니다. 애플리케이션을 디버깅할 수 있으려면 다음 절차 중 하나를 사용하여 애플리케이션을 시작합니다.

- 코드에 중단점을 설정 하 고 응용 프로그램을 시작 합니다.

- **F10** 키를 사용 하 여 응용 프로그램을 시작한 다음 (**디버그** > **단계**실행), **F11** 키 (**디버그** > **단계**)를 사용 하 여 코드를 탐색 하 고 **클릭 하 여 클릭**합니다.

- 코드 편집기에서 줄을 마우스 오른쪽 단추로 클릭 하 고 **커서까지 실행**을 선택 합니다.

  콘솔 애플리케이션을 디버깅할 때는 Visual Studio 대신 명령 프롬프트에서 애플리케이션을 시작하는 경우가 있을 수 있습니다. 이 경우에는 명령 프롬프트에서 애플리케이션을 시작하고 Visual Studio 디버거를 애플리케이션에 연결할 수 있습니다. 자세한 내용은 [실행 중인 프로세스에 연결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)을 참조 하세요.

  Visual Studio에서 콘솔 애플리케이션을 시작하면 **콘솔** 창이 Visual Studio 창 뒤에 나타날 수도 있습니다. Visual Studio에서 콘솔 애플리케이션을 시작했는데 콘솔 창이 보이지 않으면 Visual Studio 창을 이동해 보십시오.

## <a name="see-also"></a>참고 항목
- [네이티브 코드 디버그](../debugger/debugging-native-code.md)
- [관리 코드 디버그](../debugger/debugging-managed-code.md)
- [Visual C++ 프로젝트 형식](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [C#, F#, and Visual Basic Project Types](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)(C#, F# 및 Visual Basic 프로젝트 형식)
- [C++ 디버그 구성에 대한 프로젝트 설정](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [디버거 보안](../debugger/debugger-security.md)