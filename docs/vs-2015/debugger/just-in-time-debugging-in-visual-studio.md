---
title: Just-In-Time 디버깅
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
- CSharp
- VB
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
caps.latest.revision: 51
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ad2814dffa75809a318dc7cebe7831b5ecec7d29
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65690601"
---
# <a name="just-in-time-debugging-in-visual-studio"></a>Visual Studio에서 Just-In-Time 디버깅
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Just-in-time 디버깅 Visual Studio 자동으로 시작 외부 Visual Studio를 실행 하는 응용 프로그램에서 예외 또는 충돌이 발생 합니다. 이 옵션을 사용 하면 Visual Studio 실행 중이지 않을 때 응용 프로그램을 테스트 하 고 문제가 발생 한 경우 Visual Studio를 사용 하 여 디버깅을 시작할 수 있습니다.

Just-in-time 디버깅은 Windows 데스크톱 앱에 대 한 작동합니다. Windows 유니버설 앱에 대 한 작동 하지 않습니다 하 고 시각화 도우미 같은 네이티브 응용 프로그램에서 호스트 되는 관리 코드에 대해 작동 하지 않습니다.

## <a name="BKMK_Scenario"></a> 시간에서 Just 않은 앱을 실행 하려고 하면 디버거에서 대화 상자가 표시?

Visual Studio Just-에-시간을 표시 하는 경우 수행 해야 하는 작업을 수행 하려는 따라 달라 집니다 디버거 대화 상자:

#### <a name="if-you-want-to-get-rid-of-the-dialog-box-and-just-run-the-app-normally"></a>대화 상자를 제거 하 고만 하려는 경우 앱을 정상적으로 실행

