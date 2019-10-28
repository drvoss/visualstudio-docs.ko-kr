---
title: Android 및 iOS에서 OpenGL ES 애플리케이션 빌드 | Microsoft Docs
ms.custom: ''
ms.date: 10/09/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 76a67886-df57-4a81-accb-2e3c2eaf607b
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: a15902278e9a73488b315729a2db6e8fb5d53935
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72588915"
---
# <a name="build-an-opengl-es-application-on-android-and-ios"></a>Android 및 iOS에서 OpenGL ES 애플리케이션 빌드

일반 코드를 공유하는 iOS 앱과 Android 앱에 대한 Visual Studio 솔루션 및 프로젝트를 만들 수 있습니다. 이 문서에서는 간단한 iOS 앱과 Android Native Activity 앱 둘 다를 만드는 솔루션 템플릿을 안내합니다. 앱에는 공통적으로 OpenGL ES를 사용하여 각 플랫폼에서 동일한 애니메이션 회전 큐브를 표시하는 C++ 코드가 있습니다. OpenGL ES(OpenGL for Embedded Systems 또는 GLES)는 다양한 모바일 디바이스에서 지원되는 2D 및 3D 그래픽 API입니다.

## <a name="requirements"></a>요구 사항

iOS 및 Android용 OpenGL ES 앱을 개발하려면 먼저 모든 시스템 요구 사항을 충족했는지 확인해야 합니다. Visual Studio 설치 관리자에서 C++를 사용한 모바일 개발 워크로드를 아직 설치하지 않았다면 설치합니다. OpenGL ES 템플릿을 가져오고 iOS용 빌드인 경우 선택적 C++ iOS 개발 도구를 포함시킵니다. Android 빌드의 경우 C++ Android 개발 도구 및 필요한 타사 도구를 설치합니다. Android NDK, Apache Ant 및 Google Android Emulator. Intel 플랫폼에서 에뮬레이터 성능을 향상시키려면 Intel HAXM(Hardware Accelerated Execution Manager)도 설치하는 것이 좋습니다. 다음으로 Intel HAXM 및 Android Emulator가 시스템에서 실행되도록 구성합니다. 자세한 내용 및 자세한 지침은 [C++를 사용한 플랫폼 간 모바일 개발 설치](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)를 참조하세요.

iOS 앱을 빌드 및 테스트하려면 Mac 컴퓨터가 필요하며 설치 지침에 따라 설치해야 합니다. iOS 개발을 위해 설치하는 방법에 대한 자세한 내용은 [iOS를 사용하여 빌드할 도구 설치 및 구성](../cross-platform/install-and-configure-tools-to-build-using-ios.md)을 참조하세요.

## <a name="create-a-new-opengles-application-project"></a>새 OpenGLES 애플리케이션 프로젝트 만들기

이 자습서에서는 먼저 새 OpenGL ES 애플리케이션 프로젝트를 만듭니다. 그런 다음 Android 에뮬레이터에서 기본 앱을 빌드하고 실행합니다. 그런 다음 iOS용 앱을 빌드하고 iOS 디바이스에서 앱을 실행합니다.

::: moniker range="vs-2017"

1. Visual Studio에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

1. **새 프로젝트** 대화 상자의 **템플릿**에서 **Visual C++** , > **플랫폼 간**을 차례로 선택한 후 **OpenGLES 애플리케이션(Android, iOS)** 템플릿을 선택합니다.

1. 앱의 이름을 *MyOpenGLESApp*과 같이 지정하고 **확인**을 선택합니다.

   ![새 OpenGLES 애플리케이션 프로젝트](../cross-platform/media/cppmdd_opengles_newproj.PNG "CPPMDD_OpenGLES_NewProj")

   새 솔루션이 만들어지고 솔루션 탐색기가 열립니다.

   ![솔루션 탐색기의 MyOpenGLESApp](../cross-platform/media/cppmdd_opengles_solexpl.PNG "CPPMDD_OpenGLES_SolExpl")

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

1. **새 프로젝트 만들기** 대화 상자에서 **OpenGLES 애플리케이션(Android, iOS)** 템플릿을 선택한 후 **다음**을 선택합니다.

