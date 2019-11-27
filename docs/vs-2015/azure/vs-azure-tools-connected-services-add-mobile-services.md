---
title: 연결된 서비스를 사용 하 여 Mobile Services 추가
description: Visual Studio 연결된 서비스 추가 대화 상자를 사용 하 여 Mobile Services 추가
documentationcenter: na
author: ghogen
manager: jillfra
ms.assetid: 75c3cb93-88e1-476d-a416-f34caa3608e3
ms.topic: conceptual
ms.workload: azure-vs
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.date: 12/16/2015
ms.author: mlearned
ms.openlocfilehash: 4f84970daea03904d4642317cf6097beb07be7f1
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300186"
---
# <a name="adding-mobile-services-by-using-visual-studio-connected-services"></a>Visual Studio를 사용 하 여 Mobile Services 추가 연결된 서비스
Visual Studio 2015에서는 **연결 된 서비스 추가** 대화 상자를 사용 하 여 Azure Mobile Services에 연결할 수 있습니다. 모든 C# 클라이언트 앱, JavaScript 앱 또는 크로스 플랫폼 Cordova 앱에서 연결할 수 있습니다. 연결한 후에는 데이터를 만들고 액세스 하 고, 사용자 지정 Api 및 예약 된 작업을 만들거나, 푸시 알림에 대 한 지원을 추가할 수 있습니다.  연결 된 서비스 작업은 적절 한 모든 참조와 연결 코드를 추가 합니다. Azure AD, Facebook, Twitter, Microsoft 계정 등 널리 사용 되는 다양 한 id 스키마를 사용 하 여 인증에 대 한 기본 제공 지원을 활용할 수도 있습니다.

## <a name="supported-project-types"></a>지원 되는 프로젝트 형식
> [!NOTE]
> Visual Studio 2015에서 연결된 서비스 추가 대화 상자를 사용 하 여 Windows 유니버설 (Windows 10) 프로젝트에 Azure Mobile Services를 추가 하는 것은 지원 되지 않습니다. 프로젝트에 대 한 NuGet 패키지 관리자를 사용 하 여 적절 한 패키지를 설치 하 여 Azure Mobile Services를 추가할 수 있습니다.
>
>

연결된 서비스 대화 상자를 사용 하 여 다음 프로젝트 형식으로 Azure Mobile Services에 연결할 수 있습니다.

* .NET Windows 8.1 매장, 휴대폰 및 유니버설 앱 프로젝트
* JavaScript Windows 8.1 매장, 휴대폰 및 유니버설 앱 프로젝트
* Apache Cordova에 대해 Visual Studio Tools를 사용 하 여 만든 프로젝트

