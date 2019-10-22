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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a436d33bbb7c791f3f192357fded779fa77d148d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659110"
---
# <a name="how-to-use-the-argument-designer"></a>방법: 인수 디자이너 사용
이전 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 버전과 비교할 때 인수 디자이너에서 데이터를 활동에서/으로 전달하기가 쉬워졌습니다. 디자인 캔버스의 왼쪽 아래 모퉁이에 있는 **인수** 단추를 클릭 하 여 디자이너에 액세스 합니다. 이 디자이너에는 테이블 형식으로 표시 되 고 각 열 머리글을 기준으로 정렬할 수 있는 인수 목록이 포함 되어 있습니다 ( **기본값** 열 제외). 각 인수에는 이름, in/out/in-out/속성 방향, 형식 및 기본 식 값(있는 경우)이 포함됩니다. 이름 및 기본 식 값은 편집할 수 있는 텍스트 필드이며, 형식과 방향은 드롭다운입니다. 인수 [!INCLUDE[crabout](../includes/crabout-md.md)] [변수 및 인수](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8)를 참조 하세요.

### <a name="to-create-a-new-argument"></a>새 인수를 만들려면

1. [!INCLUDE[vs2010](../includes/vs2010-md.md)]에서 워크플로 또는 활동 솔루션을 엽니다.

2. 디자인 캔버스의 왼쪽 아래 모퉁이에 있는 **인수** 단추를 클릭 하 여 인수 디자이너를 엽니다. 인수 디자이너가 나타납니다.

3. **인수 만들기**라는 빈 행을 클릭 합니다. 그러면 다음과 같은 **기본값을 사용** 하 여 새 인수를 사용 하는 새 행이 추가 됩니다. **여기서 x** 는 초기 값이 1 인 정수 이며, **방향**에 따라 고유한 인수 이름을 만들도록 자동으로 증가 합니다. **인수 형식**에 대 한 및 **문자열** 입니다. **기본값**에는 값이 추가 되지 않습니다. 워크플로 디자인 프로세스 중 언제라도 이러한 값을 변경할 수 있습니다.

    > [!NOTE]
    > 인수를 삭제 하려면 인수를 클릭 하 여 선택한 다음 **delete** 키를 누릅니다.

## <a name="see-also"></a>관련 항목:
 [워크플로 디자이너](../workflow-designer/using-the-workflow-designer.md) [변수 및 인수](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8) 사용