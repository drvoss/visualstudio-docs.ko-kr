---
title: UML 모델링 프로젝트 및 다이어그램 만들기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.addnewdiagramdialog
- vs.teamarch.createnewmodelingprojectdialog
helpviewer_keywords:
- projects [Visual Studio ALM], modeling
- diagrams - modeling, modeling
- modeling diagrams
- projects, UML
- UML, deleting diagrams
- UML
- UML diagrams, adding
- UML, projects
- Visual Studio ALM, modeling projects
- modeling projects
- UML diagrams
- projects, modeling
ms.assetid: c178b04b-4fd2-4bed-97e3-d793dae8649c
caps.latest.revision: 50
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bc537e76e87e519019cfbb1c3f612eb0a4bd6181
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433369"
---
# <a name="create-uml-modeling-projects-and-diagrams"></a>UML 모델링 프로젝트 및 다이어그램 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML 모델링은 소프트웨어 시스템을 이해하고 토론하며 디자인하는 데 도움이 됩니다. Visual Studio는 가장 자주 사용되는 UML 다이어그램 중 5가지인 동작, 클래스, 구성 요소, 시퀀스 및 사용 사례에 대한 템플릿을 제공합니다. 또한 시스템 구조를 정의하는 데 도움이 되는 레이어 다이어그램을 만들 수 있습니다.  
  
 UML 모델링 다이어그램 및 레이어 다이어그램은 모델링 프로젝트 내에만 존재할 수 있습니다. 각 모델링 프로젝트에는 공유 UML 모델 및 여러 UML 다이어그램이 포함됩니다. 각 다이어그램은 모델의 부분 뷰입니다. UML 모델은 UML 다이어그램의 모든 요소를 포함하고 UML 모델 탐색기를 사용하여 볼 수 있습니다. 모델 및 다이어그램에 해당 관계에 대 한 자세한 내용은 [편집 UML 모델 및 다이어그램](../modeling/edit-uml-models-and-diagrams.md)합니다. 버전 제어에서 프로젝트를 모델링 하는 방법에 대 한 내용은 [버전 제어에서 모델 및 다이어그램 관리](../modeling/manage-models-and-diagrams-under-version-control.md) 고 [모델링 솔루션](../modeling/structure-your-modeling-solution.md)  
  
