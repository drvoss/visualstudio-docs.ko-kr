---
title: Azure App Service에 게시
ms.custom: ''
ms.date: 06/22/2018
ms.technology: vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- azure
ms.openlocfilehash: a8de7175b33a91c310da4b3d6d9e4c05c40c3522
ms.sourcegitcommit: 4f82c178b1ac585dcf13b515cc2a9cb547d5f949
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/30/2018
ms.locfileid: "39341692"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a>Visual Studio를 사용하여 Azure App Service에 웹앱 게시

**게시** 도구를 사용하여 Azure App Service 또는 Azure App Service Linux에 ASP.NET, ASP.NET Core, Node.js 및 .NET Core 앱을 게시할 수 있습니다(컨테이너를 사용하여). Python 앱의 경우 [Python - Azure App Service에 게시](../python/publishing-python-web-applications-to-azure-from-visual-studio.md)의 단계를 따릅니다.

[!INCLUDE [quickstart-prereqs-azure](includes/quickstart-prereqs-azure.md)]

## <a name="publish-to-azure-app-service"></a>Azure App Service에 게시

1. 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **게시**를 선택합니다(또는 **빌드** > **게시** 메뉴 항목 사용).

    ![솔루션 탐색기의 프로젝트 바로 가기 메뉴에서 게시 명령](../deployment/media/quickstart-publish.png "게시 선택")

1. 게시 프로필을 이전에 구성한 경우 **게시** 창이 나타납니다. 이 경우 **새 프로필 만들기**를 선택합니다.

1. **게시 대상 선택** 대화 상자에서 **App Service**를 선택합니다.

    ![Azure App Service 선택](../deployment/media/quickstart-publish-azure.png "Azure App Service 선택")

1. **게시**를 선택합니다. **App Service 만들기** 대화 상자가 나타납니다. 필요한 경우 Azure 계정으로 로그인하면 기본 앱 서비스 설정에서 필드를 채웁니다.

    ![App Service 만들기](../deployment/media/quickstart-publish-settings-app-service.png "Azure App Service 만들기")

1. **만들기**를 선택합니다. Visual Studio는 Azure App Service에 앱을 배포하고, 브라우저에 웹앱이 로드됩니다. 프로젝트 속성 **게시** 창은 사이트 URL 및 기타 세부 정보를 표시합니다.

    ![프로필 요약을 표시하는 게시 속성 창](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>리소스 정리

이전 단계에서는 리소스 그룹에서 Azure 리소스를 만들었습니다. 나중에 이러한 리소스가 필요하지 않은 경우에 리소스 그룹을 삭제하여 삭제할 수 있습니다.
Azure Portal의 왼쪽 메뉴에서 **리소스 그룹**을 선택한 다음, **myResourceGroup**을 선택합니다.
리소스 그룹 페이지에서 나열된 리소스가 삭제하려는 항목인지 확인합니다.
**삭제**를 선택하고, 텍스트 상자에 **myResourceGroup**을 입력한 다음, **삭제**를 선택합니다.

## <a name="next-steps"></a>다음 단계

이 빠른 시작에서는 Visual Studio를 사용하여 Azure에 배포를 위해 게시 프로필을 만드는 방법을 알아보았습니다. Azure App Service에서 게시 설정을 가져와서 게시 프로필을 구성할 수도 있습니다.

> [!div class="nextstepaction"]
> [게시 설정 가져오기 및 Azure에 배포](tutorial-import-publish-settings-azure.md)
