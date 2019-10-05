---
title: DLL 프로젝트 디버그 | Microsoft Docs
ms.date: 11/06/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging DLLs
- templates, debugging DLLs
- DLLs, debugging
- debugging [Visual Studio], DLLs
ms.assetid: 433cab30-d191-460b-96f7-90d2530ca243
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8ec10f226ad139ffbeb46badc6ef3dd6c384af91
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714946"
---
# <a name="debug-dlls-in-visual-studio-c-c-visual-basic-f"></a>Visual Studio에서 Dll 디버깅 (C#, C++, Visual Basic의 경우 F#)

DLL (동적 연결 라이브러리)에 둘 이상의 앱에서 사용할 수 있는 코드 및 데이터를 포함 하는 라이브러리입니다. 만들기, 빌드, 구성에 Visual Studio를 사용 하 고 Dll을 디버그할 수 있습니다.

## <a name="create-a-dll"></a>DLL 만들기

다음 Visual Studio 프로젝트 템플릿은 Dll을 만들 수 있습니다.

- C#Visual Basic의 경우 또는 F# 클래스 라이브러리
- C#Visual Basic Windows Forms 컨트롤 (WCF) 라이브러리 또는
- C++동적 연결 라이브러리 (DLL)

자세한 내용은 [MFC 디버깅 기술](../debugger/mfc-debugging-techniques.md)을 참조하세요.

WCF 라이브러리를 디버깅 하는 것을 클래스 라이브러리를 디버깅 하는 것과 비슷합니다. 자세한 내용은 참조 하세요 [Windows Forms 컨트롤](/dotnet/framework/winforms/controls/index)합니다.

일반적으로 다른 프로젝트에서 DLL을 호출 합니다. DLL 구성에 따라 호출 하는 프로젝트를 디버깅할 때 한 단계씩 코드 실행 하 고 DLL 코드를 디버그할 수 있습니다.

## <a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> DLL 디버그 구성

Visual Studio 프로젝트 템플릿을 사용 하 여 앱을 만드는 경우 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 디버그 및 릴리스 빌드 구성에 대 한 필요한 설정을 자동으로 만듭니다. 필요한 경우 이러한 설정을 변경할 수 있습니다. 자세한 내용은 다음 항목을 참조하세요.

