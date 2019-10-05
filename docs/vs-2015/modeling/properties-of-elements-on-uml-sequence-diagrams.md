---
title: 시퀀스 다이어그램에 UML 요소 속성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.sequencediagram.combinedfragment.properties
- vs.teamarch.sequencediagram.shapes.properties
helpviewer_keywords:
- UML sequence diagrams, properties
- sequence diagrams, properties
ms.assetid: 475c10f3-a2d2-4a1e-b366-dc28997d437e
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a6008566f71a241fb5daccab8d6a5dcb68882452
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444415"
---
# <a name="properties-of-elements-on-uml-sequence-diagrams"></a>UML 시퀀스 다이어그램 요소의 속성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML 시퀀스 다이어그램에서 다이어그램의 각 요소에는 속성이 있습니다. 요소의 속성을 보려면 다이어그램 또는 요소를 마우스 오른쪽 단추로 **UML 모델 탐색기** 을 클릭 한 다음 **속성**합니다. 속성에 표시 된 **속성** 창입니다.  
  
> [!NOTE]
> 이 항목은 UML 시퀀스 다이어그램 요소의 속성에 대한 것입니다. UML 시퀀스 다이어그램을 읽는 방법에 대 한 자세한 내용은 참조 하세요. [UML 시퀀스 다이어그램: 참조](../modeling/uml-sequence-diagrams-reference.md)를 참조하세요. UML 시퀀스 다이어그램을 그리는 방법에 대 한 자세한 내용은 참조 하세요. [UML 시퀀스 다이어그램: 지침](../modeling/uml-sequence-diagrams-guidelines.md)합니다.  
  
## <a name="properties-of-elements"></a>요소의 속성  
  
|속성|기본|요소|설명|  
|--------------|-------------|-------------|-----------------|  
|**이름**|기본 이름|모두|요소를 식별합니다.|  
|**정규화 된 이름**|패키지: 이름|모두|요소를 고유하게 식별합니다. 요소를 포함하는 패키지의 정규화된 이름이 접두사로 추가됩니다.|  
|**작업 항목**|0 associated|모두|이 요소와 연결된 작업 항목 수입니다. 작업 항목에 연결 하려면을 참조 하세요 [모델 요소에 연결 하 고 작업 항목](../modeling/link-model-elements-and-work-items.md)합니다.|  
|**설명**|(비어 있음)|모두|여기서 항목에 대한 일반적인 메모를 만들 수 있습니다.|  
|**색**|(요소 형식에 대한 기본값)|수명선, 메시지|도형의 색입니다. 이 속성은 모양이 표시하는 요소가 아니라 모양의 속성입니다.|  
|**Type**|(비어 있음)|수명선|수명선이 나타내는 인스턴스 형식입니다.<br /><br /> 수명선의 머리글에 표시되는 참조 기호가 있는 경우 이 클래스 또는 인터페이스가 UML 모델 탐색기에 별도로 존재하며 클래스 다이어그램에 표시될 수 있습니다.|  
|**행위자**|False|수명선|수명선이 다이어그램과 관련된 구성 요소 외부에 있는 사용자, 디바이스 또는 소프트웨어 구성 요소를 나타내는지 여부를 표시합니다.|  
|**Kind**|**전체** -메시지 보낸 사람 및 받는 사람입니다.<br /><br /> **찾을** -메시지는 지정 되지 않은 보낸 사람입니다.<br /><br /> **손실** -받는 사람을 알 수 없는 메시지.|메시지|수명선에 연결된 메시지의 끝을 나타냅니다.<br /><br /> 이 속성은 변경할 수 없습니다. 메시지를 만들 때 설정됩니다.|  
|**정렬**|**AsynchCall** -비동기 메시지입니다.<br /><br /> **SynchCall** -동기 메시지입니다.<br /><br /> **회신** -동기 메시지의 반환 부분입니다.<br /><br /> **CreateMessage** -인스턴스 생성 메시지입니다.|메시지|메시지의 형식입니다. 이 속성은 변경할 수 없습니다. 메시지를 만드는 데 사용하는 도구에 의해 결정됩니다.|  
|**연산**|(비어 있음)|메시지|받는 수명선에서 메시지에 의해 호출되는 메서드입니다.<br /><br /> 받는 수명선이 인터페이스 또는 클래스에 연결된 경우에만 표시됩니다.|  
|**참조**|시퀀스 다이어그램|상호 작용 사용|이 상호 작용 사용에서 호출되는 시퀀스 다이어그램입니다.|  
|**상호 작용 연산자**|사용한 경우에 설정 된 **감싸기** 명령|결합 조각|이 조각 또는 조각 컬렉션이 나타내는 연산자입니다.|  
|**가드**|(비어 있음)|결합 조각의 상호 작용 피연산자|가드가 true가 아니면 조각의 시퀀스가 발생하지 않습니다.<br /><br /> 결합된 조각의 최상위 조각을 선택하려면 조각 제목 아래를 클릭합니다.|  
|**최소, 최대**|(제한 없음)|루프 결합 조각|루프가 실행되는 최소 및 최대 횟수입니다.|  
|**메시지**|(비어 있음)|결합 조각 고려 및<br /><br /> 무시|이 조각에서 고려되거나 무시되는 메시지입니다.|  
  
## <a name="see-also"></a>참고 항목  
 [UML 시퀀스 다이어그램: 참조](../modeling/uml-sequence-diagrams-reference.md)   
 [UML 시퀀스 다이어그램: 지침](../modeling/uml-sequence-diagrams-guidelines.md)   
 [UML 시퀀스 다이어그램의 조각으로 제어 흐름 설명](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md)
