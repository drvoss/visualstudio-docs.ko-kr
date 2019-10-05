---
title: Visual Studio 구독에 라이선스 할당 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/24/2019
ms.topic: conceptual
description: 관리자가 구독자에게 라이선스를 할당하는 방법을 알아봅니다.
ms.openlocfilehash: 8125c5cbad2ff44dabbf1b0c5014c313d75d2e71
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/29/2019
ms.locfileid: "68604728"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administration-portal"></a>Visual Studio 구독 관리 포털에서 라이선스 할당
Visual Studio 구독 관리자는 관리 포털을 사용하여 개별 사용자 또는 사용자 그룹에 구독을 할당할 수 있습니다.

사용자 그룹의 경우 한 번에 하나씩 구독을 할당하거나 [대량 추가](assign-license-bulk.md) 기능을 사용하여 구독자 목록 및 해당 구독 정보를 쉽고 빠르게 업로드할 수 있습니다.

## <a name="add-a-single-subscriber"></a>단일 구독자 추가
구독 혜택에 액세스할 수 있도록 새 사용자에게 Visual Studio 구독 라이선스를 할당하는 방법은 다음과 같습니다.

1. [관리 포털](https://manage.visualstudio.com)에 로그인합니다.
2. 단일 Visual Studio 구독자에게 라이선스를 할당하려면 테이블 위쪽에서 **추가**를 선택합니다.
   > [!div class="mx-imgBorder"]
   > ![단일 구독자 추가](media/add-single-subscriber.png)
3. 새 구독자에 대한 정보를 양식 필드에 입력합니다. 조직에서 Azure Active Directory를 사용하는 경우 **이름** 필드는 현재 디렉터리에 있는 사람을 찾는 검색 기능 역할을 하므로 검색 결과에서 올바른 사용자를 선택할 수 있습니다. 해당 사용자를 선택하면 로그인 전자 메일 및 알림 전자 메일이 자동으로 채워집니다.
   > [!div class="mx-imgBorder"]
   > ![구독자 세부 정보](_img/assign-license-add/subscriber-details.png)

    구독자가 [Visual Studio 구독 포털](https://my.visualstudio.com?wt.mc_id=o~msft~docs)에 로그인할 때 소프트웨어 다운로드에 액세스할 수 있도록 하려면 **다운로드 설정**에서 다운로드 토글을 사용하도록 설정된 상태로 둡니다. 다운로드를 사용하지 않도록 선택하면 사용자는 소프트웨어 다운로드에 액세스할 수 없지만 구독에 포함된 다른 모든 혜택에는 계속 액세스할 수 있습니다.
   > [!div class="mx-imgBorder"]
   > ![다운로드 액세스 권한](media/access-to-downloads.png)

       If you'd like to add your own reference notes to the subscription, you can do so in the **Add reference** section.
   > [!div class="mx-imgBorder"]
   > ![각 구독에 고유한 참조 정보 추가](media/add-subscriber-reference-notes.png)

    옵션 선택 및 구독자에 대한 데이터 입력을 완료한 경우 **구독자 추가** 플라이아웃 맨 아래에 **추가**를 선택합니다.
   > [!div class="mx-imgBorder"]
   > ![추가 단추 선택](media/add-button.png)

4. 구독자가 추가되면 새 구독자에게 추가 지침이 있는 할당 이메일을 자동으로 보냅니다. 구독자를 선택하고 위쪽 메뉴의 **다시 보내기** 단추를 클릭하여 할당 전자 메일을 다시 보낼 수 있습니다.

## <a name="next-steps"></a>다음 단계
- 추가할 사용자가 많은가요?  [여러 구독자](assign-license-bulk.md)에게 구독을 할당하는 방법을 알아보세요.
- 도움이 필요하십니까?  [Visual Studio 관리 및 구독 지원](https://visualstudio.microsoft.com/support/support-overview-vs)에 문의하세요.

