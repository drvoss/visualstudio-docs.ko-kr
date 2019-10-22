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
ms.openlocfilehash: 898eb0eb1489d83e97ec9f0a5b38b475bda0199d
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72450418"
---
# <a name="debug-dlls-in-visual-studio-c-c-visual-basic-f"></a>Visual Studio의 디버그 dll (C#, C++, Visual Basic, F#)

DLL (동적 연결 라이브러리)은 둘 이상의 앱에서 사용할 수 있는 코드와 데이터가 포함 된 라이브러리입니다. Visual Studio를 사용 하 여 Dll을 만들고 빌드하고 구성 하 고 디버그할 수 있습니다.

## <a name="create-a-dll"></a>DLL 만들기

다음 Visual Studio 프로젝트 템플릿은 Dll을 만들 수 있습니다.

- C#, Visual Basic 또는 F# 클래스 라이브러리
- C#또는 WCF (Visual Basic Windows Forms 컨트롤) 라이브러리
- C++DLL (동적 연결 라이브러리)

자세한 내용은 [MFC 디버깅 기술](../debugger/mfc-debugging-techniques.md)을 참조하세요.

WCF 라이브러리 디버깅은 클래스 라이브러리 디버깅과 유사 합니다. 자세한 내용은 [Windows Forms 컨트롤](/dotnet/framework/winforms/controls/index)을 참조 하세요.

일반적으로 다른 프로젝트에서 DLL을 호출 합니다. 호출 프로젝트를 디버깅할 때 DLL 구성에 따라 DLL 코드를 한 단계씩 실행 하 고 디버그할 수 있습니다.

## <a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a>DLL 디버그 구성

Visual Studio 프로젝트 템플릿을 사용 하 여 앱을 만드는 경우 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]는 디버그 및 릴리스 빌드 구성에 필요한 설정을 자동으로 만듭니다. 필요한 경우 이러한 설정을 변경할 수 있습니다. 자세한 내용은 다음 항목을 참조하세요.