1. (고급 사용자) Visual Studio가 설치 되어 있습니다 (또는 이전에 설치 했 고 제거) 하는 경우 [사용 하지 않도록 설정 하면 시간 디버깅](#BKMK_Enabling) 앱을 다시 실행 해 보세요.

2. Internet Explorer에서 웹 앱을 실행 하는 경우 스크립트 디버깅 사용 하지 않도록 설정 합니다.

    인터넷 옵션 대화 상자에서 스크립트 디버깅 사용 안 함 이 액세스할 수 있습니다 합니다 **Control Panel** / **네트워크 및 인터넷** / **인터넷 옵션** (정확한 단계에 따라 달라 집니다 버전 Windows 및 Internet Explorer)입니다.

    ![JITInternetOptions](../debugger/media/jitinternetoptions.png "JITInternetOptions")

3. 오류가 있는 웹 페이지를 다시 엽니다. 이 문제를 해결 되지 않으면 문제를 해결 하려면 웹 앱의 소유자에 게 문의 합니다.

4. 다른 유형의 Windows 앱을 실행 하는 경우에 오류를 해결 한 다음 앱의 수정 된 버전을 다시 설치 하는 앱의 소유자에 게 문의 해야 합니다.

#### <a name="if-you-want-to-fix-or-debug-the-error-advanced-users"></a>수정 하거나 (고급 사용자) 오류를 디버깅 하려는 경우

- 있어야 [Visual Studio가 설치 되어](https://visualstudio.microsoft.com/vs/older-downloads/) 디버그 하려고 하는 오류에 대 한 자세한 정보를 보려면. 참조 [를 사용 하 여 JIT](#BKMK_Using_JIT) 자세한 지침입니다. 오류를 해결 하 고 앱 수 없습니다, 오류를 해결 하려면 앱의 소유자에 게 문의 합니다.

## <a name="BKMK_Enabling"></a> 사용 하지 않도록 설정 하면 시간에 디버깅 사용 또는 사용
 Just In Time Visual Studio에서 디버깅을 사용 하지 않도록 설정 하거나 설정할 수 있습니다 **도구 / 옵션** 대화 상자.

#### <a name="to-enable-or-disable-just-in-time-debugging"></a>Just-In-Time 디버깅을 활성화하거나 비활성화하려면

1. Visual Studio를 엽니다. **도구** 메뉴에서 **옵션**을 클릭합니다.

2. 에 **옵션** 대화 상자를 선택 합니다 **디버깅** 폴더입니다.

3. 에 **디버깅** 폴더를 선택 합니다 **Just In Time** 페이지입니다.

4. 에 **Just-In-Time 디버깅 사용 이러한 유형의 코드** 상자 선택 하거나 취소 하는 해당 프로그램 형식: **관리 되는**, **네이티브**, 또는 **스크립트**합니다.

    활성화되어 있는 Just-In-Time 디버깅을 비활성화하려면 프로그램을 관리자 권한으로 실행해야 합니다. Just-In-Time 디버깅을 활성화하면 레지스트리 키가 설정되고 이 키를 변경하려면 관리자 권한이 있어야 합니다.

5. **확인**을 클릭합니다.

   컴퓨터에 Visual Studio가 더 이상 설치되어 있지 않아도 Just-In-Time 디버깅은 계속 활성화되어 있습니다. Visual Studio 설치 되어 있지 않으면 Just In Time Visual Studio에서 디버깅을 비활성화할 수 없습니다 **옵션** 대화 상자. 이 경우 Windows 레지스트리를 편집하여 Just-In-Time 디버깅을 비활성화할 수 있습니다.

#### <a name="to-disable-just-in-time-debugging-by-editing-the-registry"></a>레지스트리를 편집하여 Just-In-Time 디버깅을 비활성화하려면

1. 에 **시작** 메뉴, 검색 및 실행 `regedit.exe`

2. 에 **레지스트리 편집기** 창 찾기 및 다음 레지스트리 항목을 삭제 합니다.

    - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\DbgManagedDebugger

3. 컴퓨터는 64 비트 운영 체제를 실행 하는 경우 다음 레지스트리 항목을 삭제 합니다.

    - HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    - HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\DbgManagedDebugger

4. 실수로 다른 레지스트리 키를 삭제하거나 변경하지 않도록 주의합니다.

5. 닫기 합니다 **레지스트리 편집기** 창입니다.

> [!NOTE]
> Just 시간 서버 쪽 앱에 대 한 디버깅을 사용 하지 않도록 설정 하려는 경우 다음이 단계에서 문제를 해결 하지 IIS 응용 프로그램 설정에서 서버 쪽 디버깅을 해제 하 고 다시 시도 하세요.

#### <a name="to-enable-just-in-time-debugging-of-a-windows-form"></a>Windows Form에 Just-In-Time 디버깅을 사용하려면

1. 기본적으로 Windows Forms 애플리케이션에는 복구할 수 있는 경우 프로그램을 계속 실행할 수 있도록 하는 최상위 예외 처리기가 있습니다. 예를 들어, Windows Forms 응용 프로그램에서 처리 되지 않은 예외를 throw 하는 경우 다음과 같은 대화 상자가 나타납니다.

     ![WindowsFormsUnhandledException](../debugger/media/windowsformsunhandledexception.png "WindowsFormsUnhandledException")

     Windows Forms 응용 프로그램의 디버깅을 사용 하면 시간을에 다음과 같은 추가 단계를 수행 해야 합니다.

2. 설정 합니다 `jitDebugging` 값을 `true` 에 `system.windows.form` 합니다 machine.config 섹션 또는  *\<응용 프로그램 이름 >* . exe.config 파일:

    ```
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

3. C++ Windows Forms 애플리케이션의 경우 .config 파일이나 코드에서 `DebuggableAttribute`도 설정해야 합니다. [/Zi](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8)만 사용하고 [/Og](https://msdn.microsoft.com/library/d10630cc-b9cf-4e97-bde3-8d7ee79e9435)는 사용하지 않은 상태에서 컴파일하면 컴파일러에서 이 특성을 자동으로 설정합니다. 그러나 최적화되지 않은 릴리스 빌드를 디버깅하려면 이 특성을 직접 설정해야 합니다. 애플리케이션의 AssemblyInfo.cpp 파일에 다음 줄을 추가하여 이 특성을 설정할 수 있습니다.

    ```
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
    ```

     자세한 내용은 <xref:System.Diagnostics.DebuggableAttribute>을 참조하세요.

## <a name="a-namebkmk_using_jituse-just-in-time-debugging"></a><a name="BKMK_Using_JIT">Just-in-time 디버깅 사용
 이 섹션에서는 실행 예외를 throw 하는 경우 어떻게 되는지 보여 줍니다.

 Visual Studio를 설치 하려면 다음이 단계를 수행 해야 합니다. Visual Studio가 없는 경우 무료 다운로드할 수 있습니다 [Visual Studio 2015 Community Edition](https://visualstudio.microsoft.com/vs/older-downloads/)합니다.

 Visual Studio를 설치하면 Just-In-Time 디버깅이 기본적으로 활성화됩니다.

 이 섹션에서는 throw 하는 Visual Studio에서 C# 콘솔 앱을 만들어 보겠습니다는 <xref:System.NullReferenceException>합니다.

 Visual Studio에서 C# 콘솔 앱을 만듭니다 (**파일 / 새로 만들기 / 프로젝트 / Visual C# / 콘솔 응용 프로그램**) 이라는 **ThrowsNullException**합니다. Visual Studio에서 프로젝트를 만드는 방법에 대 한 자세한 내용은 참조 하세요. [연습: 간단한 응용 프로그램](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)합니다.

 Visual Studio에서 프로젝트가 열리면 Program.cs 파일을 엽니다. 콘솔에 줄을 출력 하 고 다음 NullReferenceException을 throw 하는 다음 코드를 사용 하 여 main () 메서드를 바꿉니다.

```csharp
static void Main(string[] args)
{
    Console.WriteLine("we will now throw a NullReferenceException");
    throw new NullReferenceException("this is the exception thrown by the console app");
}
```

> [!IMPORTANT]
> 이 절차에서 작동 하도록 하기 위해를 [릴리스 구성을](../debugger/how-to-set-debug-and-release-configurations.md)를 해제 해야 [Just My Code](../debugger/just-my-code.md)합니다. Visual Studio에서 클릭 **도구 / 옵션**합니다. 에 **옵션** 대화 상자에서 **디버깅**합니다. 검사를 제거 **내 코드만**합니다.

 솔루션을 빌드합니다 (Visual Studio에서 선택 **빌드 / 솔루션 다시 빌드**). 디버그 또는 릴리스 구성을 선택할 수 있습니다. 빌드 구성에 대한 자세한 내용은 [빌드 구성 이해](../ide/understanding-build-configurations.md)를 참조하세요.

 빌드 프로세스는 실행 ThrowsNullException.exe를 만듭니다. C# 프로젝트를 만든 폴더에서 찾을 수 있습니다: **...\ThrowsNullException\ThrowsNullException\bin\Debug** 하거나 **...\ThrowsNullException\ThrowsNullException\bin\Release**합니다.

 ThrowsNullException.exe를 두 번 클릭 합니다. 이 같은 명령 창이 표시 됩니다.

 ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")

 몇 초 후 오류 창이 나타납니다.

 ![ThrowsNullExceptionError](../debugger/media/throwsnullexceptionerror.png "ThrowsNullExceptionError")

 클릭 하지 마세요 **취소**! 두 개의 단추를 몇 초 후 표시 **디버그** 하 고 **프로그램을 닫아**합니다. 클릭 **디버그**합니다.

> [!CAUTION]
> 응용 프로그램에 신뢰할 수 없는 코드가 보안 경고 대화 상자가 나타납니다. 이 대화 상자에서 디버깅을 계속할지 여부를 결정할 수 있습니다. 디버깅을 계속하기 전에 코드를 신뢰할 수 있는지 확인해야 합니다. 직접 작성한 코드인지, 코드 작성자를 신뢰할 수 있는지, 애플리케이션이 원격 컴퓨터에서 실행 중인 경우 프로세스 이름을 알 수 있는지 등을 확인합니다. 애플리케이션이 로컬로 실행 중이라고 해서 반드시 신뢰할 수 있는 것은 아닙니다. 컴퓨터에서 악의적인 코드가 실행 될 가능성을 고려 합니다. 코드를 하려는 경우 디버그를 신뢰할 수, 클릭 **디버그**합니다. 그렇지 않은 경우 클릭 **디버깅 하지 마십시오**합니다.

 합니다 **Visual Studio Just-In-Time Debugger** 창이 나타납니다.

 ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")

 아래 **사용 가능한 디버거**, 것을 확인할 수는 **Microsoft Visual Studio 2015의 새 인스턴스** 줄을 선택 합니다. 이미 선택 되지 않은 경우 지금 선택할.

 창의 맨 아래 **선택한 디버거를 사용 하 여 디버깅 하 시겠습니까?** , 클릭 **예**합니다.

 Visual Studio의 새 인스턴스를에서 예외를 throw 하는 줄에서 중지 된 실행과 ThrowsNullException 프로젝트를 엽니다.

 ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

 이 시점에서 디버깅을 시작할 수 있습니다. 실제 응용 프로그램의 경우 코드는 예외를 throw 하는 이유를 확인 해야 합니다.

## <a name="just-in-time-debugging-errors"></a>Just-In-Time 디버깅 오류
 프로그램이 충돌할 때 대화 상자를 표시 되지 않으면,이 컴퓨터에 Windows 오류 보고 설정으로 인해 수. 있습니다 자세한 내용은 참조 하세요. [합니다. WER 설정](https://msdn.microsoft.com/library/windows/desktop/bb513638\(v=vs.85\).aspx)합니다.

 Just-In-Time 디버깅과 관련된 다음 오류 메시지가 나타날 수도 있습니다.

- **충돌 프로세스에 연결할 수 없습니다. 지정한 프로그램은 Windows 또는 MS-DOS 프로그램이 아닙니다.**

     이 오류는 다른 사용자로 실행 되는 프로세스에 연결 하려고 할 때 발생 합니다.

     Visual Studio 시작이이 문제를 해결 하려면 엽니다는 **프로세스에 연결** 대화 상자를 **디버그** 메뉴 및 찾기 프로세스에서 디버그 하려는 **사용 가능한 프로세스**목록입니다. 프로세스의 이름을 모르는 경우 확인 합니다 **Visual Studio Just-In-Time Debugger** 대화 및 참고 프로세스 id입니다. 프로세스를 선택 합니다 **사용 가능한 프로세스** 나열 하 고 클릭 **연결**합니다. 에 **Visual Studio Just-In-Time Debugger** 대화 상자에서 클릭 **No** 대화 상자를 닫습니다.

- **로그온한 사용자가 없으므로 디버거를 시작할 수 없습니다.**

     이 오류는 콘솔에 로그온한 사용자가 없는 컴퓨터에서 Just-In-Time 디버깅 시 Visual Studio를 시작하려고 할 때 발생합니다. 로그온한 사용자가 없으므로 Just-In-Time 디버깅 대화 상자를 표시할 사용자 세션이 없습니다.

     이 문제를 해결하려면 컴퓨터에 로그온합니다.

- **클래스가 등록되지 않았습니다.**

     이 오류는 설치 문제 등으로 인해 등록되지 않은 COM 클래스를 디버거에서 만들려고 했음을 의미합니다.

     이 문제를 해결하려면 설치 디스크를 사용하여 Visual Studio를 다시 설치하거나 Visual Studio 설치를 복구합니다.

## <a name="see-also"></a>참고 항목
 [디버거 보안](../debugger/debugger-security.md) [디버거 기본 사항](../debugger/debugger-basics.md) [-Just-in-time, 디버깅, 옵션 대화 상자](../debugger/just-in-time-debugging-options-dialog-box.md) [보안 경고: 신뢰할 수 없는 사용자가 소유한 프로세스에 연결하면 위험할 수 있습니다. 아래의 정보가 의심스럽거나 잘 모르겠으면 이 프로세스에 연결하지 마세요.](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015)
