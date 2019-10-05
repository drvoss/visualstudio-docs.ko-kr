---
title: 연결 된 서비스를 사용 하 여 Mobile Services 추가
description: Visual Studio 연결 된 서비스 추가 대화 상자를 사용 하 여 Mobile Services 추가
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
ms.openlocfilehash: 4bfda342952820b4472a1f826273a7b9075faa9a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963987"
---
# <a name="adding-mobile-services-by-using-visual-studio-connected-services"></a>Visual Studio 연결 서비스를 사용 하 여 Mobile Services 추가
Visual Studio 2015를 사용 하 여 Azure Mobile Services를 사용 하 여 연결할 수는 **연결 된 서비스 추가** 대화 합니다. 연결할 수 있습니다 C# 클라이언트 앱, JavaScript 앱 또는 크로스 플랫폼 Cordova 앱. 에 연결 하면 있습니다 수 및 데이터에 액세스, 사용자 지정 Api 및 예약 된 작업을 만들거나 푸시 알림에 대 한 지원을 추가 합니다.  연결 된 서비스 작업에는 적절 한 참조와 연결 코드를 모두 추가합니다. 또한 다양 한 Azure AD와 같은 인기 있는 id 스키마로 인증용 기본 제공 지원 활용할 수 Facebook, Twitter 및 Microsoft 계정입니다.

## <a name="supported-project-types"></a>지원 되는 프로젝트 형식
> [!NOTE]
> Visual Studio 2015에서는 Windows Universal (Windows 10) 프로젝트에 연결 된 서비스 추가 대화 상자를 사용 하 여 Azure Mobile Services를 추가 지원 되지 않습니다. NuGet 패키지 관리자를 사용 하 여 프로젝트에 대 한 적절 한 패키지를 설치 하 여 Azure Mobile Services를 추가할 수 있습니다.
>
>

다음 프로젝트 형식에서 Azure Mobile Services에 연결할 연결 된 서비스 대화 상자를 사용할 수 있습니다.

* .NET Windows 8.1 Store, Phone 및 Universal 앱 프로젝트
* JavaScript Windows 8.1 Store, Phone 및 Universal 앱 프로젝트
* Apache Cordova 대 한 Visual Studio Tools를 사용 하 여 만든 프로젝트