1. **새 프로젝트 구성** 대화 상자의 **프로젝트 이름**에 *MyOpenGLESApp*과 같은 이름을 입력한 후 **만들기**를 선택합니다.

   새 솔루션이 만들어지고 솔루션 탐색기가 열립니다.

   ![솔루션 탐색기의 MyOpenGLESApp](../cross-platform/media/cppmdd_opengles_solexpl.PNG "CPPMDD_OpenGLES_SolExpl")

::: moniker-end

새 OpenGL ES 애플리케이션 솔루션에 라이브러리 프로젝트 3개와 애플리케이션 프로젝트 2개가 포함됩니다. 라이브러리 폴더에는 공유 코드 프로젝트 1개와 공유 코드를 참조하는 플랫폼별 프로젝트 2개가 포함됩니다.

- `MyOpenGLESApp.Android.NativeActivity`에는 Android에서 앱을 Native Activity로 구현하는 참조 및 글루 코드가 포함되어 있습니다. 글루 코드에서의 진입점은 `MyOpenGLESApp.Shared`의 공용 공유 코드를 포함하는 *main.cpp*에서 구현됩니다. 미리 컴파일된 헤더는 *pch.h*에 있습니다. 이 Native Activity 앱 프로젝트는 공유 라이브러리 *.so* 파일로 컴파일되며 `MyOpenGLESApp.Android.Packaging` 프로젝트에서 이 라이브러리를 선택합니다.

- `MyOpenGLESApp.iOS.StaticLibrary`는 `MyOpenGLESApp.Shared`의 공유 코드를 포함하는 iOS 정적 라이브러리( *.a*) 파일을 만듭니다. `MyOpenGLESApp.iOS.Application` 프로젝트에서 만든 앱에 연결되어 있습니다.

- `MyOpenGLESApp.Shared`에는 플랫폼 간에 작동하는 공유 코드가 포함됩니다. 플랫폼별 코드의 조건부 컴파일에 전처리기 매크로를 사용합니다. 공유 코드는 `MyOpenGLESApp.Android.NativeActivity` 및 `MyOpenGLESApp.iOS.StaticLibrary`에서 모두 프로젝트 참조에 의해 선택됩니다.

솔루션에는 Android 및 iOS 플랫폼용 앱을 빌드하는 두 프로젝트가 있습니다.

- `MyOpenGLESApp.Android.Packaging`은 Android 디바이스 또는 에뮬레이터에서 배포하기 위한 *.apk* 파일을 만듭니다. 이 파일에는 리소스와 매니페스트 속성을 설정하는 AndroidManifest.xml 파일이 포함되어 있습니다. Ant 빌드 프로세스를 제어하는 *build.xml* 파일도 포함되어 있습니다. 이 프로젝트는 기본적으로 시작 프로젝트로 설정되므로 Visual Studio에서 직접 배포 및 실행할 수 있습니다.

- `MyOpenGLESApp.iOS.Application`에는 `MyOpenGLESApp.iOS.StaticLibrary`의 C++ 정적 라이브러리 코드에 연결되는 iOS 앱을 만들기 위한 리소스와 Objective-C 붙이기 코드가 포함됩니다. 이 프로젝트는 Visual Studio 및 원격 에이전트에서 Mac으로 전송되는 빌드 패키지를 만듭니다. 이 프로젝트를 빌드하면 Visual Studio가 Mac에서 앱을 빌드하고 배포하기 위한 파일과 명령을 보냅니다.

## <a name="build-and-run-the-android-app"></a>Android 앱 빌드 및 실행

템플릿에서 만든 솔루션은 Android 앱을 기본 프로젝트로 설정합니다.  이 앱을 빌드 및 실행하여 설치 및 설정을 확인할 수 있습니다. 초기 테스트의 경우 Android용 에뮬레이터에 의해 설치된 디바이스 프로필 중 하나에서 앱을 실행합니다. 다른 대상에서 앱을 테스트하려는 경우 대상 에뮬레이터를 로드하거나 디바이스를 컴퓨터에 연결할 수 있습니다.

