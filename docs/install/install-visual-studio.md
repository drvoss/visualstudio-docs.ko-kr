---
title: Visual Studio 2017 설치 | Microsoft Docs
description: Visual Studio를 설치하는 방법을 단계별로 알아봅니다.
ms.custom: ''
ms.date: 05/07/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.about
helpviewer_keywords:
- install Visual Studio
- dev15
- set up Visual Studio
- Visual Studio setup
- Visual Studio installer
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7c3ba26f014b09624b1a8fec88bed8a5aefa632b
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349692"
---
# <a name="install-visual-studio-2017"></a>Visual Studio 2017 설치

Visual Studio를 설치하는 새로운 방법이 있습니다. 최신 버전에서는 필요한 기능만 보다 쉽게 선택하여 설치할 수 있도록 만들었습니다. 시스템에 미치는 영향을 이전보다 최소화하여 Visual Studio가 더 빨리 설치되도록 최소 사용 공간도 줄였습니다.

> [!NOTE]
> 이 토픽은 Windows의 Visual Studio에 적용됩니다. Mac용 Visual Studio는 [Mac용 Visual Studio 설치](/visualstudio/mac/installation)를 참조하세요.

이 버전의 다른 새로운 기능에 대해 자세히 알고 싶으세요? [릴리스 정보](/visualstudio/releasenotes/vs2017-relnotes)를 참조하세요.

설치할 준비가 되었나요? 설치 과정을 단계별로 안내합니다.

## <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>1단계 - Visual Studio에 대해 컴퓨터가 준비되었는지 확인

Visual Studio 설치를 시작하기 전에

1. [시스템 요구 사항](/visualstudio/productinfo/vs2017-system-requirements-vs)을 확인합니다. 이러한 요구 사항은 컴퓨터에서 Visual Studio 2017을 지원하는지 여부를 확인하는 데 도움이 됩니다.
2. 최신 Windows 업데이트를 적용합니다. 이러한 업데이트는 컴퓨터에 최신 보안 업데이트와 Visual Studio에 필요한 시스템 구성 요소가 모두 설치되어 있는지 확인합니다.
3. 다시 부팅합니다. 다시 부팅하면 보류 중인 설치 또는 업데이트가 Visual Studio 설치를 방해하지 않습니다.
4. 공간을 확보합니다. 예를 들어 디스크 정리 앱을 실행하여 %SystemDrive%에서 불필요한 파일 및 응용 프로그램을 제거합니다.

