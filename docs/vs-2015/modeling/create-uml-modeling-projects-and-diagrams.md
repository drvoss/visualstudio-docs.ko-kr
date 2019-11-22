---
title: Create UML modeling projects and diagrams | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d5884dcd3f9e3cb8f1910d2e23ec80f910ed2fc9
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301006"
---
# <a name="create-uml-modeling-projects-and-diagrams"></a>UML 모델링 프로젝트 및 다이어그램 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML 모델링은 소프트웨어 시스템을 이해하고 토론하며 디자인하는 데 도움이 됩니다. Visual Studio는 가장 자주 사용되는 UML 다이어그램 중 5가지인 동작, 클래스, 구성 요소, 시퀀스 및 사용 사례에 대한 템플릿을 제공합니다. 또한 시스템 구조를 정의하는 데 도움이 되는 레이어 다이어그램을 만들 수 있습니다.

 UML 모델링 다이어그램 및 레이어 다이어그램은 모델링 프로젝트 내에만 존재할 수 있습니다. 각 모델링 프로젝트에는 공유 UML 모델 및 여러 UML 다이어그램이 포함됩니다. 각 다이어그램은 모델의 부분 뷰입니다. UML 모델은 UML 다이어그램의 모든 요소를 포함하고 UML 모델 탐색기를 사용하여 볼 수 있습니다. For information about models and their relationship to diagrams, see [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md). For information about modeling projects under version control, see [Manage models and diagrams under version control](../modeling/manage-models-and-diagrams-under-version-control.md) and [Structure your modeling solution](../modeling/structure-your-modeling-solution.md)

