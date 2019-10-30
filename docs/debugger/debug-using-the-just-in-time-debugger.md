---
title: Just-in-time 디버거를 사용 하 여 디버그 | Microsoft Docs
ms.date: 09/24/2018
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 32a3ebd6e9047271a21425ac5b7eaaf715955b61
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911387"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Visual Studio에서 Just-in-time 디버거를 사용 하 여 디버그

Just-in-time 디버깅은 Visual Studio 오류가 발생 하거나 충돌 하는 앱을 실행 하는 경우 Visual Studio를 자동으로 시작할 수 있습니다. Just-in-time 디버깅을 사용 하면 Visual Studio 외부에서 앱을 테스트 하 고, 문제가 발생 하는 경우 Visual Studio를 열어 디버깅을 시작할 수 있습니다.

Just-in-time 디버깅은 Windows 데스크톱 앱에 대해 작동 합니다. 유니버설 Windows 앱 또는 시각화 도우미와 같은 네이티브 응용 프로그램에서 호스팅되는 관리 코드에 대해서는 작동 하지 않습니다.

> [!TIP]
> Just-in-time 디버거 대화 상자를 중지 하 고 Visual Studio를 설치 하지 않은 경우 just-in-time [디버거 사용 안 함](../debugger/just-in-time-debugging-in-visual-studio.md)을 참조 하세요. Visual Studio를 설치한 후에 [는 Windows 레지스트리에서 just-in-time 디버깅을 사용 하지 않도록 설정](#disable-just-in-time-debugging-from-the-windows-registry)해야 할 수 있습니다.

## <a name="BKMK_Enabling"></a>Visual Studio에서 Just-in-time 디버깅 사용 또는 사용 안 함

>[!NOTE]
>Just-in-time 디버깅을 사용 하거나 사용 하지 않도록 설정 하려면 관리자 권한으로 Visual Studio를 실행 해야 합니다. Just-in-time 디버깅을 사용 하거나 사용 하지 않도록 설정 하면 레지스트리 키가 설정 되 고 해당 키를 변경 하려면 관리자 권한이 필요할 수 있습니다. Visual Studio를 관리자로 열려면 Visual Studio 앱을 마우스 오른쪽 단추로 클릭 하 고 **관리자 권한으로 실행**을 선택 합니다.

Visual Studio **Tools** > **옵션** (또는 **디버그** > **옵션**) 대화 상자에서 just-in-time 디버깅을 구성할 수 있습니다.

**Just-In-Time 디버깅을 활성화하거나 비활성화하려면:**

1. **도구** 또는 **디버그** 메뉴에서 **옵션** > **디버깅** > **just-in-time**을 선택 합니다.

   ![JIT 디버깅 사용 또는 사용 안 함](../debugger/media/dbg-jit-enable-or-disable.png "JIT 디버깅 사용 또는 사용 안 함")

1. **이러한 형식의 코드에 just-in-time 디버깅 사용** 상자에서 just-in-time 디버깅을 수행 하려는 코드 형식을 **관리**, **네이티브**및/또는 **스크립트**중에서 선택 합니다.

1. **확인**을 선택합니다.

Just-in-time 디버거를 사용 하지만 앱이 충돌 하거나 오류가 발생할 때 열리지 않는 경우 [just-in-time 디버깅 문제 해결](#jit_errors)을 참조 하세요.

## <a name="disable-just-in-time-debugging-from-the-windows-registry"></a>Windows 레지스트리에서 Just-in-time 디버깅을 사용 하지 않도록 설정

컴퓨터에 Visual Studio가 더 이상 설치되어 있지 않아도 Just-In-Time 디버깅은 계속 활성화되어 있습니다. Visual Studio가 더 이상 설치 되어 있지 않으면 Windows 레지스트리를 편집 하 여 Just-in-time 디버깅을 사용 하지 않도록 설정할 수 있습니다.

**레지스트리를 편집하여 Just-In-Time 디버깅을 비활성화하려면:**

1. Windows **시작** 메뉴에서 **레지스트리 편집기** (*regedit.exe*)를 실행 합니다.

2. **레지스트리 편집기** 창에서 다음 레지스트리 항목을 찾아 삭제 합니다.

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    ![JIT 레지스트리 키](../debugger/media/dbg-jit-registry.png "JIT 레지스트리 키")

3. 컴퓨터에서 64 비트 운영 체제를 실행 하는 경우 다음 레지스트리 항목도 삭제 합니다.

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    다른 레지스트리 키를 삭제 하거나 변경 하지 않도록 해야 합니다.

5. **레지스트리 편집기** 창을 닫습니다.

## <a name="enable-just-in-time-debugging-of-a-windows-form"></a>Windows Form의 Just-in-time 디버깅 사용

기본적으로 Windows forms 앱에는 복구할 수 있는 경우 앱을 계속 실행할 수 있도록 하는 최상위 예외 처리기가 있습니다. Windows Forms 앱이 처리 되지 않은 예외를 throw 하는 경우 다음과 같은 대화 상자가 표시 됩니다.

![Windows Form 처리 되지 않은 예외](../debugger/media/windowsformsunhandledexception.png "Windows Form 처리 되지 않은 예외")

표준 Windows Form 오류 처리 대신 Just-in-time 디버깅을 사용 하도록 설정 하려면 다음 설정을 추가 합니다.

- *Machine.config 또는* *\<앱 이름 > .exe* 파일의 `system.windows.forms` 섹션에서 `jitDebugging` 값을 `true`로 설정 합니다.

    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

- C++ Windows Form 응용 프로그램에서 *.config* 파일이 나 코드에서`true`로`DebuggableAttribute`을 설정 합니다. [/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format)만 사용하고 [/Og](/cpp/build/reference/og-global-optimizations)는 사용하지 않은 상태에서 컴파일하면 컴파일러에서 이 특성을 자동으로 설정합니다. 그러나 최적화 되지 않은 릴리스 빌드를 디버깅 하려는 경우에는 앱의 *AssemblyInfo* 파일에 다음 줄을 추가 하 여 `DebuggableAttribute`를 설정 해야 합니다.

   ```cpp
   [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
   ```

   자세한 내용은 <xref:System.Diagnostics.DebuggableAttribute>을 참조하십시오.

## <a name="BKMK_Using_JIT"></a>Just-in-time 디버깅 사용
이 예제에서는 앱에서 오류를 throw 하는 경우 Just-in-time 디버깅을 안내 합니다.

- 이러한 단계를 수행 하려면 Visual Studio가 설치 되어 있어야 합니다. Visual Studio가 없는 경우 무료 [Visual Studio Community Edition](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15)을 다운로드할 수 있습니다.

- Just-in-time **디버깅을 >  > ** **도구** > **옵션** 에서 just-in-time 디버깅을 [사용 하도록 설정](#BKMK_Enabling) 해야 합니다 **.**

이 예에서는 Visual Studio에서 [NullReferenceException](/dotnet/api/system.nullreferenceexception)을 C# throw 하는 콘솔 앱을 만듭니다.

1. C# Visual Studio에서 *ThrowsNullException*라는 콘솔 앱 ** > (** visual > console >  **Visual C#**  **콘솔 응용 프로그램** ** > )** 을 만듭니다. Visual Studio에서 프로젝트를 만드는 방법에 대 한 자세한 내용은 [연습: 간단한 응용 프로그램 만들기](/visualstudio/get-started/csharp/tutorial-wpf)를 참조 하세요.

1. Visual Studio에서 프로젝트가 열리면 *Program.cs* 파일을 엽니다. Main () 메서드를 콘솔에 줄을 출력 한 다음 NullReferenceException을 throw 하는 다음 코드로 바꿉니다.

   ```csharp
   static void Main(string[] args)
   {
       Console.WriteLine("we will now throw a NullReferenceException");
       throw new NullReferenceException("this is the exception thrown by the console app");
   }
   ```

1. 솔루션을 빌드하려면 **디버그** (기본값) 또는 **릴리스** 구성을 선택한 다음 **빌드** > **솔루션 다시**빌드를 선택 합니다.

   > [!NOTE]
   > - 전체 디버깅 환경에 대 한 **디버그** 구성을 선택 합니다.
   > - [릴리스](../debugger/how-to-set-debug-and-release-configurations.md) 구성을 선택 하는 경우이 절차를 수행 하려면 [내 코드만](../debugger/just-my-code.md) 해제 해야 합니다. **도구** > **옵션** > **디버깅**에서 **내 코드만 사용**을 선택 취소 합니다.

   빌드 구성에 대한 자세한 내용은 [빌드 구성 이해](../ide/understanding-build-configurations.md)를 참조하세요.

1. 프로젝트 폴더 ( *. ..\ThrowsNullException\ThrowsNullException\bin\Debug* 또는 *. ..\ThrowsNullException\ThrowsNullException\bin\Release*)에서 빌드된 앱 ThrowsNullException를 엽니다. C#

   다음 명령 창이 표시 됩니다.

   ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")

1. **Just-in-time 디버거 선택** 대화 상자가 열립니다.

   ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")

   **사용 가능한 디버거**에서 **원하는 Visual Studio 버전/버전 > \<새 인스턴스**를 선택 합니다 (아직 선택 하지 않은 경우).

1. **확인**을 선택합니다.

   ThrowsNullException 프로젝트는 Visual Studio의 새 인스턴스에서 열리고, 예외를 throw 한 줄에서 실행이 중지 됩니다.

   ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

이 시점에서 디버깅을 시작할 수 있습니다. 실제 앱을 디버깅 하는 경우 코드에서 예외를 throw 하는 이유를 확인 해야 합니다.

> [!CAUTION]
> 응용 프로그램에 신뢰할 수 없는 코드가 포함 된 경우 디버깅을 계속할지 여부를 결정할 수 있는 보안 경고 대화 상자가 나타납니다. 디버깅을 계속 하기 전에 코드를 신뢰할 수 있는지 여부를 결정 합니다. 직접 작성한 코드인지, 애플리케이션이 원격 컴퓨터에서 실행 중인 경우 프로세스 이름을 알 수 있는지 등을 확인합니다. 응용 프로그램이 로컬로 실행 되는 경우 컴퓨터에서 악성 코드가 실행 될 수 있는 가능성을 고려 합니다. 코드를 신뢰할 수 있는 것으로 판단 되 면 **확인**을 선택 합니다. 그렇지 않으면 **취소**를 선택합니다.

## <a name="jit_errors"></a>Just-in-time 디버깅 문제 해결

앱이 충돌할 때 Just-in-time 디버깅을 시작 하지 않는 경우 (Visual Studio에서 사용 하도록 설정 된 경우에도)

- Windows 오류 보고 컴퓨터에서 오류 처리를 수행 하는 것일 수 있습니다.

  이 문제를 해결 하려면 레지스트리 편집기를 사용 하 여 **값 데이터가** **1**인 **DWORD 값** 을 **사용 하지 않도록 설정**하 여 다음 레지스트리 키에 추가 합니다.

  - **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\Windows 오류 보고**

  - (64 비트 컴퓨터의 경우): **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows\Windows 오류 보고**

  자세한 내용은을 참조 하십시오 [. WER 설정](/windows/desktop/wer/wer-settings).

- 알려진 Windows 문제로 인해 Just-in-time 디버거가 실패할 수 있습니다.

  이 문제를 해결 하려면 **값 데이터가** **1**인 **Auto**의 **DWORD 값** 을 다음 레지스트리 키에 추가 합니다.

  - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug**

  - (64 비트 컴퓨터의 경우): **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug**

Just-in-time 디버깅 중 다음과 같은 오류 메시지가 표시 될 수 있습니다.

- **충돌 프로세스에 연결할 수 없습니다. 지정한 프로그램은 Windows 또는 MS-DOS 프로그램이 아닙니다.**

    디버거가 다른 사용자로 실행 중인 프로세스에 연결 하려고 했습니다.

    이 문제를 해결 하려면 Visual Studio에서 **프로세스에 연결** > **디버그** 를 열고 **사용 가능한 프로세스** 목록에서 디버깅할 프로세스를 찾습니다. 프로세스 이름을 모르는 경우에는 **Visual Studio Just-in-time Debugger** 대화 상자에서 프로세스 ID를 찾습니다. **사용 가능한 프로세스** 목록에서 프로세스를 선택 하 고 **연결**을 선택 합니다. **아니요** 를 선택 하 여 just-in-time 디버거 대화 상자를 닫습니다.

- **로그온한 사용자가 없으므로 디버거를 시작할 수 없습니다.**

    콘솔에 로그온 한 사용자가 없으므로 Just-in-time 디버깅 대화 상자를 표시할 사용자 세션이 없습니다.

    이 문제를 해결하려면 컴퓨터에 로그온합니다.

- **클래스가 등록되지 않았습니다.**

    디버거가 등록 되지 않은 COM 클래스를 만들려고 했습니다. 설치 문제가 원인일 수 있습니다.

    이 문제를 해결 하려면 Visual Studio 설치 관리자를 사용 하 여 Visual Studio 설치를 다시 설치 하거나 복구 합니다.

## <a name="see-also"></a>참조

- [디버거 보안](../debugger/debugger-security.md)
- [디버거 소개](../debugger/debugger-feature-tour.md)
- [옵션, 디버깅, Just-in-time 대화 상자](../debugger/just-in-time-debugging-options-dialog-box.md)
- [보안 경고: 신뢰할 수 없는 사용자가 소유한 프로세스에 연결 하면 위험할 수 있습니다. 다음 정보가 의심 스 럽 거 나 잘 모르겠으면이 프로세스에 연결 하지 마십시오.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