## <a name="connect-to-azure-mobile-services-using-the-add-connected-services-dialog"></a>연결 된 서비스 추가 대화 상자를 사용 하 여 Azure Mobile Services에 연결
1. Azure 계정이 있는지 확인 합니다. Azure 계정이 없으면 있습니다 신청할 수는 [무료 평가판](http://go.microsoft.com/fwlink/?LinkId=518146)합니다.
2. 엽니다는 **연결 된 서비스 추가** 대화 상자.

   * .NET 앱에 대 한 Visual Studio에서 프로젝트를 열고, 상황에 맞는 메뉴를 열고 합니다 **참조** 솔루션 탐색기에서 노드를 선택한 후 **연결 된 서비스 추가**

        ![Azure 모바일 서비스에 연결](./media/vs-azure-tools-connected-services-add-mobile-services/IC797635.png)
   * Apache Cordova 앱 프로젝트에 대 한 Visual Studio에서 프로젝트를 열고, 솔루션 탐색기에서 프로젝트 노드에 대 한 상황에 맞는 메뉴를 열고 선택한 후 **연결 된 서비스 추가**합니다.
3. 에 **연결 된 서비스 추가** 대화 상자에서 **Azure Mobile Services**를 선택한 후는 **구성** 단추. 아직 수행 하지 않은 경우 Azure에 로그인 하 라는 메시지가 표시 될 수 있습니다.

    ![Azure 모바일 서비스를 추가합니다.](./media/vs-azure-tools-connected-services-add-mobile-services/IC797636.png)
4. 에 **Azure Mobile Services** 대화 상자에 있는 경우 기존 모바일 서비스를 선택 합니다. 새 Azure 모바일 서비스를 만들려는 경우 이렇게 하려면 다음 절차를 따르십시오. 그렇지 않은 경우 다음 단계로 건너뜁니다.

    새 모바일 서비스 계정을 만들려면:

   1. 선택 된 **서비스 만들기** 대화 상자의 맨 아래에 링크 합니다.
       ![새 모바일 연결 된 서비스 추가](./media/vs-azure-tools-connected-services-add-mobile-services/IC797637.png)
   2. 에 **모바일 서비스 만들기** 대화 상자에서 JavaScript 백 엔드 모바일 서비스 또는.NET 백 엔드 모바일 서비스에서 선택할 수 있습니다 합니다 **런타임** 드롭 다운 목록.

       ![모바일 서비스 만들기](./media/vs-azure-tools-connected-services-add-mobile-services/IC797638.png)

       JavaScript 백 엔드 서비스를 간단 하 고 강력한 됩니다. JavaScript 백 엔드 모바일 서비스를 만드는 경우 서버 쪽 JavaScript 코드가 클라우드에서 저장 되지만 서버 탐색기 또는 Azure 관리 포털을 사용 하 여 서버 스크립트를 편집할 수 있습니다.

       .NET 백 엔드 모바일 서비스의 모든 기능 및 Web API 및 Entity Framework의 유연성을 제공합니다. .NET 백 엔드 모바일 서비스를 만드는 경우 프로젝트를 생성 되어 솔루션에 추가 됩니다.
   3. 선택 된 **지역** 모바일 서비스를 선택 하 고 다음 서버에 대 한 사용자 이름 및 암호를 입력 합니다.
   4. 필요한 모든 정보를 입력 한 후 선택 합니다 **만들기** 단추 모바일 서비스를 만듭니다.
   5. 새 모바일 서비스의 서비스 목록에 표시 해야 합니다 **Azure Mobile Services** 대화 상자. 목록에서 새 모바일 서비스를 선택 하 고 선택 합니다 **추가** 프로젝트에 서비스를 추가 하려면 단추입니다.
5. 표시 되는 시작된 페이지를 검토 하 고 프로젝트를 수정 하는 방법을 알아봅니다. 연결된 된 서비스를 추가할 때마다 시작 페이지가 브라우저에 나타납니다. 다음 제안된 단계 및 코드 예제를 검토 하거나 프로젝트에 추가 된 참조 및 코드와 구성 파일 수정 된 방법을 보려면 내용 페이지로 전환 합니다.
6. 코드 샘플을 사용 하 여 가이드로, 모바일 서비스에 액세스 하는 코드를 작성 하는 작업을 시작!

## <a name="how-your-project-is-modified"></a>프로젝트를 수정하는 방법
Visual Studio에서 프로젝트를 수정 하는 방법 프로젝트 형식에 따라 달라 집니다. 에 대 한 C# 클라이언트 앱 [내용 – C# 프로젝트](http://go.microsoft.com/fwlink/p/?LinkId=513119)합니다. JavaScript 클라이언트 앱을 참조 하세요 [내용 – JavaScript 프로젝트](http://go.microsoft.com/fwlink/p/?LinkId=513120)합니다. Cordova 앱에 대 한 참조 [내용 – Cordova 프로젝트](http://go.microsoft.com/fwlink/p/?LinkId=513116)합니다.

## <a name="next-steps"></a>다음 단계
질문 하 고 도움 받기:

* [MSDN 포럼: Azure Mobile Services](https://social.msdn.microsoft.com/forums/azure/home?forum=azuremobile)
* [Microsoft Azure 팀 블로그의 azure Mobile Services](https://azure.microsoft.com/blog/topics/mobile/)
* [Azure.microsoft.com의 azure Mobile Services](https://azure.microsoft.com/services/mobile-services/)
* [Azure.microsoft.com에서 azure Mobile Services 설명서](https://azure.microsoft.com/documentation/services/mobile-services/)
