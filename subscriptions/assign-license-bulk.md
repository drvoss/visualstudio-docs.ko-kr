---
title: 사용자 그룹에 Visual Studio 구독에 대한 라이선스 할당 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/24/2019
ms.topic: conceptual
description: 관리자가 여러 구독자에게 라이선스를 할당하는 방법을 알아봅니다.
ms.openlocfilehash: 7d54dcf3cf3e7fea7845a4e9a0053de4ba734ae9
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/29/2019
ms.locfileid: "68610523"
---
# <a name="assign-subscriptions-to-multiple-users"></a>여러 사용자에게 구독 할당
구독 관리 포털을 사용하면 한 번에 한 명 또는 여러 그룹에 사용자를 추가할 수 있습니다.  개별 사용자를 추가하려면 [단일 사용자 추가](assign-license.md)를 참조하세요.

## <a name="use-bulk-add-to-assign-subscriptions"></a>대량 추가를 사용하여 구독 할당
1. [https://manage.visualstudio.com](https://manage.visualstudio.com )에서 Visual Studio 구독 관리 포털에 로그인합니다.
2. 여러 구독자를 한 번에 추가하려면 **구독자 관리** 탭으로 이동합니다. 맨 위에 있는 리본에서 **대량 추가**를 클릭합니다.
   > [!div class="mx-imgBorder"]
   > ![여러 구독자 추가](media/add-multiple-subscribers.png)

2. 대량 추가는 Microsoft Excel 템플릿을 사용하여 구독자 정보를 업로드합니다. [여러 구독자 업로드] 대화 상자에서 **다운로드**를 클릭하여 템플릿을 다운로드합니다.
   > [!div class="mx-imgBorder"]
   > ![Excel 템플릿을 다운로드하여 여러 구독자 업로드](media/download-template-upload-subscribers.png)
   >
   > [!NOTE]
   > 항상 이 템플릿의 최신 버전을 다운로드합니다. 이전 버전을 사용하는 경우 대량 업로드가 실패할 수 있습니다.

3. Excel 스프레드시트에서 구독을 할당하려는 개인에 대한 정보로 필드를 채웁니다. (*참조*는 선택적 필드입니다.) 작업을 마친 후에 파일을 로컬로 저장합니다.

   원활한 업로드를 보장하기 위해 다음 모범 사례를 관찰합니다.

    - 양식 필드에 쉼표가 없는지 확인합니다.
    - 양식 필드 앞뒤의 공백을 제거합니다.
    - 두 부분으로 이루어진 사용자 이름에서 첫 번째 이름과 마지막 이름 사이에 여분의 공백이 포함되지 않아야 합니다(예: 사용자의 첫 번째 이름이 "Maggie May"와 같이 두 부분으로 이루어진 경우 시스템에서 여분의 공백을 제거하지 않으므로 "MaggieMay"로 입력해야 함).

4. Visual Studio 구독 관리 포털로 돌아갑니다. **여러 구독자 업로드** 대화 상자에서 **찾아보기**를 클릭합니다.
   > [!div class="mx-imgBorder"]
   > ![저장된 템플릿으로 이동하여 여러 구독자 업로드](media/bulk-add-browse-saved-template.png)

5. 저장한 Excel 파일로 이동한 다음, **확인**을 클릭합니다.
   > [!div class="mx-imgBorder"]
   > ![Excel 템플릿을 업로드하여 여러 구독자 업로드](media/bulk-upload-subscribers.png)

    업로드 진행률 대화 상자가 표시됩니다.

    템플릿에 오류가 있는 경우 업로드가 실패합니다. 그러면 템플릿을 수정하고 대량 업로드를 다시 시도할 수 있도록 오류 메시지가 표시됩니다.
   > [!div class="mx-imgBorder"]
   > ![여러 구독자 업로드에 실패한 경우 오류 메시지](media/bulk-add-template-failed.png)

    업로드가 성공적으로 완료되면 구독자 목록과 확인 메시지가 표시됩니다.
   > [!div class="mx-imgBorder"]
   > ![여러 구독자 업로드에 성공한 경우 확인 메시지](media/bulk-add-template-success.png)

## <a name="next-steps"></a>다음 단계
- 구독자를 한두 명 정도만 추가하시겠습니까?  [단일 사용자 추가](assign-license.md) 체크 아웃
- 기존 구독을 [편집](edit-license.md)하는 방법 알아보기
- 도움이 필요하십니까? [Visual Studio 관리 및 구독 지원](https://visualstudio.microsoft.com/support/support-overview-vs)에 문의하세요.
