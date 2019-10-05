---
title: '방법: 활동 디자이너 라이브러리 만들기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 5b62e092-63b3-462d-9d77-fb112482f45d
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a51b4cdb67590b908bc406b78c04ddf0c5aa3e2f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694551"
---
# <a name="how-to-create-an-activity-designer-library"></a>방법: 활동 디자이너 라이브러리 만들기
사용자 지정 활동 디자이너를 사용하여 표준 또는 사용자 지정 활동을 위한 사용자 인터페이스를 만들 수 있습니다. 사용자 인터페이스의 복잡성을 조절하고 한 가지 활동에 대해 두 개 이상의 활동 디자이너를 만들 수 있습니다. 이 시나리오에서는 여러 대상에 맞게 조정한 디자이너를 만들 수 있습니다.  
  
### <a name="to-create-an-activity-designer-library"></a>활동 디자이너 라이브러리를 만들려면  
  
1. [!INCLUDE[vs2010](../includes/vs2010-md.md)]를 시작합니다.  
  
2. 에 **파일** 메뉴에서 **새로 만들기**를 선택한 후 **프로젝트...** 열려는 합니다 **새 프로젝트** 대화 상자.  
  
3. 에 **프로젝트 형식** 창 **워크플로** 에서 합니다 **Visual C#** 또는 **Visual Basic** 사용자 기본 설정에 따라 그룹화 언어입니다.  
  
4. 에 **템플릿을** 창 **활동 디자이너 라이브러리**합니다.  
  
5. 에 **이름을** 상자에서 쉽게 식별할 수 있도록 프로젝트에 대 한 설명이 포함 된 이름을 입력 합니다.  
  
6. 에 **위치** 상자에 프로젝트를 저장할 또는 클릭 하려는 디렉터리를 입력 합니다 **찾아보기** 이동 합니다.  
  
7. 에 **솔루션** 상자는 솔루션에 대 한 설명이 포함 된 이름을 입력 한 다음 클릭 **확인**합니다.  
  
    > [!NOTE]
    > 기존 솔루션에 워크플로 콘솔 응용 프로그램을 추가 하려는 경우에 솔루션을 엽니다 [!INCLUDE[vs2010](../includes/vs2010-md.md)]에서 솔루션을 마우스 오른쪽 단추로 클릭 **솔루션 탐색기**를 선택 하 고 **추가**, 다음 **새 프로젝트...** 열려는 합니다 **새 프로젝트** 대화 상자. 그런 다음 이 절차의 윗부분에 설명된 대로 진행합니다.  
  
8. 프로젝트 템플릿이 XAML로 활동 디자이너 정의를 만들고 코드 숨김 구현 파일을 소스 코드로 만듭니다. [!INCLUDE[wfd1](../includes/wfd1-md.md)]가 열리고 활동 디자이너의 캔버스가 표시됩니다.  
  
9. 끌기 [!INCLUDE[avalon1](../includes/avalon1-md.md)] 에서 제어 합니다 **도구 상자** 디자인 화면에 사용자 지정 활동 디자이너에서 사용 하 합니다.  사용자 지정 활동 디자이너를 구현 하는 방법의 예제를 참조 하세요. [방법: 사용자 지정 활동 디자이너를 만드는](https://msdn.microsoft.com/library/2f3aade6-facc-44ef-9657-a407ef8b9b31)합니다.  
  
    > [!WARNING]
    > 기본도 사용자 지정 활동에 대 한 사용자 지정 활동 디자이너를 사용할 수 [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)]활동입니다.  
  
## <a name="see-also"></a>참고 항목  
 [워크플로 프로젝트 만들기](../workflow-designer/creating-a-workflow-project.md)