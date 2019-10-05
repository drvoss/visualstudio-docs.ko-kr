---
title: '방법: 인수 디자이너 사용 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a244379bfebcf58d76ba726d4f6a84bcdfa7d1df
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696269"
---
# <a name="how-to-use-the-argument-designer"></a>방법: 인수 디자이너 사용
이전 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 버전과 비교할 때 인수 디자이너에서 데이터를 활동에서/으로 전달하기가 쉬워졌습니다. 클릭 하 여 디자이너에 액세스할 합니다 **인수** 디자인 캔버스의 왼쪽 아래 모서리에 있는 단추입니다. 디자이너를 정렬할 수 있습니다 각 열 머리글을 제외 하 고 있고 테이블 형식에서으로 표시 되는 인수의 목록을 포함 합니다 **기본값** 열입니다. 각 인수에는 이름, in/out/in-out/속성 방향, 형식 및 기본 식 값(있는 경우)이 포함됩니다. 이름 및 기본 식 값은 편집할 수 있는 텍스트 필드이며, 형식과 방향은 드롭다운입니다. [!INCLUDE[crabout](../includes/crabout-md.md)] 인수를 참조 하세요 [변수 및 인수](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8)합니다.  
  
### <a name="to-create-a-new-argument"></a>새 인수를 만들려면  
  
1. [!INCLUDE[vs2010](../includes/vs2010-md.md)]에서 워크플로 또는 활동 솔루션을 엽니다.  
  
2. 클릭 하 여 인수 디자이너를 엽니다는 **인수** 디자인 캔버스의 왼쪽 아래 모서리에 있는 단추입니다. 인수 디자이너가 나타납니다.  
  
3. 라는 빈 행을 클릭 **만드는 인수**합니다. 이 다음과 같은 기본값을 사용 하 여 새 인수를 사용 하 여 새 행이 추가 됩니다: argumentx에 대 한 합니다 **이름을** 여기서 x는 고유한 인수 이름을 만들기 위해 자동으로 증가 하는 1의 초기 값을 사용 하는 정수 **에서**  에 대 한 합니다 **방향**, 및 **문자열** 에 대 한 합니다 **인수 형식**합니다. 값에 대 한 항목이 **기본값**합니다. 워크플로 디자인 프로세스 중 언제라도 이러한 값을 변경할 수 있습니다.  
  
    > [!NOTE]
    > 인수를 삭제 하려면 클릭 하 여 인수를 선택 하 고 다음 키를 누릅니다 합니다 **삭제** 키입니다.  
  
## <a name="see-also"></a>참고 항목  
 [워크플로 디자이너 사용](../workflow-designer/using-the-workflow-designer.md)   
 [변수 및 인수](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8)