## <a name="connect-to-azure-mobile-services-using-the-add-connected-services-dialog"></a>연결된 서비스 추가 대화 상자를 사용 하 여 Azure Mobile Services에 연결
1. Azure 계정이 있는지 확인 합니다. Azure 계정이 없으면 [무료 평가판](https://go.microsoft.com/fwlink/?LinkId=518146)에 등록할 수 있습니다.
2. **연결된 서비스 추가** 대화 상자를 엽니다.

   * .NET 앱의 경우 Visual Studio에서 프로젝트를 열고 솔루션 탐색기의 **참조** 노드에 대 한 상황에 맞는 메뉴를 연 다음 **연결 된 서비스 추가** 를 선택 합니다.

        ![Azure 모바일 서비스에 연결](./media/vs-azure-tools-connected-services-add-mobile-services/IC797635.png)
   * Apache Cordova 앱 프로젝트의 경우 Visual Studio에서 프로젝트를 열고 솔루션 탐색기에서 프로젝트 노드에 대 한 상황에 맞는 메뉴를 연 다음 **연결 된 서비스 추가**를 선택 합니다.
3. **Connected Service 추가** 대화 상자에서 **Azure Mobile Services**를 선택한 다음, **구성** 단추를 선택합니다. 아직 수행 하지 않은 경우 Azure에 로그인 하 라는 메시지가 표시 될 수 있습니다.

    ![Azure 모바일 서비스 추가](./media/vs-azure-tools-connected-services-add-mobile-services/IC797636.png)
4. **Azure Mobile Services** 대화 상자에서 기존 모바일 서비스(있는 경우)를 선택합니다. 새 Azure 모바일 서비스를 만들어야 하는 경우 다음 절차에 따라 작업을 수행 합니다. 그렇지 않은 경우 다음 단계로 건너뜁니다.

    새 모바일 서비스 계정을 만들려면 다음을 수행 합니다.

   1. 대화 상자의 아래쪽에서 **서비스 만들기** 링크를 선택합니다.
       새 모바일 연결 서비스를 추가 ![](./media/vs-azure-tools-connected-services-add-mobile-services/IC797637.png)
   2. **모바일 서비스 만들기** 대화 상자의 **런타임** 드롭다운 목록에서 JavaScript 백 엔드 모바일 서비스 또는 .net 백 엔드 모바일 서비스를 선택할 수 있습니다.

       ![모바일 서비스 만들기](./media/vs-azure-tools-connected-services-add-mobile-services/IC797638.png)

       JavaScript 백 엔드 서비스는 간단 하 고 강력한 기능입니다. JavaScript 백 엔드 모바일 서비스를 만드는 경우 서버 쪽 JavaScript 코드가 클라우드에 저장되지만 서버 탐색기 또는 Azure 관리 포털을 사용하여 서버 스크립트를 편집할 수 있습니다.

       .NET 백 엔드 모바일 서비스는 Web API 및 Entity Framework의 전체 기능과 유연성을 제공 합니다. .NET 백 엔드 모바일 서비스를 만드는 경우 프로젝트가 만들어지고 솔루션에 추가 됩니다.
   3. 모바일 서비스를 원하는 **지역**을 선택한 다음 서버의 사용자 이름 및 암호를 입력합니다.
   4. 필요한 모든 정보를 입력한 후 **만들기** 단추를 선택하여 모바일 서비스를 만듭니다.
   5. 새 모바일 서비스가 **Azure Mobile Services** 대화 상자의 서비스 목록에 표시 됩니다. 목록에서 새 모바일 서비스를 선택한 다음, **추가** 단추를 선택하여 프로젝트에 서비스를 추가합니다.
5. 표시 되는 시작 페이지를 검토 하 고 프로젝트를 수정 하는 방법을 확인 합니다. 시작 페이지는 연결된 서비스를 추가할 때마다 브라우저에 나타납니다. 권장되는 다음 단계 및 코드 예제를 검토하거나, 발생하는 결과 페이지로 전환하여 프로젝트에 추가된 참조와 코드 및 구성 파일의 수정 내용을 확인할 수 있습니다.
6. 코드 샘플을 가이드로 사용 하 여 모바일 서비스에 액세스 하는 코드 작성을 시작 합니다.

## <a name="how-your-project-is-modified"></a>프로젝트를 수정하는 방법
Visual Studio에서 프로젝트를 수정 하는 방법은 프로젝트 형식에 따라 달라 집니다. 클라이언트 C# 앱의 경우 발생 하는 [상황 C# – 프로젝트](https://go.microsoft.com/fwlink/p/?LinkId=513119)를 참조 하세요. JavaScript 클라이언트 앱의 경우 발생 하는 [결과 – javascript 프로젝트](https://go.microsoft.com/fwlink/p/?LinkId=513120)를 참조 하세요. Cordova 앱의 경우 발생 하는 [결과 – cordova 프로젝트](https://go.microsoft.com/fwlink/p/?LinkId=513116)를 참조 하세요.

## <a name="next-steps"></a>다음 단계
질문을 하 고 도움을 받으세요.

* [MSDN 포럼: Azure Mobile Services](https://social.msdn.microsoft.com/forums/azure/home?forum=azuremobile)
* [Microsoft Azure 팀 블로그의 Azure Mobile Services](https://azure.microsoft.com/blog/topics/mobile/)
* [Azure.microsoft.com의 Azure Mobile Services](https://azure.microsoft.com/services/mobile-services/)
* [Azure.microsoft.com의 Azure Mobile Services 설명서](https://azure.microsoft.com/documentation/services/mobile-services/)