### <a name="to-build-and-run-the-android-native-activity-app"></a>Android Native Activity 앱을 빌드 및 실행하려면

1. 아직 선택하지 않은 경우 **솔루션 플랫폼** 드롭다운 목록에서 **x86**을 선택합니다.

   ![솔루션 플랫폼을 x86으로 설정](../cross-platform/media/cppmdd_opengles_solutionplat.png "CPPMDD_OpenGLES_SolutionPlat")

   X86을 사용하여 에뮬레이터를 대상으로 지정합니다. 디바이스를 대상으로 지정하려면 디바이스 프로세서에 따라 솔루션 플랫폼을 선택합니다. **솔루션 플랫폼** 목록이 표시되지 않는 경우 **단추 추가/제거** 목록에서 **솔루션 플랫폼**을 선택한 후 플랫폼을 선택합니다.

1. **솔루션 탐색기**에서 `MyOpenGLESApp.Android.Packaging` 프로젝트의 바로 가기 메뉴를 열고 **빌드**를 선택합니다.

   ![Android 패키징 프로젝트 빌드](../cross-platform/media/cppmdd_opengles_andbuild.png "CPPMDD_OpenGLES_AndBuild")

   출력 창에 솔루션의 Android 공유 라이브러리 및 Android 앱에 대한 빌드 프로세스 출력이 표시됩니다.

   ![Android 프로젝트용 출력 빌드](../cross-platform/media/cppmdd_opengles_andoutput.png "CPPMDD_OpenGLES_AndOutput")

1. 배포 대상으로 에뮬레이트된 Android 디바이스 프로필 중 하나를 선택합니다.

   ![배포 대상 선택](../cross-platform/media/cppmdd_opengles_pickemulator.png "CPPMDD_OpenGLES_PickEmulator")

   다른 에뮬레이터를 설치했거나 Android 디바이스를 연결한 경우 배포 대상 드롭다운 목록에서 선택할 수 있습니다. 앱을 실행하려면 빌드된 솔루션 플랫폼이 대상 디바이스의 플랫폼과 일치해야 합니다.

1. **F5** 키를 눌러 디버깅을 시작하거나 **Shift**+**F5**를 눌러 디버깅하지 않고 시작합니다.

   에뮬레이터가 시작됩니다. 코드를 로드하고 배포하는 데 몇 초 정도 걸릴 수 있습니다. 에뮬레이터에서 앱이 표시되는 방법은 다음과 같습니다.

   ![Android 에뮬레이터에서 실행 중인 앱](../cross-platform/media/cppmdd_opengles_andemulator.png "CPPMDD_OpenGLES_AndEmulator")

   앱이 시작되면 중단점을 설정하고 디버거를 사용하여 코드를 단계별로 실행하고 지역을 검토하고 값을 조사할 수 있습니다.

