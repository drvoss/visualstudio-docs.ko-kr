---
title: 저장소 뷰어를 사용 하 여 디버깅 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, store viewer
- Domain-Specific Language, store
ms.assetid: 0178db2e-ae99-4ed3-9b87-8620fa9fa8e4
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a870c66b1c14dc6ddf3e38fb6e5be8c116be3573
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654885"
---
# <a name="debugging-by-using-the-store-viewer"></a>저장소 뷰어를 사용하여 디버깅
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

저장소 뷰어를 사용 하 여 [!INCLUDE[dsl](../includes/dsl-md.md)]에서 사용 하는 *저장소* 의 상태를 검사할 수 있습니다. 저장소 뷰어에는 요소 속성과 요소 간의 링크와 함께 특정 저장소에 있는 모든 도메인 모델 요소가 표시 됩니다.

## <a name="opening-store-viewer"></a>저장소 뷰어 열기
 @No__t_0 실험적 빌드에 있으면 저장소의 인스턴스에 모델 정보가 포함 된 중단점에서 코드를 중지 합니다. 그런 다음 **직접 실행** 창에서 다음 명령을 입력 하 여 저장소 뷰어를 엽니다.

```
Microsoft.VisualStudio.Modeling.Diagnostics.StoreViewer.Show(mystore);
```

> [!NOTE]
> @No__t_0을 저장소 인스턴스의 이름으로 바꾸어야 합니다. 또한 코드에 네임 스페이스를 추가 하는 경우 정규화 된 네임 스페이스 없이 저장소 뷰어를 표시 하는 명령을 입력할 수 있습니다.
>
> `using Microsoft.VisualStudio.Modeling.Diagnostics;`
>
> `…`
>
> `StoreViewer.Show(mystore);`

 @No__t_0 메서드에는 여러 오버 로드가 있습니다. 저장소나 파티션의 인스턴스를 매개 변수로 지정할 수 있습니다.

 또는 `Show` 메서드에 전달 하는 매개 변수가 범위 내에 있는 코드에서 저장소 뷰어를 표시 하는 코드 줄을 배치할 수 있습니다. 이 작업은 코드 줄이 저장소 콘텐츠의 스냅숏으로 실행 될 때 저장소 뷰어를 표시 합니다.

### <a name="using-store-viewer"></a>저장소 뷰어 사용
 저장소 뷰어가 열리면 다음 그림에 표시 된 것 처럼 모덜리스 Windows Forms 창이 표시 됩니다.

 ![](../modeling/media/storeviewer2.png "storeviewer2")저장소 뷰어

 저장소 뷰어에는 왼쪽 창, 오른쪽 위 창, 오른쪽 아래 창의 세 가지 창이 있습니다. 왼쪽 창은 저장소의 `DomainDataDirectory` 멤버에 있는 형식의 트리 뷰입니다. 파티션 노드를 확장 하 고 요소를 클릭 하면 오른쪽 위의 창에 요소의 속성이 표시 됩니다. 요소가 다른 요소에 연결 된 경우에는 오른쪽 아래 창에 추가 요소가 표시 됩니다. 오른쪽 아래 창에서 요소를 두 번 클릭 하면 왼쪽 창에 요소가 강조 표시 됩니다.

## <a name="see-also"></a>관련 항목:
 [프로그램 코드에서 모델 탐색 및 업데이트](../modeling/navigating-and-updating-a-model-in-program-code.md)