> [!NOTE]
> 프로그램 코드를 시각화하는 데 사용되는 다른 종류의 다이어그램인 .NET 클래스 다이어그램도 있습니다. 자세한 내용은 [보기 클래스와 형식 디자인 및](http://go.microsoft.com/fwlink/?LinkId=142231)합니다.  
  
## <a name="CreatingModelingDiagrams"></a> 모델링 프로젝트에서 다이어그램 만들기  
 이 기능을 지원하는 Visual Studio 버전을 확인하려면 [아키텍처 및 모델링 도구에 대한 버전 지원](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.  
  
#### <a name="to-create-a-diagram-and-add-it-to-a-project"></a>다이어그램을 만들고 프로젝트에 추가하려면  
  
1. 에 **아키텍처** 메뉴 선택 **새 UML 또는 레이어 다이어그램**합니다.  
  
2. 에 **새 다이어그램 추가** 대화 상자에서 원하는 모델링 다이어그램의 유형을 클릭 합니다.  
  
    ![새 다이어그램 대화 상자를 추가](../modeling/media/uml-adddiagram.png "UML_AddDiagram")  
  
3. 새 다이어그램의 이름을 입력합니다.  
  
4. 에 **모델링 프로젝트에 추가** 상자:  
  
   - 솔루션에 이미 있는 모델링 프로젝트를 선택한 다음 클릭 **확인**합니다.  
  
     \- 또는 -  
  
   1. 선택 **새 모델링 프로젝트를 만듭니다**를 클릭 하 고 **확인**합니다.  
  
   2. 에 **새 모델링 프로젝트 만들기** 대화 상자에서 이름 및 새 프로젝트에 대 한 위치를 입력 한 다음 **확인**합니다.  
  
        ![새 모델링 프로젝트 대화 상자를 만들](../modeling/media/uml-createmodel.png "UML_CreateModel")  
  
        솔루션이 열려 있으면 새 프로젝트가 솔루션에 추가됩니다. 열려 있는 솔루션이 없는 경우 새 솔루션의 이름을 입력할 수 있습니다.  
  
   모델링 프로젝트가 이미 있는 경우 다음 절차를 사용할 수도 있습니다.  
  
#### <a name="to-add-a-diagram-to-an-existing-modeling-project"></a>기존 모델링 프로젝트에 다이어그램을 추가하려면  
  
1. **솔루션 탐색기**, 클릭 모델링 프로젝트 노드.  
  
    > [!NOTE]
    > 모델링 프로젝트에 모델 정의 폴더가 **ModelDefinition**합니다.  
  
2. **프로젝트** 메뉴에서 **새 항목 추가**를 클릭합니다.  
  
3. 에 **새 항목 추가-**  *\<프로젝트 이름 >* 대화 상자의 **템플릿**, 모델링 클릭 다이어그램 형식, 예를 들어 **UML 구성 요소 다이어그램**합니다.  
  
4. 다이어그램의 이름을 입력 한 다음 클릭 **추가**합니다.  
  
     모델링 다이어그램이 열리고 모델링 프로젝트에 표시됩니다.  
  
    > [!CAUTION]
    > 기존 다이어그램 파일을 다른 모델링 프로젝트 또는 솔루션의 다른 위치에 추가 또는 복사하거나 끌어오지 않도록 합니다. 그렇게 하는 경우 요소가 복사된 다이어그램에서 사라지거나 다이어그램을 열 때 오류가 발생할 수 있습니다. 해당 다이어그램 파일이 만들어진 모델링 프로젝트에서 다이어그램 파일을 열어야 합니다. UML 다이어그램이 모델링 프로젝트에서 소유하는 모델의 뷰이기 때문입니다. 다이어그램 파일을 복사하려면 새 다이어그램을 만들고 소스 다이어그램에서 새 다이어그램으로 요소를 복사합니다. 자세한 내용은 [문제 해결 모델링 프로젝트 및 다이어그램](#TroubleshootingModelingProjects)합니다.  
  
#### <a name="to-create-a-blank-modeling-project"></a>빈 모델링 프로젝트를 만들려면  
  
1. **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트**를 클릭합니다.  
  
2. 에 **새 프로젝트** 대화 상자의 **설치 된 템플릿**, 클릭 **모델링 프로젝트**합니다.  
  
3. 가운데 창에서 클릭 **모델링 프로젝트**합니다.  
  
4. 프로젝트 이름과 위치를 지정 합니다 **이름** 하 고 **위치** 상자.  
  
5. 에 **솔루션** 상자에서 **솔루션에 추가** 이미 열려 있는; 솔루션에 새 프로젝트를 추가 하려면 또는 **새 솔루션 만들기** 열려 있는 솔루션을 추가 합니다 새 솔루션에 프로젝트입니다.  
  
## <a name="RemovingModelingDiagrams"></a> 프로젝트에서 모델링 다이어그램 제거  
 다이어그램을 영구적으로 삭제하거나 프로젝트에서 다이어그램을 일시적으로 제외한 후 복원할 수 있습니다.  
  
#### <a name="to-permanently-delete-a-diagram-from-a-project"></a>프로젝트에서 다이어그램을 영구적으로 삭제하려면  
  
- **솔루션 탐색기**다이어그램을 나타내는 주 파일을 마우스 오른쪽 단추로 클릭 하 고 클릭 **삭제**합니다.  
  
     다이어그램이 프로젝트 및 파일 시스템에서 제거됩니다. 다이어그램에 표시 되는 요소에서 제거 되지 않습니다 **UML 모델 탐색기**합니다.  
  
    > [!NOTE]
    > 각 다이어그램에는 종속 관계에 있는 두 개의 파일이 있습니다. 예를 들어 `CD1`이라는 구성 요소 다이어그램이 있는 경우 `CD1.componentdiagram`이라는 파일을 삭제하면 `CD1.componentdiagram.layout`라는 종속 파일도 자동으로 삭제됩니다.  
  
#### <a name="to-temporarily-exclude-a-diagram-from-a-project"></a>프로젝트에서 다이어그램을 일시적으로 제외하려면  
  
- **솔루션 탐색기**다이어그램 파일을 마우스 오른쪽 단추로 클릭 한 다음 클릭 **프로젝트에서 제외**합니다.  
  
     프로젝트에서 다이어그램이 제거됩니다. 그렇지만 다이어그램이 파일 시스템에서 제거되지는 않습니다.  
  
    > [!NOTE]
    > 다이어그램에 표시 되는 요소에서 제거 되지 않습니다 **UML 모델 탐색기**합니다.  
  
#### <a name="to-restore-a-temporarily-excluded-diagram-to-a-project"></a>일시적으로 제외된 다이어그램을 프로젝트로 복원하려면  
  
1. **솔루션 탐색기**, 클릭 모델링 프로젝트 노드.  
  
    > [!NOTE]
    > 모델링 프로젝트에 모델 정의 폴더가 **ModelDefinition**합니다.  
  
2. **프로젝트** 메뉴에서 **기존 항목 추가**를 클릭합니다.  
  
3. 에 **기존 항목 추가** 대화 상자에서 다이어그램 파일을 찾습니다 파일을 선택 하 고 클릭 **추가**합니다.  
  
     모델링 다이어그램이 열리고 모델링 프로젝트에 표시됩니다.  
  
    > [!NOTE]
    > 각 다이어그램에 해당하는 한 쌍의 파일이 파일 시스템에 있습니다. 확장명이 `.layout`인 파일은 선택하지 않습니다. 또한 Visual Studio에서는 여러 모델링 프로젝트에 기존 UML 다이어그램을 추가할 수 없습니다. 각 다이어그램 파일은 해당 파일이 만들어진 모델링 프로젝트 내에서 열어야 합니다. UML 다이어그램이 모델링 프로젝트에서 소유하는 모델의 뷰를 나타내기 때문입니다.  
  
## <a name="NonModelDiagrams"></a> 모델링 프로젝트 필요로 하지 않는 다이어그램  
 다음과 같은 종류의 다이어그램은 모델링 프로젝트에 속하지 않습니다.  
  
- 소스 코드의 뷰로 만들어진 클래스 다이어그램. UML 클래스 다이어그램과 관련이 없습니다. 자세한 내용은 [보기 클래스와 형식 디자인 및](../ide/designing-and-viewing-classes-and-types.md)합니다.  
  
- 코드 맵. [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md)을 참조하세요.  
  
- 도메인 관련 언어와 같이 UML 다이어그램 또는 레이어 다이어그램이 아닌 다이어그램.  
  
## <a name="TroubleshootingModelingProjects"></a> 모델링 프로젝트 및 다이어그램 문제 해결  
 다음 테이블에서는 모델링 프로젝트 또는 다이어그램에서 발생할 수 있는 문제와 이러한 문제를 해결하는 방법을 설명합니다.  
  
|**문제**|**원인**|**해결**|  
|---------------|----------------|--------------------|  
|모델링 프로젝트를 열거나 솔루션으로 로드할 수 없습니다.<br /><br /> 다음 메시지가 표시됩니다.<br /><br /> "솔루션의 프로젝트 중 하나 이상이 제대로 로드되지 않았습니다. 자세한 내용은 출력 창을 참조하세요."<br /><br /> 출력 창에는 다음과 같은 메시지가 표시됩니다.<br /><br /> "*ModelingProjectFilenameAndPath*.modelproj: error: 인식할 수 없는 Guid 형식입니다. "|모델링 프로젝트에 이름과 위치가 같은 프로젝트에 대한 참조가 있습니다.<br /><br /> 예를 들어 레이어가 이름과 위치가 같은 프로젝트에 연결되어 있습니다.|텍스트 편집기를 사용하여 모델링 프로젝트 파일을 열고 참조를 제거한 다음 모델링 프로젝트를 다시 열어 봅니다.<br /><br /> 이 문제를 방지하려면 동일한 이름을 가진 프로젝트에 대한 참조를 추가하지 않도록 합니다. 프로젝트 이름이 고유한지 확인합니다.|  
|다른 모델링 프로젝트 또는 솔루션의 다른 위치로 추가 또는 복사하거나 끌어온 요소가 다이어그램에 없습니다.<br /><br /> 또는<br /><br /> 다이어그램을 열려고 할 때 다음 메시지가 표시됩니다.<br /><br /> -"일부 모양이 나 다이어그램에 연결선 되므로 누락이 프로젝트에 해당 정의가 존재 하지 않습니다. 다이어그램을 닫는 동안 모델에서 정의가 삭제되었거나 다이어그램이 해당 정의가 포함되지 않은 프로젝트로 복사되었습니다."<br /><br /> 또는<br /><br /> -"이이 문서는 다른 프로젝트에서 열려 있습니다."|다이어그램 파일을 모델링 프로젝트에서 다른 모델링 프로젝트로 또는 솔루션의 다른 위치로 추가하거나 복사하거나 끌어왔습니다.|다이어그램 파일을 복사하려면 새 다이어그램을 만들고 소스 다이어그램에서 새 다이어그램으로 요소를 복사합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [UML 모델 및 다이어그램 편집](../modeling/edit-uml-models-and-diagrams.md)   
 [모델링 솔루션 구성](../modeling/structure-your-modeling-solution.md)