1. **Shift**+**F5**를 눌러 디버깅을 중지합니다.

   에뮬레이터는 별도의 프로세스로 계속 실행됩니다. 코드를 편집 및 컴파일하여 동일한 에뮬레이터에 여러 번 배포할 수 있습니다. 앱이 에뮬레이터의 앱 컬렉션에 표시되고, 여기서 직접 시작할 수 있습니다.

   생성된 Android Native Activity 앱 및 라이브러리 프로젝트는 Android 플랫폼과 인터페이스하기 위한 "글루" 코드를 포함하는 C++ 공유 코드를 동적 라이브러리에 배치합니다. 대부분의 앱 코드는 라이브러리에 있고 매니페스트, 리소스 및 빌드 지침은 패키징 프로젝트에 있습니다. 공유 코드는 NativeActivity 프로젝트의 main.cpp에서 호출됩니다. Android NativeActivity를 프로그래밍하는 방법에 대한 자세한 내용은 Android 개발자 NDK [개념](https://developer.android.com/ndk/guides/concepts.html) 페이지를 참조하세요.

   Visual Studio는 Clang을 플랫폼 도구 집합으로 사용하는 Android NDK를 사용하여 Android Native Activity 프로젝트를 빌드합니다. Visual Studio는 NativeActivity 프로젝트의 속성을 대상 플랫폼에서 컴파일, 연결 및 디버그하는 데 사용되는 옵션에 매핑합니다. 자세한 내용을 보려면 MyOpenGLESApp.Android.NativeActivity 프로젝트에 대한 **속성 페이지** 대화 상자를 엽니다. 명령줄 스위치에 대한 자세한 내용은 [Clang 컴파일러 사용자 설명서](http://clang.llvm.org/docs/UsersManual.html)를 참조하세요.

## <a name="build-and-run-the-ios-app-on-an-ios-device"></a>iOS 디바이스에서 iOS 앱 빌드 및 실행

iOS 앱 프로젝트는 Visual Studio에서 개발되고 편집되지만 라이선싱 제한 사항 때문에 Mac에서 빌드하고 배포해야 합니다. Visual Studio는 Mac에서 실행되는 원격 에이전트와 통신하여 프로젝트 파일을 전송하고 빌드, 배포 및 디버깅 명령을 실행합니다. iOS 앱을 빌드하려면 먼저 Mac 및 Visual Studio를 통신하도록 설정 및 구성합니다. 자세한 내용은 [iOS를 사용하여 빌드할 도구 설치 및 구성](../cross-platform/install-and-configure-tools-to-build-using-ios.md)을 참조하세요. 원격 에이전트가 Mac에서 실행되고 Visual Studio와 쌍으로 연결되면 iOS 앱을 빌드 및 실행하여 설치 및 설정을 확인할 수 있습니다.

IOS 디바이스에 iOS 앱을 배포하려면 Mac의 Xcode에서 자동 서명도 설정해야 합니다. 자동 서명은 앱 서명을 자동으로 관리하고 앱 빌드를 서명할 프로비전 프로필을 만듭니다.

### <a name="to-set-up-automatic-signing-on-xcode"></a>Xcode에서 자동 서명을 설정하려면

1. 아직 설치하지 않은 경우 [Xcode](https://developer.apple.com/xcode/)를 Mac에 설치합니다.

1. Mac에서 Xcode 앱을 엽니다.

1. 새 **단일 뷰 애플리케이션** Xcode 프로젝트를 만듭니다. 프로젝트를 만드는 동안 필수 필드를 입력합니다. 프로젝트는 나중에 앱의 빌드에 서명하는 데 사용되는 프로비전 프로필을 만드는 데만 사용되므로 값은 임의의 값이 될 수 있습니다.

1. [Apple 개발자 프로그램](https://developer.apple.com/programs/) 계정에 등록된 Apple ID를 Xcode에 추가합니다. Apple ID는 앱을 서명하기 위한 서명 ID로 사용됩니다. Xcode에서 서명 ID를 추가하려면 **Xcode** 메뉴를 열고 **기본 설정**을 선택합니다. **계정**을 선택하고 추가 단추(+)를 클릭하여 Apple ID를 추가합니다. 자세한 지침은 [Apple ID 계정 추가](https://help.apple.com/xcode/mac/current/#/devaf282080a)를 참조하세요.

1. Xcode 프로젝트의 “일반” 설정에서 **번들 식별자**의 값을 `com.<NameOfVSProject>`로 변경합니다. 여기서 `<NameOfVSProject>`는 Visual Studio 솔루션 프로젝트의 이름으로 만들었던 이름과 같습니다. 예를 들어 Visual Studio에서 `MyOpenGLESApp`이라는 프로젝트를 만들었다면 **번들 식별자**를 `com.MyOpenGLESApp`으로 설정합니다.

   ![Xcode 번들 식별자](../cross-platform/media/cppmdd-opengles-iosxcodeid.png "CPPMDD_OpenGLES_iOSXcodeId")

1. 자동 서명을 사용하도록 설정하려면 확인합니다. 자동으로 서명 관리**.

   ![Xcode 자동 서명](../cross-platform/media/cppmdd-opengles-iosxcodesign.png "CPPMDD_OpenGLES_iOSXcodeSign")

1. 추가한 Apple ID의 팀 이름을 개발 **팀**으로 선택합니다.

   ![Xcode 팀](../cross-platform/media/cppmdd-opengles-iosxcodeteam.png "CPPMDD_OpenGLES_iOSXcodeTeam")

### <a name="to-build-and-run-the-ios-app-on-an-ios-device"></a>iOS 디바이스에서 iOS 앱을 빌드 및 실행하려면

1. Mac에서 원격 에이전트를 실행하고 Visual Studio가 원격 에이전트와 쌍으로 연결되었는지 확인합니다. 원격 에이전트를 시작하려면 터미널 앱 창을 열고 `vcremote`를 참조하세요. 자세한 내용은 [Visual Studio에서 원격 에이전트 구성](../cross-platform/install-and-configure-tools-to-build-using-ios.md#ConfigureVS)을 참조하세요.

   ![vcremote를 실행하는 Mac 터미널 창](../cross-platform/media/cppmdd_common_vcremote.png "CPPMDD_common_vcremote")

1. iOS 디바이스를 Mac에 첨부합니다. 컴퓨터에 처음으로 디바이스를 첨부한 경우 디바이스에 액세스하는 컴퓨터를 신뢰할 수 있는지 묻는 경고 메시지가 나타납니다. Mac 컴퓨터를 신뢰하도록 디바이스를 설정합니다.

1. Visual Studio에서 아직 선택하지 않은 경우 디바이스 프로세서에 따라 나타나는 **솔루션 플랫폼** 드롭다운 목록에서 솔루션 플랫폼을 선택합니다. 이 예제에서는 **ARM64** 프로세서입니다.

   ![솔루션 플랫폼을 ARM64로 설정](../cross-platform/media/cppmdd-opengles-pickplatformarm64.png "CPPMDD_OpenGLES_SolutionPlatARM64")

1. 솔루션 탐색기에서 MyOpenGLESApp.iOS.Application 프로젝트의 바로 가기 메뉴를 열고 **프로젝트 언로드**를 선택하여 프로젝트를 언로드합니다.

1. 언로드된 MyOpenGLESApp.iOS.Application 프로젝트의 바로 가기 메뉴를 다시 열고 **project.pbxproj 편집**을 선택하여 프로젝트 파일을 편집합니다. `project.pbxproj` 파일에서 `buildSettings` 특성을 찾고 Apple Team ID를 사용하여 `DEVELOPMENT_TEAM`을 추가합니다. 아래 스크린샷은 Apple Team ID의 `123456ABC` 예제 값을 보여 줍니다. Xcode에서 Apple Team ID의 값을 찾을 수 있습니다. **설정 빌드**로 이동하여 개발 팀 이름 위에 마우스 단추를 놓으면 도구 설명이 표시됩니다. 도구 설명에 팀 ID가 나타납니다.

   ![개발 팀 설정](../cross-platform/media/cppmdd-opengles-iosdevelopmentteam.png "CPPMDD_OpenGLES_iOSDevelopmentTeam")

1. `project.pbxproj` 파일을 닫고 언로드된 MyOpenGLESApp.iOS.Application 프로젝트의 바로 가기 메뉴를 연 다음 **프로젝트 다시 로드**를 선택하여 프로젝트를 다시 로드합니다.

1. 이제 프로젝트의 바로 가기 메뉴를 열고 **빌드**를 선택하여 MyOpenGLESApp.iOS.Application 프로젝트를 빌드합니다.

   ![iOS 애플리케이션 프로젝트 빌드](../cross-platform/media/cppmdd_opengles_iosbuild.png "CPPMDD_OpenGLES_iOSBuild")

   출력 창에 솔루션의 iOS 정적 라이브러리 및 iOS 앱에 대한 빌드 프로세스 출력이 표시됩니다. Mac에서 원격 에이전트를 실행하는 터미널 창에 명령 및 파일 전송 작업이 표시됩니다.

   Mac 컴퓨터에서 키체인에 액세스하기 위해 코드 서명을 허용할지 묻는 메시지가 표시될 수 있습니다. 계속하려면 **허용**을 선택합니다.

1. Mac에 첨부된 디바이스에서 앱을 실행하려면 도구 모음에서 iOS 장치를 선택합니다. 앱이 시작되지 않으면 배포된 애플리케이션을 디바이스에서 실행할 수 있는 권한이 있는지 확인합니다. 이 권한은 디바이스에서 **설정** > **일반** > **디바이스 관리**로 이동하여 설정할 수 있습니다. 개발자 앱 계정을 선택하고 계정을 신뢰하도록 설정한 후 앱을 확인합니다. Visual Studio에서 앱을 다시 실행해 봅니다.

   ![iOS 디바이스의 iOS 앱](../cross-platform/media/cppmdd-opengles-iosdevice.png "CPPMDD_OpenGLES_iOSDevice")

   앱이 시작되면 중단점을 설정하고 Visual Studio 디버거를 사용하여 지역을 검사하고, 호출 스택을 확인하고, 값을 조사할 수 있습니다.

   ![iOS 앱의 중단점에 있는 디버거](../cross-platform/media/cppmdd_opengles_iosdebug.png "CPPMDD_OpenGLES_iOSDebug")

1. **Shift**+**F5**를 눌러 디버깅을 중지합니다.

   생성된 iOS 앱 및 라이브러리 프로젝트는 공유 코드만 구현하는 C++ 코드를 정적 라이브러리에 넣습니다. 대부분의 애플리케이션 코드는 `Application` 프로젝트에 있습니다. 이 템플릿 프로젝트의 공유 라이브러리 코드 호출은 *GameViewController.m* 파일에서 수행됩니다. iOS 앱을 빌드하기 위해 Visual Studio는 Mac에서 실행되는 원격 클라이언트와 통신해야 하는 Xcode 플랫폼 도구 집합을 사용합니다.

   Visual Studio는 프로젝트 파일을 전송하고 Xcode를 사용하여 앱을 빌드하는 명령을 원격 클라이언트에 보냅니다. 원격 클라이언트는 빌드 상태 정보를 Visual Studio로 다시 보냅니다. 앱이 성공적으로 빌드된 경우 Visual Studio를 사용하여 앱을 실행 및 디버그하는 명령을 보낼 수 있습니다. Visual Studio의 디버거는 Mac에 첨부된 iOS 디바이스에서 실행되는 앱을 제어합니다. Visual Studio는 StaticLibrary 프로젝트의 속성을 대상 iOS 플랫폼에서 컴파일, 연결 및 디버그하는 데 사용되는 옵션에 매핑합니다. 컴파일러 명령줄 옵션에 대한 자세한 내용을 보려면 MyOpenGLESApp.iOS.StaticLibrary 프로젝트에 대한 **속성 페이지** 대화 상자를 엽니다.

## <a name="customize-your-apps"></a>앱 사용자 지정

공유 C++ 코드를 수정하여 공통 기능을 추가하거나 변경할 수 있습니다. 일치시킬 `MyOpenGLESApp.Android.NativeActivity` 및 `MyOpenGLESApp.iOS.Application` 프로젝트에서 공유 코드 호출을 변경해야 합니다. 전처리기 매크로를 사용하여 공통 코드에서 플랫폼별 섹션을 지정할 수 있습니다. 전처리기 매크로 `__ANDROID__` 는 Android용으로 빌드할 때 미리 정의됩니다. 전처리기 매크로 `__APPLE__` 는 iOS용으로 빌드할 때 미리 정의됩니다.

특정 프로젝트 플랫폼에 대한 IntelliSense를 보려면 편집기 창의 위쪽 탐색 모음에 있는 컨텍스트 전환기 드롭다운에서 프로젝트를 선택합니다.

![편집기의 프로젝트 컨텍스트 전환기 드롭다운](../cross-platform/media/cppmdd_opengles_contextswitcher.png)

현재 프로젝트에 사용되는 코드의 IntelliSense 문제는 빨간색 물결선으로 표시됩니다. 다른 프로젝트의 문제는 자주색 물결선으로 표시됩니다. Visual Studio는 Java 또는 Objective-C 파일에 대해 코드 색 지정 또는 IntelliSense를 지원하지 않습니다. 그러나 여전히 원본 파일을 수정하고 리소스를 변경하여 애플리케이션 이름, 아이콘 및 기타 구현 세부 정보를 설정할 수 있습니다.
