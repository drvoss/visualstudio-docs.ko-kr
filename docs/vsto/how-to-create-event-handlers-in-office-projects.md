---
title: '방법: Office 프로젝트에서 이벤트 처리기 만들기'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Basic [Office development in Visual Studio], event handlers
- event handlers [Office development in Visual Studio]
- Visual C# [Office development in Visual Studio], event handlers
- events [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 537bae766b71744a61e5158b1a859cade4cdcda7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63419645"
---
# <a name="how-to-create-event-handlers-in-office-projects"></a>방법: Office 프로젝트에서 이벤트 처리기 만들기
  Visual Basic 및 C#에서 이벤트 처리기를 만드는 방법은 여러 가지가 있습니다. 디자인 뷰에서 컨트롤을 두 번 클릭 하 여 기본 컨트롤에 대 한 이벤트 처리기 만들기 또는 이벤트 창 수를 **속성** 창 컨트롤에서 모든 이벤트에 대 한 처리기를 만들려고 합니다. 그러나 코드 보기에 있는 경우 있습니다 하지 않을 이벤트 처리기를 만들 디자인 뷰로 전환 합니다.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-create-an-event-handler-in-visual-basic"></a>Visual Basic의 이벤트 처리기를 만들려면

1. **클래스 이름** 코드 편집기의 맨 위에 있는 드롭다운 목록에서 선택 하려는 개체에 대 한 이벤트 처리기를 만듭니다.

    > [!NOTE]
    > 에 대 한 이벤트 처리기를 만들려는 경우 `ThisDocument` 또는 `ThisWorkbook`를 선택 해야 **(ThisDocument 이벤트)** 또는 **(ThisWorkbook 이벤트)** 에 **클래스 이름**드롭 다운 목록

2. **메서드 이름** 드롭 다운 목록 맨 위에 있는 코드 편집기의 이벤트를 선택 합니다.

     Visual Studio 이벤트 처리기를 만들고 새로 만든된 이벤트 처리기에 삽입 지점을 이동 합니다. 이벤트 처리기가 이미 있으면 기존 이벤트 처리기에 삽입 지점을 이동 합니다.

### <a name="to-create-an-event-handler-in-c"></a>C에서 이벤트 처리기를 만들려면\#

1. 이벤트 대리자를 만듭니다는 **시작** 뒤에 공백, 정규화 된 이벤트 이름을 입력 하 고 입력 하 여 클래스의 이벤트 **+=** 나중에 공백 없이 합니다. 예를 들어:

     `this.<object name>.<event name> +=`

2. 코드 줄의 끝 TAB 키를 두 번 누릅니다.

     Visual Studio 자동으로 코드 줄을 완료, 이벤트 처리기를 만들고 새로 만든된 이벤트 처리기에 삽입 지점을 이동 합니다.

## <a name="see-also"></a>참고자료
- [Office 솔루션에서 코드를 작성 합니다.](../vsto/writing-code-in-office-solutions.md)
- [연습: NamedRange 컨트롤의 이벤트에 대 한 프로그램](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)
- [Office 솔루션 빌드](../vsto/building-office-solutions.md)