Visual Studio 2017과 함께 이전 버전의 Visual Studio를 나란히 실행하는 방법에 대한 의문 사항은 [Visual Studio 호환성 정보](/visualstudio/productinfo/vs2017-compatibility-vs#compatibility-with-previous-releases)를 참조하세요.

## <a name="step-2---download-visual-studio"></a>2단계 - Visual Studio 다운로드

다음으로 Visual Studio 부트스트래퍼 파일을 다운로드합니다. 이렇게 하려면 다음 단추를 클릭하고, 원하는 Visual Studio 2017 버전을 선택하고, **저장**을 클릭하고, **폴더 열기**를 클릭합니다.

 > [!div class="button"]
 > [Visual Studio 2017 다운로드](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
<br/>

|         |         |
|---------|---------|
|  ![비디오에 대한 비디오 카메라 아이콘](media/video-icon.png "비디오 보기")  |    Visual Studio 부트스트래퍼 파일을 다운로드하고 적합한 Visual Studio의 버전을 선택하는 방법에 대한 [비디오를 봅니다](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Download-the-Visual-Studio-Installer-GgrESHD6D_3311787171). |

## <a name="step-3---install-the-visual-studio-installer"></a>3단계 - Visual Studio 설치 관리자 설치

그런 다음 Visual Studio 설치 관리자를 설치하려면 부트스트래퍼 파일을 실행합니다. 이 새 경량 설치 관리자는 Visual Studio 2017을 설치하고 사용자 지정하는 데 필요한 모든 항목을 포함합니다.

1. **다운로드** 폴더에서 다음 파일 중 하나와 일치하거나 비슷한 부트스트래퍼 파일을 두 번 클릭합니다.

   * Visual Studio Enterprise용 **vs_enterprise.exe**
   * Visual Studio Professional용 **vs_professional.exe**
   * Visual Studio Community용 **vs_community.exe**  <br><br>

   사용자 계정 컨트롤 알림을 받으면 **예**를 클릭합니다.

2. Microsoft [사용 약관](https://visualstudio.microsoft.com/license-terms/) 및 Microsoft [개인정보처리방침](https://privacy.microsoft.com/privacystatement)에 동의하도록 요청하는 메시지가 표시됩니다. **계속**을 클릭합니다.

   ![사용 조건 및 개인정보처리방침](media/vs2017-privacy-and-license-terms.PNG "Microsoft 사용 조건 및 개인정보처리방침")

## <a name="step-4---select-workloads"></a>4단계 - 워크로드 선택

설치 관리자를 설치한 후에 원하는 기능 집합이나 워크로드를 선택하여 설치를 사용자 지정하는 데 사용할 수 있습니다. 방법은 다음과 같습니다.

1. **Visual Studio 설치** 화면에서 원하는 작업을 찾습니다.

   ![Visual Studio 2017 설정 대화 상자에서 작업을 선택합니다.](../install/media/install-visual-studio-community.png)

     예를 들어 ".NET 데스크톱 개발" 작업을 선택합니다. 20개가 넘는 언어에 대한 기본 코드 편집 기능, 프로젝트 없이도 폴더에서 코드를 열어 편집할 수 있는 기능 및 통합 소스 코드 제어 기능이 포함된 기본 핵심 편집기가 제공됩니다.

2. 원하는 작업을 선택한 후 **설치**를 클릭합니다.

    다음으로 Visual Studio 설치 진행률을 보여 주는 상태 화면이 나타납니다.

3. 새 작업과 구성 요소가 설치된 후 **시작**을 클릭합니다.

> [!TIP]
> 설치 후에 언제든지 초기에 설치하지 않은 워크로드 또는 구성 요소를 설치할 수 있습니다. Visual Studio가 열려 있으면 **도구** > **도구 및 기능 가져오기...** 로 이동하여 Visual Studio 설치 관리자를 엽니다. 또는 [시작] 메뉴에서 **Visual Studio 설치 관리자**를 엽니다. 여기서 설치하려는 워크로드 또는 구성 요소를 선택한 다음 **수정**을 클릭합니다.

|         |         |
|---------|---------|
|  ![비디오에 대한 비디오 카메라 아이콘](media/video-icon.png "비디오 보기")  |    Visual Studio 설치 관리자를 설치하고 다음 워크로드를 설치하는 방법에 대한 [비디오를 봅니다](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Workloads-in-Visual-Studio-2017-jHE19HD6D_1611787171). |

## <a name="step-5---select-individual-components-optional"></a>5단계 - 개별 구성 요소 선택(선택 사항)

워크로드 기능을 사용하여 Visual Studio 설치를 사용자 지정하지 않으려면 대신 개별 구성 요소를 설치하여 수행할 수 있습니다. 개별 구성 요소를 선택하려면 Visual Studio 설치 관리자에서 **개별 구성 요소** 옵션을 클릭하고, 원하는 항목을 선택한 다음 표시되는 메시지를 따릅니다.

  ![Visual Studio 2017 - 개별 구성 요소 설치](media/vs2017-components.PNG "Visual Studio 개별 구성 요소 설치")

  |         |         |
  |---------|---------|
  |  ![비디오에 대한 비디오 카메라 아이콘](media/video-icon.png "비디오 보기")  |   Visual Studio 설치 관리자를 사용하여 개별 구성 요소를 설치하는 방법에 대한 [비디오를 봅니다](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Components-in-Visual-Studio-2017-ZMfaVID6D_7411787171). |

## <a name="step-6---install-language-packs-optional"></a>6단계 - 언어 팩 설치(선택 사항)

기본적으로 설치 관리자 프로그램은 처음 실행될 때 운영 체제의 언어와 일치시키려고 합니다. 선택한 언어로 Visual Studio 2017을 설치하려면 Visual Studio 설치 관리자에서 **언어 팩** 옵션을 클릭하고 프롬프트를 따릅니다.

  ![Visual Studio 2017 - 언어 팩 설치](media/vs2017-languages.PNG "Visual Studio 언어 팩 설치")

  |         |         |
  |---------|---------|
  |  ![비디오에 대한 비디오 카메라 아이콘](media/video-icon.png "비디오 보기")  |   Visual Studio 설치 관리자를 사용하여 언어 팩을 설치하는 방법에 대한 [비디오를 봅니다](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Language-Packs-in-Visual-Studio-2017-ByT7yID6D_9011787171). |

### <a name="change-the-installer-language-from-the-command-line"></a>명령줄에서 설치 관리자 언어 변경

기본 언어를 변경할 수 있는 다른 방법은 명령줄에서 설치 관리자를 실행하는 것입니다. 예를 들어 `vs_installer.exe --locale en-US` 명령을 사용하여 설치 관리자를 영어로 강제 실행할 수 있습니다. 설치 관리자는 다음에 실행될 때 이 설정을 기억합니다. 설치 관리자는 zh-cn, zh-tw, cs-cz, en-us, es-es, fr-fr, de-de, it-it, ja-jp, ko-kr, pl-pl, pt-br, ru-ru, and tr-tr과 같은 언어 토큰을 지원합니다.

## <a name="step-7---change-the-installation-location-optional"></a>7단계 - 설치 위치 변경(선택 사항)

**15.7의 새로운 기능**: 시스템 드라이브에서 Visual Studio의 설치 공간을 줄일 수 있습니다. 다운로드 캐시, 공유 구성 요소, SDK 및 도구를 다른 드라이브로 이동하고 Visual Studio를 가장 빠르게 실행되는 드라이브에 유지하도록 선택할 수 있습니다.

  ![Visual Studio 2017 - 설치 위치 변경](media/installation-options-by-location.png "설치 위치 변경")

자세한 내용은 [Visual Studio에서의 설치 위치 변경](change-installation-locations.md) 페이지를 참조하세요.

## <a name="step-8---start-developing"></a>8단계 - 개발 시작

1. Visual Studio 설치가 완료되면 **시작** 단추를 클릭하여 Visual Studio에서 개발을 시작합니다.

2. **파일**, **새 프로젝트**를 차례로 클릭합니다.

3. 프로젝트 형식을 선택합니다.

   예를 들어 [C++ 앱을 빌드](../ide/getting-started-with-cpp-in-visual-studio.md)하려면 **설치됨**을 클릭하고, **Visual C++** 를 확장한 다음, 빌드할 C++ 프로젝트 형식을 선택합니다.

   [C# 앱을 빌드](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)하려면 **설치됨**을 클릭하고, **Visual C#** 을 확장한 다음, 빌드할 C# 프로젝트 형식을 선택합니다.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>참고 항목

* [Visual Studio 2017 업데이트](update-visual-studio.md)
* [Visual Studio 2017 수정](modify-visual-studio.md)
* [Visual Studio 2017 제거](uninstall-visual-studio.md)
* [Visual Studio 2017의 오프라인 설치 만들기](create-an-offline-installation-of-visual-studio.md)
* [명령줄 매개 변수를 사용하여 Visual Studio 2017 설치](use-command-line-parameters-to-install-visual-studio.md)
* [Mac용 Visual Studio 설치](/visualstudio/mac/installation)