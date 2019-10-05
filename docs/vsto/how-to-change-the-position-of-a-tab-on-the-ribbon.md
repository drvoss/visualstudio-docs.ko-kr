---
title: '방법: 리본의 탭 위치 변경'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 512dfda8c95ecd56fe44eb6878e6abc0d942a782
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62826734"
---
# <a name="how-to-change-the-position-of-a-tab-on-the-ribbon"></a>방법: 리본의 탭 위치 변경
  사용 하 여 리본 메뉴의 사용자 지정 탭 순서를 변경할 수는 **탭 컬렉션 편집기**합니다. 리본의 기본 제공 탭 앞 이나 뒤에 사용자 지정 탭을 배치할 수 있습니다. 기본 제공 탭은 Microsoft Office 응용 프로그램의 리본 메뉴에 이미 있는 탭입니다. 예를 들어 합니다 **데이터** 탭은 Excel에서 기본 제공 탭 합니다.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-change-the-order-of-tabs-on-the-ribbon"></a>리본 메뉴의 탭 순서를 변경 하려면

1. 리본 코드 파일을 선택 (*.vb* 하거나 *.cs* 파일)에서 **솔루션 탐색기**합니다.

2. 에 **뷰** 메뉴에서 클릭 **디자이너**합니다.

3. 리본 디자이너를 마우스 오른쪽 단추로 누른 **속성**합니다.

4. 에 **속성** 창에서 합니다 **탭** 속성을 다음 줄임표 단추를 클릭 하 고 (![ASP.NET 모바일 디자이너 줄임표](../sharepoint/media/mwellipsis.gif "ASP.NET 모바일 디자이너 줄임표")).

     합니다 **탭 컬렉션 편집기** 나타납니다.

5. 에 **탭 컬렉션 편집기**를 **멤버** 목록에서 이동 하 고 화살표를 클릭 하거나 아래쪽 화살표를 탭 순서를 변경 하려면 탭을 선택 합니다.

### <a name="to-position-a-tab-before-or-after-a-built-in-tab-on-the-ribbon"></a>리본의 기본 제공 탭 앞 이나 뒤에 탭 배치

1. 리본 디자이너에서 사용자 지정 탭을 선택 합니다.

2. 에 **속성** 창 확장를 **ControlId** 속성을 다음 되어 있는지 확인 값을 **ControlIdType** 속성 **사용자지정**.

3. 에 **속성** 창에서 확장을 **위치** 속성.

4. 설정 된 **PositionType** 속성을 적절 한 값:

    - **BeforeOfficeId** 지정된 된 기본 제공 탭 앞에 그룹을 배치 합니다.

    - **AfterOfficeId** 후 지정된 된 기본 제공 탭에 그룹을 배치 합니다.

5. 설정 된 **OfficeId** 속성을 기본 제공 탭의 컨트롤 ID입니다.

     컨트롤 Id의 목록을 참조 하세요. [Office 2010 도움말 파일: Office fluent 사용자 인터페이스 제어 식별자](http://go.microsoft.com/fwlink/?LinkID=181052)합니다.

## <a name="see-also"></a>참고자료
- [리본 개요](../vsto/ribbon-overview.md)
- [리본 디자이너](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [연습: 리본 디자이너를 사용 하 여 사용자 지정 탭 만들기](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [연습: 리본 XML을 사용 하 여 사용자 지정 탭 만들기](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