- [C++ 디버그 구성에 대한 프로젝트 설정](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [C# 디버그 구성을 위한 프로젝트 설정](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Visual Basic 디버그 구성에 대한 프로젝트 설정](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [방법: 디버그 및 릴리스 구성 설정](../debugger/how-to-set-debug-and-release-configurations.md)

### <a name="set-c-debuggableattribute"></a>DebuggableAttribute C++ 설정

디버거가 C++ DLL에 연결 하려면 코드에서 C++ `DebuggableAttribute`를 내보내야 합니다.

**@No__t_1을 설정 하려면:**

1. 솔루션 탐색기에서 C++ DLL 프로젝트를 선택 하 고 **속성** 아이콘을 선택 하거나 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **속성**을 선택 합니다.

1. **속성** 창의 **링커**  > **디버깅**에서 디버깅 가능한 **어셈블리**에 대해 **예 (/ASSEMBLYDEBUG)** 를 선택 합니다.

자세한 내용은 [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute)를 참조 하세요.

### <a name="vxtskdebuggingdllprojectsexternal"></a>C/C++ DLL 파일 위치 설정

외부 DLL을 디버깅 하려면 호출 하는 프로젝트에서 DLL, [.pdb 파일](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)및 dll에 필요한 다른 모든 파일을 찾을 수 있어야 합니다. 사용자 지정 빌드 작업을 만들어 이러한 파일을 *\<project 폴더 > \Debug* output 폴더로 복사 하거나 수동으로 파일을 복사할 수 있습니다.

C/C++ 프로젝트의 경우 프로젝트 속성 페이지에서 헤더 및 LIB 파일 위치를 출력 폴더에 복사 하는 대신 설정할 수 있습니다.

**C/C++ 헤더 및 LIB 파일 위치를 설정 하려면 다음을 수행 합니다.**

1. 솔루션 탐색기에서 C/C++ DLL 프로젝트를 선택 하 고 **속성** 아이콘을 선택 하거나 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **속성**을 선택 합니다.

1. **속성** 창의 위쪽에 있는 **구성**에서 **모든 구성**을 선택 합니다.

1. **C/C++**   > **일반**  > **추가 포함 디렉터리**에서 헤더 파일을 포함 하는 폴더를 지정 합니다.

1. **추가 라이브러리 디렉터리** ** > ** **링커**  > 에 LIB 파일이 있는 폴더를 지정 합니다.

1. **링커** 에서**추가 종속성** > **입력**  >  LIB 파일의 전체 경로와 파일 이름을 지정 합니다.

1. **확인**을 선택합니다.

프로젝트 설정에 C++ 대 한 자세한 내용은 [Windows C++ 속성 페이지 참조](/cpp/build/reference/property-pages-visual-cpp)를 참조 하세요.

## <a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a>디버그 버전 빌드

디버깅을 시작 하기 전에 DLL의 디버그 버전을 빌드해야 합니다. DLL을 디버깅 하려면 호출 하는 앱에서 해당 [.pdb 파일](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) 및 dll에 필요한 다른 파일을 찾을 수 있어야 합니다.

사용자 지정 빌드 작업을 만들어 DLL 파일을 *\<calling 프로젝트 폴더 > \Debug* output 폴더로 복사 하거나 수동으로 파일을 복사할 수 있습니다.

올바른 위치에서 DLL을 호출 해야 합니다. 이는 명확 하 게 보일 수 있지만 호출 하는 앱이 DLL의 다른 복사본을 찾아 로드 하는 경우 디버거는 설정한 중단점에 도달 하지 않습니다.

## <a name="vxtskdebuggingdllprojectswaystodebugthedll"></a>DLL 디버그

DLL은 직접 실행할 수 없습니다. 앱 (일반적으로 *.exe* 파일)에서 호출 해야 합니다. 자세한 내용은 [Visual Studio 프로젝트- C++ ](/cpp/ide/creating-and-managing-visual-cpp-projects)를 참조 하세요.

DLL을 디버깅 하려면 [호출 하는 응용 프로그램에서 디버깅을 시작](#vxtskdebuggingdllprojectsthecallingapplication)하거나 호출 하는 앱을 지정 하 여 [dll 프로젝트에서 디버그할](how-to-debug-from-a-dll-project.md) 수 있습니다. 디버거 [직접 실행 창을](#vxtskdebuggingdllprojectstheimmediatewindow) 사용 하 여 호출 하는 앱을 사용 하지 않고도 디자인 타임에 DLL 함수 또는 메서드를 평가할 수도 있습니다.

자세한 내용은 [디버거에서 먼저 확인](../debugger/debugger-feature-tour.md)을 참조 하세요.

### <a name="vxtskdebuggingdllprojectsthecallingapplication"></a>호출 하는 앱에서 디버깅 시작

DLL을 호출 하는 앱은 다음과 같을 수 있습니다.

- DLL과 동일한 또는 다른 솔루션에 있는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로젝트의 앱입니다.
- 테스트 또는 프로덕션 컴퓨터에 이미 배포 되어 실행 되 고 있는 기존 앱입니다.
- 웹에 위치하며 URL을 통해 액세스합니다.
- DLL을 포함 하는 웹 페이지를 포함 하는 웹 앱입니다.

호출 하는 앱에서 DLL을 디버깅 하려면 다음을 수행할 수 있습니다.

- 호출 앱에 대 한 프로젝트를 열고 **디버그**  > **디버깅 시작** 또는 **F5**키를 선택 하 여 디버깅을 시작 합니다.

  or

- 테스트 또는 프로덕션 컴퓨터에 이미 배포 되어 실행 되 고 있는 앱에 연결 합니다. 웹 사이트 또는 웹 앱의 Dll에이 방법을 사용 합니다. 자세한 내용은 [방법: 실행 중인 프로세스에 연결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)을 참조하세요.

호출 하는 응용 프로그램에 대 한 디버깅을 시작 하기 전에 DLL에서 중단점을 설정 합니다. [중단점 사용](../debugger/using-breakpoints.md)을 참조 하세요. DLL 중단점이 적중 되 면 코드를 단계별로 실행 하 여 각 줄에서 작업을 관찰할 수 있습니다. 자세한 내용은 [디버거에서 코드 탐색](../debugger/navigating-through-code-with-the-debugger.md)을 참조 하세요.

디버깅 하는 동안 **모듈** 창을 사용 하 여 앱이 로드 하는 dll 및 *.exe* 파일을 확인할 수 있습니다. 디버깅 하는 동안 **모듈** 창을 열려면 **디버그**  > **Windows**  > **모듈**을 선택 합니다. 자세한 내용은 [방법: 모듈 창](../debugger/how-to-use-the-modules-window.md)을 참조하세요.

### <a name="vxtskdebuggingdllprojectstheimmediatewindow"></a>직접 실행 창 사용

**직접 실행** 창을 사용 하 여 디자인 타임에 DLL 함수 또는 메서드를 평가할 수 있습니다. **직접 실행** 창에서 호출 하는 앱의 역할이 재생 됩니다.

>[!NOTE]
>디자인 타임에 대부분의 프로젝트 형식에서 **직접 실행** 창을 사용할 수 있습니다. SQL, 웹 프로젝트 또는 스크립트에 대해서는 지원 되지 않습니다.

예를 들어 클래스 `Class1`에서 `Test` 라는 메서드를 테스트 하려면 다음을 수행 합니다.

1. DLL 프로젝트가 열려 있는 상태에서 **디버그**  > **Windows**  > **즉시** 선택 하거나 **Ctrl** +**Alt** +**I**를 눌러 **직접 실행** 창을 엽니다.

1. C# **직접 실행** 창에서 다음 코드를 입력 하 고 **enter**키를 눌러 `Class1` 형식의 개체를 인스턴스화합니다. 이 관리 코드는 및 C# Visual Basic에 대해 작동 하며 적절 한 구문을 변경 합니다.

   ```csharp
   Class1 obj = new Class1();
   ```

   C#에서 모든 이름은 정규화되어야 합니다. 언어 서비스에서 식을 계산 하려고 할 때 모든 메서드나 변수는 현재 범위와 컨텍스트에 있어야 합니다.

1. `Test` 에서 `int` 매개 변수 하나를 사용하는 것으로 가정하고 `Test` 직접 실행 **창을 사용하여** 를 실행합니다.

   ```csharp
   ?obj.Test(10);
   ```

   [ **직접 실행** ] 창에 결과가 출력 됩니다.

1. 중단점을 배치한 다음, 함수를 다시 실행하여 `Test`를 계속 디버깅할 수 있습니다.

   중단점에 도달 하면 `Test`를 단계별로 실행 할 수 있습니다. 실행이 `Test`를 벗어나면 디버거가 디자인 모드로 되돌아갑니다.

## <a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> 혼합 모드 디버깅

관리 코드 또는 네이티브 코드에서 DLL에 대 한 호출 앱을 작성할 수 있습니다. 네이티브 앱이 관리 되는 DLL을 호출 하 고 둘 다 디버깅 하려는 경우 프로젝트 속성에서 관리 되는 디버거와 네이티브 디버거를 모두 사용 하도록 설정할 수 있습니다. 정확한 프로세스는 DLL 프로젝트 또는 호출 하는 앱 프로젝트에서 디버깅을 시작할지 여부에 따라 달라 집니다. 자세한 내용은 [방법: 혼합 모드에서 디버깅](../debugger/how-to-debug-in-mixed-mode.md)을 참조하세요.

관리 되는 호출 프로젝트에서 네이티브 DLL을 디버그할 수도 있습니다. 자세한 내용은 [관리 코드 및 네이티브 코드를 디버깅 하는 방법](how-to-debug-managed-and-native-code.md)을 참조 하세요.

## <a name="see-also"></a>참조
- [관리 코드 디버그](../debugger/debugging-managed-code.md)
- [프로젝트 디버그 C++ 준비](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [C#, F# 및 Visual Basic 프로젝트 형식](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [C# 디버그 구성을 위한 프로젝트 설정](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [C# 디버그 구성을 위한 프로젝트 설정](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Visual Basic 디버그 구성을 위한 프로젝트 설정](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [디버거 보안](../debugger/debugger-security.md)
