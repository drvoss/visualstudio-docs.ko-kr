---
title: 컨테이너 로그, 환경 변수 및 파일 시스템 액세스
description: 도구 창을 통해 앱을 호스트하는 컨테이너 내에서 수행되는 작업을 확인하여 Visual Studio에서 컨테이너 기반 앱을 디버그하고 진단하는 기능을 향상하는 방법을 설명합니다.
author: ghogen
ms.author: ghogen
ms.topic: conceptual
ms.date: 05/06/2019
ms.technology: vs-azure
monikerRange: vs-2019
ms.openlocfilehash: 3fb9a52f990a2e492c63a6e71a7cc2063110c816
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/30/2019
ms.locfileid: "71126096"
---
# <a name="how-to-view-and-diagnose-containers-in-visual-studio"></a>Visual Studio에서 컨테이너를 살펴보고 진단하는 방법

**컨테이너** 창을 사용하여 앱을 호스트하는 컨테이너 내에서 수행되는 작업을 살펴볼 수 있습니다. 명령 프롬프트에서 Docker 명령을 실행하여 컨테이너에서 수행되는 작업을 살펴보고 진단하는 데 익숙한 경우, 이 창에서 제공하는 보다 편리한 방법으로 Visual Studio IDE 내에서 컨테이너를 모니터링할 수 있습니다.

> [!NOTE]
> 컨테이너 창은 현재 Visual Studio 2019용으로 [다운로드](https://aka.ms/vscontainerspreview)할 수 있는 미리 보기 확장으로 제공됩니다.

## <a name="prerequisites"></a>전제 조건

- [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) 설치
- [컨테이너 창 확장](https://aka.ms/vscontainerspreview) 설치

## <a name="view-information-about-your-containers"></a>컨테이너에 대한 정보 보기

컨테이너화된 .NET 프로젝트를 시작하면 **컨테이너** 창이 자동으로 열립니다. 언제든지 Visual Studio에서 컨테이너를 보려면 **Ctrl**+**Q**를 사용하여 Visual Studio 검색 상자를 활성화하고 `Containers`를 입력한 다음, 첫 번째 항목을 선택합니다. 주 메뉴에서 **컨테이너** 창을 열 수도 있습니다. **보기** > **다른 창** > **컨테이너** 메뉴 경로를 사용합니다.  

![컨테이너 창의 환경 탭 스크린샷](media/view-and-diagnose-containers/container-window.png)

왼쪽에는 로컬 컴퓨터의 컨테이너 목록이 표시됩니다. 솔루션과 연결된 컨테이너는 **솔루션 컨테이너** 아래에 표시됩니다. 오른쪽에는 **환경**, **포트**, **로그** 및 **파일** 탭이 포함된 창이 표시됩니다.

> [!TIP]
> **컨테이너** 도구 창이 Visual Studio에서 도킹되는 위치를 쉽게 사용자 지정할 수 있습니다. [Visual Studio에서 창 레이아웃 사용자 지정](/visualstudio/ide/customizing-window-layouts-in-visual-studio)을 참조하세요. 기본적으로 **컨테이너** 창은 디버거가 실행 중일 때 **조사식** 창에 도킹됩니다.

## <a name="view-environment-variables"></a>환경 변수 보기

**환경** 탭에는 컨테이너의 환경 변수가 표시됩니다. Dockerfile 또는 .env 파일 사용, Docker 명령을 사용하여 컨테이너를 시작할 때 -e 옵션 사용 등의 다양한 방법으로 앱의 컨테이너에 대해 이러한 변수를 설정할 수 있습니다.

![컨테이너 창의 환경 탭 스크린샷](media/view-and-diagnose-containers/container-environment-vars.png)

> [!NOTE]
> 환경 변수의 변경 내용은 실시간으로 반영되지 않습니다. 또한 이 탭의 환경 변수는 컨테이너의 시스템 환경 변수이며, 앱의 로컬 사용자 환경 변수는 반영되지 않습니다.

## <a name="view-port-mappings"></a>포트 매핑 보기

**포트** 탭에서 컨테이너에 적용된 포트 매핑을 확인할 수 있습니다.

![컨테이너 창의 포트 탭 스크린샷](media/view-and-diagnose-containers/container-ports.png)

잘 알려진 포트가 연결되어 있으므로, 포트에 제공된 콘텐츠가 있을 경우 링크를 클릭하여 브라우저를 열 수 있습니다.

## <a name="view-logs"></a>로그 보기

**로그** 탭에는 `docker logs` 명령의 결과가 표시됩니다. 기본적으로 이 탭에는 컨테이너의 stdout 및 stderr 스트림이 표시되지만, 출력을 구성할 수 있습니다. 자세한 내용은 [Docker 로깅](https://docs.docker.com/config/containers/logging/)을 참조하세요.  기본적으로 **로그** 탭은 로그를 스트리밍하지만, 탭의 **중지** 단추를 선택하여 스트리밍하지 않도록 설정할 수 있습니다.

![컨테이너 창의 로그 탭 스크린샷](media/view-and-diagnose-containers/containers-logs.jpg)

로그를 지우려면 **로그** 탭의 **지우기** 단추를 사용합니다.  모든 로그를 가져오려면 **새로 고침** 단추를 사용합니다.

> [!NOTE]
> Visual Studio는 자동으로 stdout 및 stderr을 **출력** 창으로 리디렉션하므로, Visual Studio에서 시작된 컨테이너(즉, **솔루션 컨테이너** 섹션의 컨테이너)의 로그는 이 탭에 표시되지 않습니다. **출력** 창을 대신 사용합니다.

## <a name="view-the-filesystem"></a>파일 시스템 보기

**파일** 탭에서 프로젝트가 포함된 앱 폴더를 비롯한 컨테이너의 파일 시스템을 볼 수 있습니다.

![컨테이너 창의 파일 탭 스크린샷](media/view-and-diagnose-containers/container-filesystem.png)

Visual Studio에서 파일을 열려면 파일을 찾아서 두 번 클릭하거나, 마우스 오른쪽 단추를 클릭하고 **열기**를 선택합니다. Visual Studio는 읽기 전용 모드로 파일을 엽니다.

![Visual Studio에서 보기 위해 열린 파일 스크린샷](media/view-and-diagnose-containers/container-file-open.png)

**파일** 탭을 사용하여 IIS 로그와 같은 애플리케이션 로그, 구성 파일 및 컨테이너 파일 시스템에 있는 기타 콘텐츠 파일을 볼 수 있습니다.

## <a name="start-stop-and-remove-containers"></a>컨테이너 시작, 중지 및 제거

기본적으로 **컨테이너** 창에는 Docker에서 관리하는 머신의 모든 컨테이너가 표시됩니다. 도구 모음 단추를 사용하여 컨테이너를 시작 또는 중지하거나, 더 이상 필요하지 않은 컨테이너를 제거(삭제)할 수 있습니다.  이 목록은 컨테이너를 만들거나 제거할 때 동적으로 업데이트됩니다.

## <a name="next-steps"></a>다음 단계

[컨테이너 도구 개요](overview.md)를 참조하여 Visual Studio에서 사용할 수 있는 컨테이너 도구에 대해 자세히 알아봅니다.

## <a name="see-also"></a>참고 항목

[Visual Studio의 컨테이너 개발](/visualstudio/containers)

[Visual Studio용 확장 마켓플레이스](https://marketplace.visualstudio.com/)