> [!NOTE]
> 프로그램 코드를 시각화하는 데 사용되는 다른 종류의 다이어그램인 .NET 클래스 다이어그램도 있습니다. For more information, see [Designing and Viewing Classes and Types](https://go.microsoft.com/fwlink/?LinkId=142231).

## <a name="CreatingModelingDiagrams"></a> Create a Diagram in a Modeling Project
 이 기능을 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.

#### <a name="to-create-a-diagram-and-add-it-to-a-project"></a>다이어그램을 만들고 프로젝트에 추가하려면

1. On the **Architecture** menu, choose **New UML or Layer Diagram**.

2. In the **Add New Diagram** dialog box, click the type of modeling diagram that you want.

    ![Add New Diagram dialog](../modeling/media/uml-adddiagram.png "UML_AddDiagram")

3. 새 다이어그램의 이름을 입력합니다.

4. In the **Add to modeling project** box:

   - Select a modeling project that already exists in your solution, and then click **OK**.

     \- 또는 -

   1. Select **Create a new modeling project**, and then click **OK**.

   2. In the **Create New Modeling Project** dialog box, type a name and location for the new project, and then click **OK**.

        ![Create New Modeling Project dialog](../modeling/media/uml-createmodel.png "UML_CreateModel")

        솔루션이 열려 있으면 새 프로젝트가 솔루션에 추가됩니다. 열려 있는 솔루션이 없는 경우 새 솔루션의 이름을 입력할 수 있습니다.

   모델링 프로젝트가 이미 있는 경우 다음 절차를 사용할 수도 있습니다.

#### <a name="to-add-a-diagram-to-an-existing-modeling-project"></a>기존 모델링 프로젝트에 다이어그램을 추가하려면

1. In **Solution Explorer**, click the modeling project node.

    > [!NOTE]
    > The modeling project contains a model definition folder named **ModelDefinition**.

2. **프로젝트** 메뉴에서 **새 항목 추가**를 클릭합니다.

3. In the **Add New Item -** *\<project name>* dialog box, under **Templates**, click the modeling diagram type, for example, **UML Component Diagram**.

4. Type a name for the diagram, and then click **Add**.

     모델링 다이어그램이 열리고 모델링 프로젝트에 표시됩니다.

    > [!CAUTION]
    > 기존 다이어그램 파일을 다른 모델링 프로젝트 또는 솔루션의 다른 위치에 추가 또는 복사하거나 끌어오지 않도록 합니다. 그렇게 하는 경우 요소가 복사된 다이어그램에서 사라지거나 다이어그램을 열 때 오류가 발생할 수 있습니다. 해당 다이어그램 파일이 만들어진 모델링 프로젝트에서 다이어그램 파일을 열어야 합니다. UML 다이어그램이 모델링 프로젝트에서 소유하는 모델의 뷰이기 때문입니다. 다이어그램 파일을 복사하려면 새 다이어그램을 만들고 소스 다이어그램에서 새 다이어그램으로 요소를 복사합니다. For more information, see [Troubleshooting Modeling Projects and Diagrams](#TroubleshootingModelingProjects).

#### <a name="to-create-a-blank-modeling-project"></a>빈 모델링 프로젝트를 만들려면

1. **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트**를 클릭합니다.

2. In the **New Project** dialog box, under **Installed Templates**, click **Modeling Projects**.

3. In the middle window, click **Modeling Project**.

4. Name the project and specify a location in the **Name** and **Location** boxes.

5. In the **Solution** box, select **Add to Solution** to add the new project to a solution you already have open; or **Create new Solution** to close any open solution and add the project to a new solution.

## <a name="RemovingModelingDiagrams"></a> Removing Modeling Diagrams from a Project
 다이어그램을 영구적으로 삭제하거나 프로젝트에서 다이어그램을 일시적으로 제외한 후 복원할 수 있습니다.

#### <a name="to-permanently-delete-a-diagram-from-a-project"></a>프로젝트에서 다이어그램을 영구적으로 삭제하려면

- In **Solution Explorer**, right-click the main file that represents the diagram, and then click **Delete**.

     다이어그램이 프로젝트 및 파일 시스템에서 제거됩니다. The elements shown on the diagram are not removed from **UML Model Explorer**.

    > [!NOTE]
    > 각 다이어그램에는 종속 관계에 있는 두 개의 파일이 있습니다. 예를 들어 `CD1`이라는 구성 요소 다이어그램이 있는 경우 `CD1.componentdiagram`이라는 파일을 삭제하면 `CD1.componentdiagram.layout`라는 종속 파일도 자동으로 삭제됩니다.

#### <a name="to-temporarily-exclude-a-diagram-from-a-project"></a>프로젝트에서 다이어그램을 일시적으로 제외하려면

- In **Solution Explorer**, right-click the diagram file, and then click **Exclude from Project**.

     프로젝트에서 다이어그램이 제거됩니다. 그렇지만 다이어그램이 파일 시스템에서 제거되지는 않습니다.

    > [!NOTE]
    > The elements shown on the diagram are not removed from **UML Model Explorer**.

#### <a name="to-restore-a-temporarily-excluded-diagram-to-a-project"></a>일시적으로 제외된 다이어그램을 프로젝트로 복원하려면

1. In **Solution Explorer**, click the modeling project node.

    > [!NOTE]
    > The modeling project contains a model definition folder named **ModelDefinition**.

2. On the **Project** menu, click **Add Existing Item**.

3. In the **Add Existing Item** dialog box, locate the diagram file, select the file, and then click **Add**.

     모델링 다이어그램이 열리고 모델링 프로젝트에 표시됩니다.

    > [!NOTE]
    > 각 다이어그램에 해당하는 한 쌍의 파일이 파일 시스템에 있습니다. 확장명이 `.layout`인 파일은 선택하지 않습니다. 또한 Visual Studio에서는 여러 모델링 프로젝트에 기존 UML 다이어그램을 추가할 수 없습니다. 각 다이어그램 파일은 해당 파일이 만들어진 모델링 프로젝트 내에서 열어야 합니다. UML 다이어그램이 모델링 프로젝트에서 소유하는 모델의 뷰를 나타내기 때문입니다.

## <a name="NonModelDiagrams"></a> Diagrams that Do Not Require Modeling Projects
 다음과 같은 종류의 다이어그램은 모델링 프로젝트에 속하지 않습니다.

- 소스 코드의 뷰로 만들어진 클래스 다이어그램. UML 클래스 다이어그램과 관련이 없습니다. For more information, see [Designing and Viewing Classes and Types](../ide/designing-and-viewing-classes-and-types.md).

- 코드 맵. [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md)을 참조하세요.

- 도메인 관련 언어와 같이 UML 다이어그램 또는 레이어 다이어그램이 아닌 다이어그램.

## <a name="TroubleshootingModelingProjects"></a> Troubleshooting Modeling Projects and Diagrams
 다음 테이블에서는 모델링 프로젝트 또는 다이어그램에서 발생할 수 있는 문제와 이러한 문제를 해결하는 방법을 설명합니다.

|**문제**|**Causes**|**해결**|
|---------------|----------------|--------------------|
|모델링 프로젝트를 열거나 솔루션으로 로드할 수 없습니다.<br /><br /> 다음 메시지가 표시됩니다.<br /><br /> "솔루션의 프로젝트 중 하나 이상이 제대로 로드되지 않았습니다. 자세한 내용은 출력 창을 참조하세요."<br /><br /> 출력 창에는 다음과 같은 메시지가 표시됩니다.<br /><br /> "*ModelingProjectFilenameAndPath*.modelproj: error: Unrecognized Guid format."|모델링 프로젝트에 이름과 위치가 같은 프로젝트에 대한 참조가 있습니다.<br /><br /> 예를 들어 레이어가 이름과 위치가 같은 프로젝트에 연결되어 있습니다.|텍스트 편집기를 사용하여 모델링 프로젝트 파일을 열고 참조를 제거한 다음 모델링 프로젝트를 다시 열어 봅니다.<br /><br /> 이 문제를 방지하려면 동일한 이름을 가진 프로젝트에 대한 참조를 추가하지 않도록 합니다. 프로젝트 이름이 고유한지 확인합니다.|
|다른 모델링 프로젝트 또는 솔루션의 다른 위치로 추가 또는 복사하거나 끌어온 요소가 다이어그램에 없습니다.<br /><br /> 또는<br /><br /> 다이어그램을 열려고 할 때 다음 메시지가 표시됩니다.<br /><br /> -   "Some shapes or connectors on the diagram are missing because their definitions do not exist in this project. 다이어그램을 닫는 동안 모델에서 정의가 삭제되었거나 다이어그램이 해당 정의가 포함되지 않은 프로젝트로 복사되었습니다."<br /><br /> 또는<br /><br /> -   "This document is opened by another project."|다이어그램 파일을 모델링 프로젝트에서 다른 모델링 프로젝트로 또는 솔루션의 다른 위치로 추가하거나 복사하거나 끌어왔습니다.|다이어그램 파일을 복사하려면 새 다이어그램을 만들고 소스 다이어그램에서 새 다이어그램으로 요소를 복사합니다.|

## <a name="see-also"></a>관련 항목:
 [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md) [Structure your modeling solution](../modeling/structure-your-modeling-solution.md)