- [C++ 디버그 구성에 대한 프로젝트 설정](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [C# 디버그 구성을 위한 프로젝트 설정](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Visual Basic 디버그 구성에 대한 프로젝트 설정](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [방법: 디버그 및 릴리스 구성 설정](../debugger/how-to-set-debug-and-release-configurations.md)

### <a name="set-c-debuggableattribute"></a>설정 C++ DebuggableAttribute

연결할 디버거에 대 한는 C++ DLL을 C++ 코드를 내보내야 `DebuggableAttribute`합니다.

**설정할 `DebuggableAttribute`:**

1. 선택는 C++ 에서 DLL 프로젝트 **솔루션 탐색기** 선택 합니다 **속성** 아이콘을 또는 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 선택 **속성**.

1. 에 **속성** 창 아래에 있는 **링커** > **디버깅**선택 **예 (/ ASSEMBLYDEBUG)** 에 대 한  **디버깅 가능한 어셈블리**합니다.

자세한 내용은 [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute)합니다.

### <a name="vxtskdebuggingdllprojectsexternal"></a> C를 설정 /C++ DLL 파일 위치

외부 DLL을 디버깅 하려면 호출 하는 프로젝트에서 DLL을 찾을 수 있어야 해당 [.pdb 파일](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), 및 DLL에 필요한 기타 파일입니다. 이러한 파일을 복사 하는 사용자 지정 빌드 작업을 만들 수 있습니다 하  *\<프로젝트 폴더 > \Debug* 출력 폴더 또는 있습니다 있습니다 파일을 수동으로 복사할 수 있습니다.

C /C++ 프로젝트에서에서 설정할 수 있습니다 헤더 및 LIB 파일 위치는 프로젝트 출력 폴더에 복사 하는 대신 속성 페이지.

**C를 설정 /C++ 헤더 및 LIB 파일 위치:**

1. C를 선택 합니다. /C++ 에서 DLL 프로젝트 **솔루션 탐색기** 선택 합니다 **속성** 아이콘을 또는 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 선택 **속성**.

1. 맨 위에 있는 합니다 **속성** 창 아래에 있는 **구성**를 선택 **모든 구성**합니다.

1. 아래 **C /C++**  > **일반** > **Additional Include Directories**, 헤더 파일이 있는 폴더를 지정 합니다.

1. 아래 **링커** > **일반** > **추가 라이브러리 디렉터리**, LIB 파일이 있는 폴더를 지정 합니다.

1. 아래 **링커** > **입력** > **추가 종속성**, 전체 경로 및 LIB 파일에 대 한 filename을 지정 합니다.

1. **확인**을 선택합니다.

대 한 자세한 내용은 C++ 프로젝트 설정을 참조 하세요 [속성 페이지 (Visual C++)](/cpp/build/reference/property-pages-visual-cpp)합니다.

## <a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> 디버그 버전 빌드

디버깅을 시작 하기 전에 DLL의 디버그 버전을 작성 해야 합니다. DLL을 디버깅 하려면 호출 앱을 찾을 수 있어야 해당 [.pdb 파일](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) 및 DLL에 필요한 기타 파일입니다.

DLL 파일을 복사 하는 사용자 지정 빌드 작업을 만들 수 있습니다 하  *\<프로젝트 폴더를 호출 > \Debug* 출력 폴더 또는 있습니다 있습니다 파일을 수동으로 복사할 수 있습니다.

올바른 위치에서 DLL을 호출 해야 합니다. 이 모호해 보일 수 있지만 디버거는 설정한 중단점에 오버플로되지 호출 앱을 찾아서 로드 DLL의 다른 복사본을 하는 경우.

## <a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> DLL 디버깅

DLL을 직접 실행할 수 없습니다. 일반적으로 앱에서 호출할 수 있어야 합니다는 *.exe* 파일입니다. 자세한 내용은 [만들기 및 시각적 개체를 관리 C++ 프로젝트](/cpp/ide/creating-and-managing-visual-cpp-projects)합니다.

DLL을 디버깅 하려면 [호출한 응용 프로그램에서 디버깅 시작](#vxtskdebuggingdllprojectsthecallingapplication), 또는 [DLL 프로젝트에서 디버그](how-to-debug-from-a-dll-project.md) 호출 해당 앱을 지정 하 여 합니다. 디버거를 사용할 수도 있습니다 [직접 실행 창](#vxtskdebuggingdllprojectstheimmediatewindow) 호출 앱을 사용 하지 않고 디자인 타임에 DLL 함수 또는 메서드를 평가 합니다.

자세한 내용은 [디버거 소개](../debugger/debugger-feature-tour.md)합니다.

### <a name="vxtskdebuggingdllprojectsthecallingapplication"></a> 호출 앱에서 디버깅 시작

DLL을 호출 하는 앱이 될 수 있습니다.

- 앱을 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 동일 하거나 DLL에서 다른 솔루션에 프로젝트입니다.
- 이미 배포 된 기존 앱 및 테스트 컴퓨터나 프로덕션 컴퓨터에서 실행 되지 않도록 합니다.
- 웹에 위치하며 URL을 통해 액세스합니다.
- DLL을 포함 하는 웹 페이지를 사용 하 여 웹 앱입니다.

호출 앱에서 DLL을 디버깅 하려면 다음을 수행할 수 있습니다.

- 호출 앱에 대 한 프로젝트를 열고 선택 하 여 디버깅을 시작할 **디버깅할** > **디버깅 시작** 키를 누르거나 **F5**합니다.

  또는

- 이미 배포 되어 테스트 컴퓨터나 프로덕션 컴퓨터에서 실행 되는 앱에 연결 합니다. 웹 사이트 또는 웹 앱의 Dll에 대 한이 메서드를 사용 합니다. 자세한 내용은 [방법: 실행 중인 프로세스에 연결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

호출 응용 프로그램 디버깅을 시작 하기 전에 DLL에서 중단점을 설정 합니다. 참조 [중단점을 사용 하 여](../debugger/using-breakpoints.md)입니다. DLL 중단점이 적중 될 때 실행할 수 있습니다 코드를 통해 각 줄의 작업을 관찰 합니다. 자세한 내용은 [디버거에서 코드를 탐색](../debugger/navigating-through-code-with-the-debugger.md)합니다.

디버그 하는 동안 사용할 수 있습니다 합니다 **모듈** Dll을 확인 하려면 창 및 *.exe* 앱이 로드 파일입니다. 열려는 합니다 **모듈** 창에서 디버그 하는 동안 **디버그** > **Windows** > **모듈**합니다. 자세한 내용은 [방법: 모듈 창 사용](../debugger/how-to-use-the-modules-window.md)을 참조하세요.

### <a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> 직접 실행 창 사용

사용할 수는 **직접 실행** 창 디자인 타임에 DLL 함수 또는 메서드를 평가 합니다. 합니다 **직접 실행** 창 호출 응용 프로그램의 역할을 수행 합니다.

>[!NOTE]
>사용할 수는 **직접 실행** 대부분의 프로젝트 형식에 디자인 타임에는 창입니다. SQL, 웹 프로젝트 또는 스크립트에 대해서는 지원 되지 않습니다.

예를 들어 라는 메서드를 테스트할 `Test` 클래스에서 `Class1`:

1. DLL 프로젝트를 열고, 엽니다는 **직접 실행** 선택 하 여 창 **디버그** > **Windows** > **즉시**키를 누르거나 **Ctrl**+**Alt**+**있습니까**합니다.

1. 형식의 개체를 인스턴스화할 `Class1` 다음을 입력 하 여 C# 의 코드를 **직접 실행** 창과 키를 눌러 **Enter**. 이 관리 코드에서 사용할 수 C# 및 Visual Basic의 경우 적절 한 구문 변경 합니다.

   ```csharp
   Class1 obj = new Class1();
   ```

   C#에서 모든 이름은 정규화되어야 합니다. 언어 서비스 식 평가 하려고 할 때 현재 범위와 상황에 맞는 모든 메서드나 변수 여야 합니다.

1. `Test` 에서 `int` 매개 변수 하나를 사용하는 것으로 가정하고 `Test` 직접 실행 **창을 사용하여** 를 실행합니다.

   ```csharp
   ?obj.Test(10);
   ```

   결과 인쇄 합니다 **직접 실행** 창입니다.

1. 중단점을 배치한 다음, 함수를 다시 실행하여 `Test`를 계속 디버깅할 수 있습니다.

   중단점 도달 하면 단계별로 실행할 수 있습니다 및 `Test`합니다. 실행이 `Test`를 벗어나면 디버거가 디자인 모드로 되돌아갑니다.

## <a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> 혼합 모드 디버깅

관리 되는 또는 네이티브 코드에서 DLL에 대 한 호출 앱을 작성할 수 있습니다. 관리 되는 DLL을 호출 하는 네이티브 앱을 모두 디버그 하려는 경우에 프로젝트 속성에서 관리 및 네이티브 디버거를 사용할 수 있습니다. 정확한 프로세스는 DLL 프로젝트 또는 호출 응용 프로그램 프로젝트에서 디버깅을 시작할 것인지에 따라 달라 집니다. 자세한 내용은 [방법: 혼합 모드에서 디버그](../debugger/how-to-debug-in-mixed-mode.md).

또한 관리 되는 호출 프로젝트에서 네이티브 DLL을 디버깅할 수 있습니다. 자세한 내용은 [관리 및 네이티브 코드를 디버그 하는 방법을](how-to-debug-managed-and-native-code.md)합니다.

## <a name="see-also"></a>참고자료
- [관리 코드 디버그](../debugger/debugging-managed-code.md)
- [Visual C++ 프로젝트 형식](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [C#, F# 및 Visual Basic 프로젝트 형식](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [C# 디버그 구성을 위한 프로젝트 설정](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [C# 디버그 구성을 위한 프로젝트 설정](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Visual Basic 디버그 구성을 위한 프로젝트 설정](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [디버거 보안](../debugger/debugger-security.md)
