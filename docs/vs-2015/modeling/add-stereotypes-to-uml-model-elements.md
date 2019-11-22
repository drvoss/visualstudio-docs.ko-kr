---
title: Add stereotypes to UML model elements | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, stereotypes
ms.assetid: 82545252-83ce-4e11-a419-61373be75d16
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 67d489b1446e7205d72b53e160a8c7ca87f216d7
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74292337"
---
# <a name="add-stereotypes-to-uml-model-elements"></a>UML 모델 요소에 스테레오타입 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML 모델 요소에 스테레오타입을 추가하여 주석을 지정하고 특수화된 속성을 제공할 수 있습니다. 모델 요소에 스테레오타입을 추가하려면 프로필에서 스테레오타입을 정의해야 하며 모델 요소를 포함하는 모델 또는 패키지에 프로필을 연결해야 합니다. UML 클래스, 사용 사례 또는 구성 요소와 같은 특정 종류의 모델 요소에만 각 스테레오타입을 추가할 수 있습니다.

 예를 들어 «specification» 스테레오타입으로 UML 클래스를 정의하려는 경우 표준 프로필 L2에 연결된 패키지 또는 모델 내에서 만들어야 합니다.

 기본적으로 모든 모델은 UML 표준 프로필 L2 및 L3에 연결됩니다.

### <a name="to-link-a-profile-to-a-model-or-a-package"></a>모델 또는 패키지에 프로필을 연결하려면

1. Open **UML Model Explorer**. On the **Architecture** menu, point to **Windows**, and then click **UML Model Explorer**.

2. 프로필의 스테레오타입을 적용할 모든 요소를 포함하는 패키지 또는 모델을 찾습니다.

3. Right-click the package or the model and then click **Properties**.

4. In the **Properties** window, set the **Profiles** property to the profiles that contain the stereotypes you want to use.

     이제 모델 또는 패키지 내의 모든 요소에서 프로필의 스테레오타입을 사용할 수 있습니다. 패키지에 다른 패키지가 포함된 경우 내부 요소에서도 스테레오타입을 사용할 수 있습니다.

### <a name="to-add-stereotypes-to-model-elements-or-relationships"></a>모델 요소 또는 관계에 스테레오타입을 추가하려면

1. Right-click the model element or relationship, either on a diagram or in **UML Model Explorer**, and then click **Properties**.

    > [!NOTE]
    > 여러 요소에 동일한 스테레오타입을 추가하려면 여러 요소를 선택하고 그중 하나를 마우스 오른쪽 단추로 클릭할 수 있습니다.

2. Click the **Stereotypes** property and select the stereotypes that you want to apply.

     대부분의 요소 및 관계 종류의 경우 선택한 스테레오타입이 모델 요소의 «펼침 단추» 내에 표시됩니다.

    > [!NOTE]
    > If you cannot see the **Stereotypes** property, or if the stereotype you want does not appear, verify that the model element is inside a package or a model to which the appropriate profile has been linked.

3. 일부 스테레오타입을 사용하면 모델 요소에 대한 추가 속성 값을 설정할 수 있습니다. To see these properties, expand the **Stereotypes** property.

### <a name="to-create-model-elements-within-a-package"></a>패키지 내에서 모델 요소를 만들려면

1. Create a package either in a UML Class Diagram, or in **UML Model Explorer**.

2. 다음 방법 중 하나로 패키지에 모델 요소를 추가합니다.

    - UML 클래스 다이어그램에서 요소에 대한 도구를 클릭한 다음 다이어그램에서 패키지 내부를 클릭합니다.

         \- 또는 -

    - In UML Model Explorer, right-click the package, point to **Add**, and then click an element type.

         \- 또는 -

    - UML 모델 탐색기에서 기존 요소를 패키지로 끌어옵니다.

         \- 또는 -

    - 다이어그램을 패키지에 연결하고 다이어그램 내에서 요소를 만듭니다.

         To do this, right-click a blank part of the diagram and then click **Properties**. In the **Properties** window, set **Linked Package** to the package you want.

         다이어그램에서 새로 만든 모든 요소는 해당 패키지 내에서 정의됩니다.

         일부 형식의 다이어그램에서만 이 작업을 수행할 수 있습니다.

## <a name="see-also"></a>관련 항목:
 [Define a profile to extend UML](../modeling/define-a-profile-to-extend-uml.md) [Customize your model with profiles and stereotypes](../modeling/customize-your-model-with-profiles-and-stereotypes.md) [Define packages and namespaces](../modeling/define-packages-and-namespaces.md)

