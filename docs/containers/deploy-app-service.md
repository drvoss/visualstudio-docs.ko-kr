---
title: Azure App Service에 ASP.NET Core Docker 컨테이너 배포 | Microsoft Docs
description: Visual Studio Container Tools를 사용하여 Azure App Service에 ASP.NET Core 웹앱을 배포하는 방법을 알아봅니다.
author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: article
ms.date: 03/08/2019
ms.author: ghogen
ms.openlocfilehash: 5d1f160435fd8c62a44d3e5d3192870143558de4
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188784"
---
# <a name="deploy-an-aspnet-core-container-to-azure-app-service-using-visual-studio"></a>Visual Studio를 사용하여 Azure App Service에 ASP.NET Core 컨테이너 배포

이 자습서에서는 Visual Studio를 사용하여 컨테이너화된 ASP.NET Core 웹 애플리케이션을 [Azure App Service](/azure/app-service)에 게시하는 방법을 설명합니다. Azure App Service는 Azure에 호스트된 단일 컨테이너 웹앱에 적합한 서비스입니다.

Azure 구독이 아직 없는 경우 시작하기 전에 [체험 계정](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs)을 만듭니다.

## <a name="prerequisites"></a>전제 조건

이 자습서를 완료하려면 다음이 필요합니다.

::: moniker range="vs-2017"
- "ASP.NET 및 웹 개발" 워크로드가 포함된 최신 버전의 [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)을 설치합니다.
::: moniker-end
::: moniker range=">=vs-2019"
- *ASP.NET 및 웹 개발* 워크로드가 있는 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)
::: moniker-end
- [Docker Desktop](https://docs.docker.com/docker-for-windows/install/) 설치

## <a name="create-an-aspnet-core-web-app"></a>ASP.NET Core 웹앱 만들기

다음 단계에서는 이 자습서에서 사용할 기본적인 ASP.NET Core 앱을 만드는 과정을 안내합니다.

::: moniker range="vs-2017"
1. Visual Studio 메뉴에서 **파일 > 새로 만들기 > 프로젝트**를 선택합니다.
2. **새 프로젝트** 대화 상자의 **템플릿** 섹션에서 **Visual C# > 웹**을 선택합니다.
3. **새 ASP.NET Core 웹 애플리케이션**을 선택합니다.
4. 새 애플리케이션에 이름을 지정(또는 기본값 사용)하고 **확인**을 선택합니다.
5. **웹 애플리케이션**을 선택합니다.
6. **Docker 지원 사용** 확인란을 선택합니다.
7. **Linux** 컨테이너 형식을 선택하고 **확인**을 클릭합니다. Windows 컨테이너는 Azure App Service에 컨테이너로 배포할 수 없습니다.
::: moniker-end
::: moniker range=">= vs-2019"
1. Visual Studio 시작 창에서 **새 프로젝트 만들기**를 선택합니다.
1. **ASP.NET Core 웹 애플리케이션**을 선택하고 **다음**을 선택합니다.
1. 새 애플리케이션에 이름을 지정(또는 기본값 사용)하고 **만들기**를 선택합니다.
1. **웹 애플리케이션**을 선택합니다.
1. **HTTPS에 대한 구성** 확인란을 사용하여 SSL 지원의 사용 여부를 선택합니다.
1. **Docker 지원 사용** 확인란을 선택합니다.
1. **Linux** 컨테이너 형식을 선택하고 **만들기**를 클릭합니다. Windows 컨테이너는 Azure App Service에 컨테이너로 배포할 수 없습니다.
::: moniker-end

## <a name="deploy-the-container-to-azure"></a>Azure에 컨테이너 배포

1. **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **게시**를 선택합니다.
1. 게시 대상 대화 상자에서 **App Service Linux**를 선택합니다.
1. App Service에만 게시하거나, App Service와 ACR(Azure Container Registry)에 모두 게시할 수 있습니다. ACR(Azure Container Registry)에 컨테이너를 게시하려면 **컨테이너에 대한 새 App Service 만들기**를 선택하고 **게시**를 클릭합니다.

   ![게시 대화 상자 스크린샷](media/deploy-app-service/publish-app-service-linux.PNG)

   Azure Container Registry를 사용하지 않고 Azure App Service에만 게시하려면 **새로 만들기**를 선택하고 **게시**를 클릭합니다.

1. Azure 구독과 연결된 계정으로 로그인했는지 확인하고 고유 이름, 구독, 리소스 그룹, 호스팅 계획 및 컨테이너 레지스트리(해당하는 경우)를 선택하거나 기본값을 적용합니다.

   ![게시 설정 스크린샷](media/deploy-app-service/publish-app-service-linux2.png)

1. **만들기**를 선택합니다. 컨테이너는 Azure의 선택한 리소스 그룹 및 컨테이너 레지스트리에 배포됩니다. 이 프로세스는 시간이 걸립니다. 작업이 완료되면, **게시** 탭에 사이트 URL을 포함하여 게시된 항목에 대한 정보가 표시됩니다.

   ![게시 탭 스크린샷](media/deploy-app-service/publish-succeeded.PNG)

1. 사이트 링크를 클릭하여 Azure에서 앱이 예상대로 작동하는지 확인합니다.

   ![웹 애플리케이션 스크린샷](media/deploy-app-service/web-application-running.png)

1. 리소스 그룹 및 컨테이너 레지스트리와 같은 선택한 모든 세부 정보와 함께 게시 프로필이 저장됩니다.
1. 동일한 게시 프로필을 사용하여 다시 배포하려면 **게시** 단추 또는 **웹 게시 작업** 창의 **게시** 단추를 사용하거나, **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 상황에 맞는 메뉴에서 **게시** 항목을 선택합니다.

## <a name="clean-up-resources"></a>리소스 정리

이 자습서와 관련된 Azure 리소스를 모두 제거하려면 [Azure Portal](https://portal.azure.com)을 사용하여 해당 리소스 그룹을 삭제합니다. 게시된 웹 애플리케이션과 관련된 리소스 그룹을 찾으려면 **보기** > **다른 창** > **웹 게시 작업**을 선택한 다음, 기어 아이콘을 선택합니다. 리소스 그룹이 포함된 **게시** 탭이 열립니다.

Azure Portal에서 **리소스 그룹**을 선택한 다음, 리소스 그룹을 선택하여 세부 정보 페이지를 엽니다. 올바른 리소스 그룹인지 확인하고 **리소스 그룹 제거**를 선택한 다음, 이름을 입력하고 **삭제**를 선택합니다.

## <a name="next-steps"></a>다음 단계

[Azure Pipelines](/azure/devops/pipelines/?view=azure-devops)를 사용하여 CI/CD(연속 통합 및 지속적인 업데이트)를 설정합니다.

## <a name="see-also"></a>참고 항목

[Azure Container Registry에 배포](hosting-web-apps-in-docker.md)