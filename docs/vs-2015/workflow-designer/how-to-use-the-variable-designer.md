---
title: '방법: 변수 디자이너를 사용 하 여 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.DesignTimeVariable.UI
ms.assetid: 0318dfb0-bf8f-4f92-9b86-ae4c1b2161ad
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9ebfcf53ce4d03f676930bd905baa0723c17e481
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697087"
---
# <a name="how-to-use-the-variable-designer"></a>방법: 변수 디자이너 사용
변수 디자이너는 데이터 바인딩 시나리오 및 조건문에 사용할 변수를 만드는 데 사용됩니다. 클릭 하 여 디자이너에 액세스할 합니다 **변수** 디자인 캔버스의 왼쪽 아래 모서리에 있는 단추입니다. 디자이너에 테이블 형식 폼에 표시 하 고 정렬할 수 있습니다 각 열 머리글을 제외 하 고 있는 변수 목록을 포함 합니다 **기본** 열입니다. 각 변수에는 이름, 변수 형식, 범위 및 기본값(있는 경우)이 포함됩니다. 이름 및 기본값은 편집 가능한 텍스트 필드이며 형식과 범위는 드롭다운입니다. 범위란 변수 디자이너를 호출할 때 선택한 활동입니다. 선택 항목의 범위 안에서 변수를 만들 수 없는 경우, 선택 항목과 가장 근접하면서 변수를 만들 수 있는 상위 활동 범위가 기본 범위로 사용됩니다. [!INCLUDE[crabout](../includes/crabout-md.md)] 변수를 참조 하세요 [변수 및 인수](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8)합니다.  
  
 정렬 순서는 사용자가 정렬 컨트롤 중 하나를 명시적으로 사용하거나, 변수 디자이너를 닫았다가 다시 열거나, 다른 변수를 만들어야 적용됩니다.  
  
### <a name="to-create-a-new-variable"></a>새 변수를 만들려면  
  
1. [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]에서 워크플로 또는 활동 솔루션을 엽니다.  
  
2. 디자인 캔버스의 워크플로에서 활동을 선택합니다.  
  
3. 클릭 하 여 변수 디자이너를 엽니다는 **변수** 디자인 캔버스의 왼쪽 아래 모서리에 있는 단추입니다. 변수 디자이너가 나타납니다.  
  
4. 라는 빈 행을 클릭 **변수 만들기**합니다. 이 기본값을 사용 하 여 새 변수를 사용 하 여 새 행이 추가 됩니다:에 대 한 variablex 합니다 **이름** 여기서 x는 고유한 변수 이름을 만들기 위해 자동으로 증가 하는 1의 초기 값을 사용 하는 정수  **문자열** 에 대 한 합니다 **변수 형식**, 및 **시퀀스** 에 대 한 합니다 **범위**합니다. 값에 대 한 항목이 **기본**입니다. 워크플로 디자인 프로세스 중 언제라도 이러한 값을 변경할 수 있습니다.  
  
    > [!NOTE]
    > 변수를 삭제 하려면 클릭 하 여 변수를 선택 하 고 다음 키를 누릅니다 합니다 **삭제** 키입니다.  
  
## <a name="see-also"></a>참고 항목  
 [워크플로 디자이너 사용](../workflow-designer/using-the-workflow-designer.md)   
 [변수 및 인수](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8)   
 [방법: 인수 디자이너 사용](../workflow-designer/how-to-use-the-argument-designer.md)