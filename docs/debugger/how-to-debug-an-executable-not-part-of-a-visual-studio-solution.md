---
title: Visual Studio 솔루션의 일부가 아닌 응용 프로그램을 디버깅
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/19/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2db4cf8a678b6c20693dcc9c1e730d83f0d5ca7a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62848001"
---
# <a name="debug-an-app-that-isnt-part-of-a-visual-studio-solution-c-c-visual-basic-f"></a>Visual Studio 솔루션의 일부가 아닌 응용 프로그램을 디버깅 (C++, C#, Visual Basic의 경우 F#)

앱을 디버그 하는 것이 좋습니다 (*.exe* 파일)는 Visual Studio 솔루션의 일부가 아닌입니다. 또는 누군가가 만들었을 Visual Studio 외부에서 앱 또는 다른 위치에서 앱을 가져왔습니다.

Visual Studio에서 존재 하지 않는 앱을 디버그 하는 일반적인 방법은 Visual Studio 외부에서 앱을 시작 하 고 사용 하 여 연결 하는 것 **프로세스에 연결** Visual Studio 디버거에서 합니다. 자세한 내용은 [실행 중인 프로세스에 연결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)합니다.

몇 초를 사용 하는 수동 단계 필요 앱에 연결 합니다. 이 지연으로 인해 시작 문제를 디버그할 수 없습니다 연결 하거나 앱 사용자에 대 한 대기 하지 않습니다 하는 입력 및 신속 하 게 완료 합니다.

이러한 상황에서는 앱에 대 한 Visual Studio EXE 프로젝트를 만듭니다 하거나 기존에 가져올 수 있습니다 C#, Visual Basic 또는 C++ 솔루션입니다. 모든 프로그래밍 언어가 EXE 프로젝트를 지원하는 것은 아닙니다.

>[!IMPORTANT]
>앱에 연결 하 든 Visual Studio 솔루션에 추가 되지 않은 Visual Studio에서 작성 하는 앱에 대 한 디버깅 기능 제한 됩니다.
>
>소스 코드를 사용 하는 경우 가장 좋은 방법은 Visual Studio 프로젝트에 코드를 가져오는 방법은입니다. 그런 다음 앱의 디버그 빌드를 실행 합니다.
>
>소스 코드가 없는 경우 및 앱에 없는 [디버그 정보](../debugger/how-to-set-debug-and-release-configurations.md) 호환 형식으로 디버깅 기능을 사용할 수는 매우 적습니다.

### <a name="to-create-a-new-exe-project-for-an-existing-app"></a>기존 앱에 대 한 새 EXE 프로젝트를 만들려면

1. Visual Studio에서 선택 **파일** > **Open** > **프로젝트**합니다.

1. 에 **프로젝트 열기** 대화 상자에서 **모든 프로젝트 파일**, 선택 되지 않은 경우, 드롭다운 목록에서 옆에 **파일 이름을**입니다.

1. 로 이동 합니다 *.exe* 파일을 선택 하 고 선택 **오픈**합니다.

   파일을 일시적으로 새 Visual Studio 솔루션에 나타납니다.

1. 같은 실행 명령을 선택 하 여 앱을 디버깅을 시작할 **디버깅 시작**에서 **디버그** 메뉴.

### <a name="to-import-an-app-into-an-existing-visual-studio-solution"></a>기존 Visual Studio 솔루션으로 앱을 가져오려면

1. 사용 하 여는 C++, C#, Visual Studio에서 열려 있는 Visual Basic 솔루션을 선택 하거나 **파일** > **추가** > **기존 프로젝트**.

1. 에 **프로젝트 열기** 대화 상자에서 **모든 프로젝트 파일**, 선택 되지 않은 경우, 드롭다운 목록에서 옆에 **파일 이름을**입니다.

1. 로 이동 합니다 *.exe* 파일을 선택 하 고 선택 **오픈**합니다.

   현재 솔루션에서 새 프로젝트로 파일이 표시 됩니다.

1. 선택한 새 파일을 같은 실행 명령을 선택 하 여 앱을 디버깅을 시작할 **디버깅 시작**에서 **디버그** 메뉴.

### <a name="see-also"></a>참고자료
- [디버거 설정 및 준비](../debugger/debugger-settings-and-preparation.md)
- [디버거 보안](../debugger/debugger-security.md)
- [DBG 파일](/previous-versions/visualstudio/visual-studio-2010/da528y14(v=vs.100))