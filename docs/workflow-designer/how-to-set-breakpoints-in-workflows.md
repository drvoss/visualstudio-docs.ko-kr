---
title: '워크플로 디자이너-방법: 워크플로에 중단점 설정'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7503d0b0bee201a9617e90966c9f75ac6333f228
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62949524"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>방법: 워크플로에 중단점 설정

워크플로 디자이너를 사용 하는 경우와 마찬가지로 Visual Basic 또는 C# 코드에서 그래픽 워크플로에 중단점을 설정할 수 있습니다. 예상대로 설정한 각 중단점에서 워크플로 실행이 중지됩니다.

중단점에는 세 가지 상태에 있습니다. *보류 중인*, *바인딩된*, 및 *오류*합니다. 새로 설정한 중단점은 보류 중 상태가 되고 단색의 빨간색 아이콘으로 표시됩니다. 런타임 시 워크플로 형식을 로드한 경우 중단점은 바인딩됨 상태가 됩니다. 유효하지 않은 활동 이름과 같이 중단점에 대해 잘못된 형식을 지정하면 오류 창이 나타납니다. 그래도 중단점 창에 중단점이 추가되기는 하지만 소문자 "x"로 표시됩니다.

> [!NOTE]
> 호출된 워크플로에는 중단점을 설정할 수 없습니다.

> [!NOTE]
> 옵션을 선택 했는지 확인 **내 코드만 사용 (관리 전용)** 에서 합니다 **도구** > **옵션** > **디버깅**  디버그 하기 전에 메뉴. 옵션을 선택 하지 않으면 두 시퀀스가 다른 시퀀스 내에 중첩 해야 하 고 첫 번째 내부 시퀀스에 중단점을 설정, 키를 눌러 **F11** 두 번째 내부 시퀀스는 디버깅 되지 않습니다.

> [!NOTE]
> XAML 파일 속성의 전체 경로 정확 하 게 없는 경우 워크플로의 중단점이 적중 되지 않습니다. 프로젝트 또는 솔루션을 다른 폴더 또는 다른 컴퓨터로 이동한 후 XAML 파일에 전체 경로가 정확 하 게 되었습니다. 선택 **Ctrl**+**S** 저장 하 고 전체 경로 속성을 업데이트 합니다.

## <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>디자인 뷰에서 활동의 중단점을 설정하려면

1. 디버거를 중단할 활동을 선택합니다.

2. 에 **디버그** 메뉴에서 **중단점 설정/해제**합니다. 활동의 왼쪽 위에 빨간색 아이콘이 표시됩니다.

   또는 눌러 수 있습니다 **F9** 활동 또는 사용자를 선택 하는 활동을 마우스 오른쪽 단추로 클릭 수 및 선택한 후 **중단점** > **중단점 삽입** 마우스 오른쪽 단추로 클릭 합니다.

## <a name="see-also"></a>참고자료

- [워크플로 디자이너로 워크플로 디버깅](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)
- [방법: 워크플로 디자이너로 XAML 디버그](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)