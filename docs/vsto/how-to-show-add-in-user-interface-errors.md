---
title: '방법: 추가 사용자 인터페이스 오류 표시'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], user interface errors
- errors [Office development in Visual Studio], user interface errors
- user interfaces [Office development in Visual Studio], errors
- application-level add-ins [Office development in Visual Studio], user interface errors
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 78cc4d2e85e2f7a5347fe0c8927c855160fbb511
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441783"
---
# <a name="how-to-show-add-in-user-interface-errors"></a>방법: 추가 사용자 인터페이스 오류 표시
  VSTO 추가 기능에 Microsoft Office 사용자 인터페이스 (UI) 및 실패를 조작 하려고 시도 하는 경우에 기본적으로 오류 메시지가 표시 됩니다. 그러나 UI에 관련된 오류에 대한 메시지를 표시하도록 Microsoft Office 애플리케이션을 구성할 수 있습니다. 이러한 메시지는 이유는 리본 나타나지만 컨트롤이 표시 또는 사용자 지정 리본을 표시 되지 않는 이유를 확인 하는 데 사용할 수 있습니다.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="to-show-vsto-add-in-user-interface-errors"></a>VSTO 추가 기능 사용자 인터페이스 오류를 표시하려면

1. 애플리케이션을 시작합니다.

2. **파일** 탭을 클릭합니다.

3. **옵션**을 클릭합니다.

4. 범주 창에서 **고급**을 클릭합니다.

5. 세부 정보 창에서 **VSTO 추가 기능 사용자 인터페이스 오류 표시**를 선택하고 **확인**을 클릭합니다.

    > [!NOTE]
    > Outlook의 경우 세부 정보 창의 **개발자** 섹션에 **VSTO 추가 기능 사용자 인터페이스 오류 표시** 확인란이 있습니다. 다른 애플리케이션의 경우 이 확인란은 세부 정보 창의 **일반** 섹션에 있습니다.

## <a name="see-also"></a>참고자료
- [Office UI 사용자 지정](../vsto/office-ui-customization.md)
- [Outlook 양식 영역 만들기](../vsto/creating-outlook-form-regions.md)
- [리본 개요](../vsto/ribbon-overview.md)
- [작업 창 개요](../vsto/actions-pane-overview.md)
