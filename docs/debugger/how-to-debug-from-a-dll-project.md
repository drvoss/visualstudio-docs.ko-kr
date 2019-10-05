---
title: '방법: DLL 프로젝트에서 디버그 | Microsoft Docs'
ms.date: 10/10/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DLL projects, debugging
- debugging DLLs
- DLLs, debugging projects
- debugging [Visual Studio], DLLs
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2e4df2028a14281ee2343ad48b4b71812d29fca
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62847955"
---
# <a name="how-to-debug-from-a-dll-project-in-visual-studio-c-c-visual-basic-f"></a>방법: Visual Studio에서 DLL 프로젝트에서 디버그 (C#, C++, Visual Basic의 경우 F#)

DLL 프로젝트를 디버깅 하는 한 가지 방법은 DLL 프로젝트 속성에서 호출한 응용 프로그램을 지정 하는 것입니다. 그런 다음 자체 DLL 프로젝트에서 디버깅을 시작할 수 있습니다. 이 방법을 사용 하려면 앱을 구성한 것과 동일한 위치에 동일한 DLL을 호출 해야 합니다. 앱을 다른 버전의 DLL 로드를 찾아서 해당 버전 중단점 포함 되지 않습니다. Dll 디버깅의 다른 메서드를 참조 하세요 [DLL 디버깅 프로젝트](../debugger/debugging-dll-projects.md)합니다.

네이티브 DLL을 호출 하는 관리 되는 앱 또는 네이티브 앱을 관리 되는 DLL을 호출 하는 경우에 DLL 및 호출 앱 모두를 디버깅할 수 있습니다. 자세한 내용은 [방법: 혼합 모드에서 디버그](../debugger/how-to-debug-in-mixed-mode.md).

네이티브 및 관리 DLL 프로젝트에는 호출 앱을 지정 다른 설정이 있습니다.

## <a name="specify-a-calling-app-in-a-native-dll-project"></a>호출 앱을 네이티브 DLL 프로젝트 지정

1. 선택 된 C++ 에서 DLL 프로젝트 **솔루션 탐색기**합니다. 선택 된 **속성** 아이콘을 눌러 **Alt**+**Enter**, 또는 마우스 오른쪽 단추로 클릭 하 고 선택 **속성**.

1. 에  **\<프로젝트 > 속성 페이지** 대화 상자는 **구성** 창의 맨 위에 있는 필드 설정 됩니다 **디버그**합니다.

1. 선택 **구성 속성** > **디버깅**합니다.

1. 에 **실행할 디버거** 목록에서 선택 하거나 **로컬 Windows 디버거** 또는 **원격 Windows 디버거**합니다.

1. 에 **명령** 또는 **원격 명령** 상자에서 호출한 응용 프로그램의 파일 이름을 확인 하 고 정규화 된 경로 같은 추가 *.exe* 파일입니다.

   ![디버그 속성 창](../debugger/media/dbg-debugging-properties-dll.png "디버그 속성 창")

1. 필요한 프로그램 인수를 **명령 인수** 상자에 추가합니다.

1. **확인**을 선택합니다.

## <a name="specify-a-calling-app-in-a-managed-dll-project"></a>관리 되는 DLL 프로젝트에서 호출 앱을 지정 합니다.

1. C# 또는 Visual Basic DLL 프로젝트를 선택 **솔루션 탐색기**합니다. 선택 된 **속성** 아이콘을 눌러 **Alt**+**Enter**, 또는 마우스 오른쪽 단추로 클릭 하 고 선택 **속성**.

1. 창의 맨 위에 있는 **구성** 필드가 **디버그**로 설정되어 있는지 확인합니다.

1. 아래 **시작 작업**:

   - .NET Framework Dll에 대 한 선택 **시작 외부 프로그램**, 호출한 응용 프로그램의 이름과 정규화 된 경로 추가 합니다.

   - 또는 선택 **URL로 브라우저 시작** 로컬 ASP.NET 앱의 URL을 입력 합니다.

   - .NET Core Dll에 대 한 합니다 **디버그** 속성 페이지 다릅니다. 선택 **실행 파일** 에서 합니다 **시작** 드롭다운에서 다음에서 호출 된 앱의 이름과 정규화 된 경로 추가 합니다 **실행 파일** 필드.

1. 에 필요한 명령줄 인수를 추가 합니다 **명령줄 인수** 하거나 **응용 프로그램 인수** 필드입니다.

   ![C# 디버그 속성 창](../debugger/media/dbg-debugging-properties-dll-csharp.png "C# 디버그 속성 창")

1. 사용 하 여 **파일** > **선택한 항목 저장** 하거나 **Ctrl**+**S** 변경 내용을 저장 합니다.

## <a name="debug-from-the-dll-project"></a>DLL 프로젝트에서 디버그

1. DLL 프로젝트에 중단점을 설정 합니다.

1. DLL 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 선택 **시작 프로젝트로 설정**합니다.

1. 있는지 확인 합니다 **솔루션 구성** 필드 설정 됩니다 **디버그**합니다. 키를 눌러 **F5**, 클릭 녹색 **시작** 화살표 또는 선택 **디버그** > **디버깅 시작**합니다.

디버깅 중단점 적중 되지 않습니다 하는 경우 DLL 출력는 있는지 확인 (기본적으로  *\<프로젝트 > \Debug* 폴더) 호출한 응용 프로그램을 호출 하는 위치입니다.

## <a name="see-also"></a>참고자료
- [DLL 프로젝트 디버깅](../debugger/debugging-dll-projects.md)
- [C# 디버그 구성에 대한 프로젝트 설정](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Visual Basic 디버그 구성에 대한 프로젝트 설정](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [C++ 디버그 구성에 대한 프로젝트 설정](../debugger/project-settings-for-a-cpp-debug-configuration.md)