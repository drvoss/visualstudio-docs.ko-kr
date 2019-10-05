---
title: 관리자 포털에서 구독 편집 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/28/2019
ms.topic: conceptual
description: 관리자가 구독 할당을 편집하는 방법을 알아봅니다.
ms.openlocfilehash: e55cee74f861973e3cc29e3f19dc9b31a107f437
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/29/2019
ms.locfileid: "68605672"
---
# <a name="edit-visual-studio-subscription-assignments"></a>Visual Studio 구독 할당 편집
구독 관리자는 조직 내에서 개인에게 할당된 구독을 변경할 수 있습니다.  이 문서에서는 관리자가 변경할 수 있는 유형에 대해 설명하고 필요한 단계를 제공합니다.

## <a name="change-subscriber-information"></a>구독자 정보 변경
구독자 정보를 편집하여 오류를 수정하거나 정보를 업데이트할 수 있습니다.

구독자를 편집하려면 마우스로 위를 가리킬 때 구독자의 이메일 주소 옆에 나타나는 줄임표(...)를 선택합니다. 드롭다운이 표시됩니다.  **편집**을 선택하여 구독자 세부 정보를 수정합니다. 또한 그리드에서 구독자의 행을 두 번 클릭하여 편집 창을 열 수도 있습니다.
> [!div class="mx-imgBorder"]
> ![편집할 구독자 선택](_img/edit-license/select-subscriber.png)

구독자의 성, 이름, 국가, 언어 및 다운로드를 업데이트할 수 있습니다. 구독자 정보를 편집한 다음 **저장**을 클릭합니다.

   > [!NOTE]
   > 구독자의 구독 수준을 변경해야 하는 경우 포털에서 해당 사용자를 삭제하고 다시 추가해야 합니다. 구독 수준은 편집할 수 없습니다.

## <a name="edit-multiple-subscribers-using-bulk-edit"></a>대량 편집을 사용하여 여러 구독자 편집
대량 편집 프로세스를 사용하여 여러 구독자를 한 번에 수정할 수 있습니다. 이 기능은 주로 회사 이메일 주소 변경을 수행하는 조직에서 사용되거나 조직에서 다운로드에 대한 액세스를 제한하도록 결정한 경우에 사용됩니다.

   > [!IMPORTANT]
   > 구독 수준(예: Enterprise, Professional 등) 및 구독 GUID는 변경할 수 없습니다.  이러한 항목이 변경된 상태에서 업로드를 시도하면 업로드가 실패합니다.

1. 여러 구독자를 한 번에 수정하려면 [구독자] 탭으로 이동합니다. 맨 위에 있는 리본에서 **대량 편집**을 클릭합니다.

2. 대량 편집은 Excel 템플릿을 사용하여 구독자 정보를 편집합니다. [대량 편집] 상자에서 **이 Excel 내보내기**를 클릭하여 모든 정보가 포함된 현재 구독자 목록을 다운로드합니다.
   > [!div class="mx-imgBorder"]
   > ![라이선스 편집 - 대량 편집 목록 내보내기](_img/edit-license/edit-license-bulk-edit-export.png)

3. 다음으로 파일을 쉽게 찾을 수 있고 업로드하기 전에 필요한 변경을 수행할 수 있도록 해당 파일을 로컬로 저장합니다. 업로드를 성공적으로 수행하려면 **구독 수준 또는 구독 GUID**를 편집하지 마세요. 그렇지 않으면 업로드가 실패하게 됩니다.

4. Visual Studio 구독 관리 포털로 돌아가고, [대량 편집] 대화 상자에서 **찾아보기**를 클릭합니다. 저장한 Excel 파일을 선택하고 **확인**을 클릭합니다. 업로드 진행률이 화면에 표시됩니다.
   > [!div class="mx-imgBorder"]
   > ![라이선스 편집 - 대량 편집 파일 업로드](_img/edit-license/edit-license-bulk-file-upload1.png)

5. 파일이 업로드되면 성공했음을 알려주는 알림이 표시됩니다. 이 시점에서 편집한 내용이 구독자 정보에 반영됩니다.

## <a name="next-steps"></a>다음 단계
- 특정 구독을 찾는 데 도움이 필요하면 [구독 검색](search-license.md)을 체크 아웃하세요.
- 모든 구독 목록을 만들어야 하나요?  [구독 내보내기](exporting-subscriptions.md)를 체크 아웃하세요.