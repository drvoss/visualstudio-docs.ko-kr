---
title: '방법: Backstage 보기에 컨트롤 추가 '
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- customizing the Ribbon, menus
- controls, Ribbon
- menus, customizing
- Microsoft Office Button
- custom Ribbon, menus
- Ribbon, customizing
- Office button
- Ribbon, menus
- Microsoft Office Menu
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c4241464fe8a43af882fbdbad0f898838e8fd897
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62826784"
---
# <a name="how-to-add-controls-to-the-backstage-view"></a>방법: Backstage 보기에 컨트롤 추가
  리본 디자이너를 사용 하 여 컨트롤을 클릭할 때 열리는 메뉴에 추가 하는 **파일** 탭 합니다. 컨트롤에 추가한 응용 프로그램을 실행 하는 경우는 **파일** 라는 그룹 탭이 표시 **추가 기능**합니다.

 Visual Studio에서 리본 디자이너를 사용 하 여 기본 제공 컨트롤 전후 컨트롤을 배치할 수 없습니다. 기본 제공 컨트롤은 Backstage 뷰에 이미 표시 되는 컨트롤입니다. 기본 제공 컨트롤 전후 컨트롤을 배치 하려는 경우 리본 XML을 사용 해야 합니다. 에 대 한 자세한 내용은 **리본 (XML)** 를 참조 하십시오 [리본 XML](../vsto/ribbon-xml.md)합니다. Backstage 보기 사용자 지정 하는 방법에 대 한 자세한 내용은 참조 하세요. [개발자를 위한 Office 2010 Backstage 보기 소개](http://go.microsoft.com/fwlink/?LinkId=182189) 하 고 [개발자를 위한 Office 2010 Backstage 보기를 사용자 지정할](http://go.microsoft.com/fwlink/?LinkId=182188)합니다.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-controls-to-backstage-view"></a>Backstage 보기에 컨트롤을 추가 하려면

1. 디자인 뷰에서 리본 항목을 엽니다.

     추가 하는 방법에 대 한 자세한를 **리본 (비주얼 디자이너)** 프로젝트에 항목을 참조 하십시오 [방법: 리본 사용자 지정 시작](../vsto/how-to-get-started-customizing-the-ribbon.md)합니다.

2. 리본 디자이너를 클릭 합니다 **파일** 탭 합니다.

     메뉴 디자이너에 표시 됩니다. 이 디자인 화면에 컨트롤이 없습니다.

3. **Office 리본 컨트롤** 탭의 **도구 상자**, 메뉴 디자이너를 끌어 다음 컨트롤 중 하나:

    - 단추

    - CheckBox

    - 갤러리

    - 메뉴

    - 구분 기호

    - SplitButton

    - ToggleButton

4. 메뉴의 새 위치로 이동 하는 컨트롤을 끕니다.

## <a name="see-also"></a>참고자료
- [리본 개요](../vsto/ribbon-overview.md)
- [리본 디자이너](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [방법: 시작 리본을 사용자 지정](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [연습: 리본 디자이너를 사용 하 여 사용자 지정 탭 만들기](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
