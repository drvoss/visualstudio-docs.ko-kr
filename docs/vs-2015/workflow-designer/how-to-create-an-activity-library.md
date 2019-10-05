---
title: '방법: 활동 라이브러리 만들기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 1eeebe74-7303-4345-8a83-fe37a26bc84b
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9463e46a7341a7da5c4aa79ae477d6aa0ff0c6cc
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686650"
---
# <a name="how-to-create-an-activity-library"></a>방법: 활동 라이브러리 만들기
사용자 지정 활동은 워크플로의 특정 비즈니스 프로세스를 모델링하는 데 사용됩니다. [!INCLUDE[vs2010](../includes/vs2010-md.md)]의 활동 라이브러리 템플릿은 [!INCLUDE[wfd1](../includes/wfd1-md.md)]를 사용하여 이러한 사용자 지정 활동을 시각적으로 만들 수 있도록 하기 위한 것입니다.  
  
### <a name="to-create-a-workflow-activity-library"></a>워크플로 활동 라이브러리를 만들려면  
  
1. [!INCLUDE[vs2010](../includes/vs2010-md.md)]를 시작합니다.  
  
2. 에 **파일** 메뉴에서 **새로 만들기**를 선택한 후 **프로젝트...** .  
  
     **새 프로젝트** 대화 상자가 열립니다.  
  
3. 에 **프로젝트 형식** 창 **워크플로** 에서 합니다 **Visual C#** 프로젝트 또는 **Visual Basic** 그룹화에 따라 프로그램 언어 기본 설정 합니다.  
  
4. 에 **템플릿을** 창 **활동 라이브러리**합니다.  
  
5. 에 **이름을** 상자에서 쉽게 식별할 수 있도록 프로젝트에 대 한 설명이 포함 된 이름 입력 합니다.  
  
6. 에 **위치** 상자에 프로젝트를 저장 하거나 클릭 하려는 디렉터리에 **찾아보기** 이동 합니다.  
  
7. 에 **솔루션** 상자는 솔루션에 대 한 설명이 포함 된 이름을 입력 한 다음 클릭 **확인**합니다.  
  
    > [!NOTE]
    > 기존 솔루션에 워크플로 콘솔 응용 프로그램을 추가 하려는 경우에 솔루션을 엽니다 [!INCLUDE[vs2010](../includes/vs2010-md.md)]에서 솔루션을 마우스 오른쪽 단추로 클릭 **솔루션 탐색기**를 선택 하 고 **추가**, 한 다음  **새 프로젝트...** 열려는 합니다 **새 프로젝트** 대화 상자. 그런 다음 이 절차의 윗부분에 설명된 대로 진행합니다.  
  
8. 프로젝트 템플릿이 활동 정의를 XAML로 만듭니다. [!INCLUDE[wfd1](../includes/wfd1-md.md)]가 열리고 사용자 지정 활동의 캔버스가 표시됩니다.  
  
9. 활동을 끌어 합니다 **도구 상자** 을 디자인 화면으로 사용자 지정 활동에 포함 합니다.  
  
    > [!CAUTION]
    > 사용자 지정 활동의 본문에 자식 활동을 한 개만 넣을 수 있지만, 자식 활동으로 <xref:System.Activities.Statements.Sequence> 활동 또는 <xref:System.Activities.Statements.Flowchart> 활동과 같은 복합 활동을 사용할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [방법: 활동 만들기](https://msdn.microsoft.com/library/c09b1e99-21b5-4d96-9c04-ec31db3f4436)   
 [워크플로 프로젝트 만들기](../workflow-designer/creating-a-workflow-project.md)