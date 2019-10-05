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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1a76cd9b726e534271937cb67a8d3f946d4eb477
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433192"
---
# <a name="debugging-by-using-the-store-viewer"></a>저장소 뷰어를 사용하여 디버깅
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

저장소 뷰어를 사용 하 여 상태를 검사할 수 있습니다는 *저장할* 에서 사용 하는 [!INCLUDE[dsl](../includes/dsl-md.md)]합니다. 저장소 뷰어를 모든 요소 속성 및 요소 간의 링크와 함께 특정 저장소에는 도메인 모델 요소를 표시 합니다.  
  
## <a name="opening-store-viewer"></a>저장소를 열지 뷰어  
 있는 경우는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 실험적 빌드, 인스턴스 저장소의 모델 정보를 포함 하는 위치에 중단점에서 코드를 중지 합니다. 그런 다음에 다음 명령을 입력 하 여 저장소 뷰어를 엽니다는 **직접 실행** 창:  
  
```  
Microsoft.VisualStudio.Modeling.Diagnostics.StoreViewer.Show(mystore);  
```  
  
> [!NOTE]
> 바꿔야 `mystore` 저장소 인스턴스의 이름입니다. 또한 코드에 네임 스페이스를 추가 하는 경우 정규화 된 네임 스페이스가 없는 저장소 뷰어를 표시 하는 것에 대 한 명령을 입력할 수 있습니다.  
>   
> `using Microsoft.VisualStudio.Modeling.Diagnostics;`  
>   
> `…`  
>   
> `StoreViewer.Show(mystore);`  
  
 `Show` 메서드에 몇 가지 오버 로드가 있습니다. 매개 변수로 파티션 또는 저장소의 인스턴스를 지정할 수 있습니다.  
  
 대신 코드에서 아무 곳 이나 저장소 뷰어를 표시 하는 코드 줄을 입력할 수 있습니다 위치에 전달 하는 매개 변수는 `Show` 메서드는 범위입니다. 이 작업 코드 줄에는 저장소의 콘텐츠를 스냅숏으로 실행 하는 경우 저장소 뷰어를 표시 합니다.  
  
### <a name="using-store-viewer"></a>저장소 뷰어를 사용 하 여  
 저장소 뷰어 열리고 다음 그림과 같이 모덜리스 Windows Forms 창이 나타납니다.  
  
 ![](../modeling/media/storeviewer2.png "storeviewer2")  
저장소 뷰어  
  
 저장소 뷰어는 세 가지 창인: 왼쪽 창과 오른쪽 창 오른쪽 아래 창입니다. 왼쪽된 창에서 형식의 트리 뷰입니다는 `DomainDataDirectory` 저장소의 멤버입니다. 파티션 노드를 확장 하 고 요소를 클릭 하면 오른쪽 창에서 요소의 속성이 나타납니다. 요소는 다른 요소에 연결 하는 경우 추가 요소가 오른쪽 아래 창에 나타납니다. 오른쪽 아래 창에서 요소를 두 번 클릭 하면 왼쪽된 창에서 요소 강조 표시 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [프로그램 코드에서 모델 탐색 및 업데이트](../modeling/navigating-and-updating-a-model-in-program-code.md)
