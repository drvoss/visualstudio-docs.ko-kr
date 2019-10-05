---
title: Just-In-Time 디버거를 사용 하 여 디버그 | Microsoft Docs
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
ms.openlocfilehash: b2aff8e1b515f460e6fdc31a528e6730971b7853
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62853207"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Just-In-Time 디버거를 사용 하 여 Visual Studio에서 디버그

Just-in-time 디버깅 수 Visual Studio 자동으로 시작 하면 외부 Visual Studio 오류 또는 크래시를 실행 중인 앱입니다. Just In Time 디버깅, Visual Studio 외부에서 앱을 테스트 하 고 문제가 발생 한 경우 디버깅을 시작 하려면 Visual Studio를 열고 사용할 수 있습니다.

Just-in-time 디버깅은 Windows 데스크톱 앱에 대 한 작동합니다. 시각화 도우미 같은 네이티브 응용 프로그램에서 호스트 되는 관리 코드 또는 유니버설 Windows 앱에 대 한 작동 하지 않습니다.

> [!TIP]
> 만 하려는 경우는 Just-In-Time 디버거 대화 상자가 표시를 중지 하지만 하지 Visual studio가 설치를 참조 하십시오 [Just-In-Time 디버거를 사용 하지 않도록 설정](../debugger/just-in-time-debugging-in-visual-studio.md)합니다. 한 번 Visual Studio가 설치 되어 있으면 해야 [Windows 레지스트리에서 사용 하지 않도록 설정 하면 시간 디버깅](#disable-just-in-time-debugging-from-the-windows-registry)합니다.

## <a name="BKMK_Enabling"></a> Just In Time Visual Studio에서 디버깅을 사용할지 설정 합니다.

>[!NOTE]
>를 사용 하거나 Just In Time 디버깅을 사용 하지 않도록 설정 하려면 실행 해야 Visual Studio를 관리자 권한으로 합니다. 활성화 또는 비활성화 Just In Time 레지스트리 키를 설정 하는 디버깅 하 고 해당 키를 변경 하려면 관리자 권한이 필요할 수 있습니다. 관리자 권한으로 Visual Studio를 열려면 Visual Studio 앱을 마우스 오른쪽 단추로 클릭 하 고 선택 **관리자 권한으로 실행**합니다.

Just In Time Visual Studio에서 디버깅을 구성할 수 있습니다 **도구가** > **옵션** (또는 **디버그** > **옵션**) 대화 상자입니다.

**Just-In-Time 디버깅을 활성화하거나 비활성화하려면:**

1. 에 **도구** 하거나 **디버그** 메뉴에서 **옵션** > **디버깅**  >   **Just In Time**합니다.

   ![JIT 디버깅을 사용할지](../debugger/media/dbg-jit-enable-or-disable.png "JIT 디버깅을 사용할지")

1. 에 **이러한 유형의 코드에 Just-In-Time 디버깅 사용** 상자 시간 Just-디버그 하려면 디버그 하려는 코드의 형식을 선택 합니다. **관리 되는**, **네이티브**, 및/또는 **스크립트**합니다.

1. **확인**을 선택합니다.

시간에만 사용 하도록 설정 하면 앱 작동이 중단 되거나 오류를 참조 하는 경우 열리지 않으면 디버거, 하지만 [문제를 해결 하는 Just-In-Time 디버깅](#jit_errors)합니다.

## <a name="disable-just-in-time-debugging-from-the-windows-registry"></a>Just In Time Windows 레지스트리에서 디버깅을 사용 하지 않도록 설정

컴퓨터에 Visual Studio가 더 이상 설치되어 있지 않아도 Just-In-Time 디버깅은 계속 활성화되어 있습니다. Visual Studio가 설치 되지 않은, 경우에 Just In Time Windows 레지스트리를 편집 하 여 디버깅을 비활성화할 수 없습니다.

**레지스트리를 편집하여 Just-In-Time 디버깅을 비활성화하려면:**

1. Windows에서 **시작** 메뉴에서 실행 합니다 **레지스트리 편집기** (*regedit.exe*).

2. 에 **레지스트리 편집기** 창 찾기 및 다음 레지스트리 항목을 삭제 합니다.

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    ![JIT 레지스트리 키](../debugger/media/dbg-jit-registry.png "JIT 레지스트리 키")

3. 컴퓨터는 64 비트 운영 체제를 실행 하는 경우 다음 레지스트리 항목을 삭제 합니다.

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    삭제 하거나 다른 레지스트리 키를 변경할 필요가 있는지 확인 합니다.

5. 닫기 합니다 **레지스트리 편집기** 창입니다.

## <a name="enable-just-in-time-debugging-of-a-windows-form"></a>Just In Time 사용 Windows Form의 디버깅

기본적으로 Windows Form 앱에는 앱에 복구할 수 있는 경우 계속 실행 하는 최상위 예외 처리기를 있습니다. Windows Forms 앱에서 처리 되지 않은 예외를 throw 하는 경우 다음 대화 상자가 표시 됩니다.

![처리 되지 않은 예외를 Windows Form](../debugger/media/windowsformsunhandledexception.png "Windows 양식 처리 되지 않은 예외")

Just In Time 표준 Windows 폼 오류를 처리 하는 대신 디버깅을 사용 하도록 설정 하려면 이러한 설정을 추가 합니다.

- `system.windows.forms` 의 섹션을 *machine.config* 또는  *\<앱 이름 >. exe.config* 파일에서 설정 합니다 `jitDebugging` 값을 `true`:

    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

- 에 C++ Windows Form 응용 프로그램을 설정할 수도 `DebuggableAttribute` 에 `true` 에 *.config* 파일 또는 코드에서. [/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format)만 사용하고 [/Og](/cpp/build/reference/og-global-optimizations)는 사용하지 않은 상태에서 컴파일하면 컴파일러에서 이 특성을 자동으로 설정합니다. 그러나 최적화 되지 않은 릴리스 빌드 디버깅 하려는 경우 설정 해야 합니다 `DebuggableAttribute` 앱의 다음 줄을 추가 하 여 *AssemblyInfo.cpp* 파일:

   ```cpp
   [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
   ```

   자세한 내용은 <xref:System.Diagnostics.DebuggableAttribute>을 참조하세요.

## <a name="BKMK_Using_JIT"></a>Just In Time을 사용 하 여 디버깅
이 예제에서는 시간 하기만 하면 됩니다-앱에서 오류를 throw 하는 경우 디버깅을 안내 합니다.

- Visual Studio를 설치 하려면 다음이 단계를 수행 해야 합니다. Visual Studio가 없는 경우 무료 다운로드할 수 있습니다 [Visual Studio Community Edition](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15)합니다.

- 있는지 Just In Time을 확인은 디버깅 [활성화](#BKMK_Enabling) 에 **도구** > **옵션** > **디버깅**  >  **Just In Time**합니다.

예를 들어 해야는 C# 를 throw 하는 Visual Studio에서 콘솔 앱을 [NullReferenceException](/dotnet/api/system.nullreferenceexception).

1. Visual studio는 C# 콘솔 앱 (**파일** > **새로 만들기** > **프로젝트** > **C#**  >  **콘솔 응용 프로그램**) 라는 *ThrowsNullException*합니다. Visual Studio에서 프로젝트를 만드는 방법에 대 한 자세한 내용은 참조 하세요. [연습: 간단한 응용 프로그램](/visualstudio/get-started/csharp/tutorial-wpf)합니다.

1. Visual Studio에서 프로젝트가 열리면 엽니다는 *Program.cs* 파일입니다. 콘솔에 줄을 출력 하 고 다음 NullReferenceException을 throw 하는 다음 코드를 사용 하 여 main () 메서드를 바꿉니다.

   ```csharp
   static void Main(string[] args)
   {
       Console.WriteLine("we will now throw a NullReferenceException");
       throw new NullReferenceException("this is the exception thrown by the console app");
   }
   ```

1. 솔루션을 빌드하려면 선택 합니다 **디버깅할** (기본값) 또는 **릴리스** 구성을 선택한 후 **빌드** > **솔루션 다시 빌드** .

   > [!NOTE]
   > - 선택할 **디버그** 전체 디버깅 환경을 구성 합니다.
   > - 선택 하는 경우 [릴리스](../debugger/how-to-set-debug-and-release-configurations.md) 구성을 해제 해야 [Just My Code](../debugger/just-my-code.md) 이 절차를 수행 하려면. 아래 **도구** > **옵션** > **디버깅**을 선택 취소 **내 코드만**합니다.

   빌드 구성에 대한 자세한 내용은 [빌드 구성 이해](../ide/understanding-build-configurations.md)를 참조하세요.

1. 기본 제공된 앱을 엽니다 *ThrowsNullException.exe* 에서 프로그램 C# 프로젝트 폴더 ( *...\ThrowsNullException\ThrowsNullException\bin\Debug* 하거나 *...\ThrowsNullException\ ThrowsNullException\bin\Release*).

   다음 명령 창에 표시 됩니다.

   ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")

1. 합니다 **Just-In-Time 디버거 선택** 대화 상자가 열립니다.

   ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")

   아래 **사용 가능한 디버거**를 선택 **의 새 인스턴스 \<에 기본 Visual Studio 버전 >** 아직 선택 하지 않은 경우.

1. **확인**을 선택합니다.

   Visual Studio의 새 인스턴스에서 예외를 발생 시킨 줄에서 중지 된 실행과 ThrowsNullException 프로젝트를 엽니다.

   ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

이 시점에서 디버깅을 시작할 수 있습니다. 실제 앱을 디버깅할 경우 코드는 예외를 throw 하는 이유를 확인 해야 합니다.

> [!CAUTION]
> 신뢰할 수 없는 코드를 포함 하는 앱을 디버깅을 계속할지 여부를 결정할 수 있도록 보안 경고 대화 상자가 나타납니다. 디버깅을 계속 하기 전에 코드를 신뢰할 수 있는지 여부를 결정 합니다. 직접 작성한 코드인지, 애플리케이션이 원격 컴퓨터에서 실행 중인 경우 프로세스 이름을 알 수 있는지 등을 확인합니다. 앱을 로컬로 실행 중인 경우 컴퓨터에서 실행 되는 악성 코드가 될 가능성을 고려 합니다. 코드는 신뢰할 수 있는 하려는 경우 선택 **확인**합니다. 그렇지 않으면 **취소**를 선택합니다.

## <a name="jit_errors"></a> Just In Time 해결 디버깅

Just In Time 경우 디버깅 시작 되지 않는 앱 충돌 하는 경우 Visual Studio에서 사용 하도록 설정 하는 경우에:

- Windows 오류 보고 컴퓨터에 처리 오류 시간이 걸리는 수 없습니다.

  이 문제를 해결 하려면 추가 레지스트리 편집기를 사용을 **DWORD 값** 의 **사용 안 함**를 사용 하 여 **값 데이터** 의 **1**, 다음 레지스트리 키에:

  - **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\Windows 오류 보고**

  - (64 비트 컴퓨터)의 경우 **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows\Windows 오류 보고**

  자세한 내용은 참조 하세요. [합니다. WER 설정](https://docs.microsoft.com/windows/desktop/wer/wer-settings)합니다.

- 시간에만 알려진된 Windows 문제를 일으킬 수 디버거 실패 합니다.

  수정을 추가 하는 것을 **Dword** 의 **자동**를 사용 하 여 **값 데이터** 의 **1**, 다음 레지스트리 키에:

  - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug**

  - (64 비트 컴퓨터)의 경우 **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug**

Just In Time 중 다음 오류 메시지가 표시 될 수 있습니다 디버깅:

- **충돌 프로세스에 연결할 수 없습니다. 지정한 프로그램은 Windows 또는 MS-DOS 프로그램이 아닙니다.**

    디버거가 다른 사용자에서 실행 중인 프로세스에 연결 하려고 했습니다.

    Visual Studio에서이 문제를 해결 하려면 엽니다 **디버그** > **프로세스에 연결**를 디버그 하려면 프로세스를 찾습니다는 **사용 가능한 프로세스** 목록입니다. 프로세스의 이름을 모르는 경우의 프로세스 ID를 찾을 합니다 **Visual Studio Just-In-Time Debugger** 대화 합니다. 프로세스를 선택 합니다 **사용 가능한 프로세스** 목록에서 선택한 **연결**합니다. 선택 **No** 시간에서 Just를 해제 하려면 디버거 대화 합니다.

- **로그온한 사용자가 없으므로 디버거를 시작할 수 없습니다.**

    시간에 하면 표시할 사용자 세션이 이므로 콘솔에 로그온 한 사용자가 대화를 디버깅 합니다.

    이 문제를 해결하려면 컴퓨터에 로그온합니다.

- **클래스가 등록되지 않았습니다.**

    등록 되지 않은, 아마도 설치 문제로 인해 COM 클래스를 디버거에서 만들려고 합니다.

    이 문제를 해결 하려면 Visual Studio 설치 관리자를 사용 하 여 다시 설치 하거나 Visual Studio 설치를 복구 합니다.

## <a name="see-also"></a>참고자료

- [디버거 보안](../debugger/debugger-security.md)
- [디버거 소개](../debugger/debugger-feature-tour.md)
- [Just In Time, 디버깅, 옵션 대화 상자](../debugger/just-in-time-debugging-options-dialog-box.md)
- [보안 경고: 신뢰할 수 없는 사용자가 소유한 프로세스에 연결하면 위험할 수 있습니다. 아래의 정보가 의심스럽거나 잘 모르겠으면 이 프로세스에 연결하지 마세요.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
