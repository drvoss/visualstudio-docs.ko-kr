---
title: 'UML 시퀀스 다이어그램: 참조 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.sequencediagram.diagram
- vs.teamarch.UMLModelExplorer.sequencediagram
- vs.teamarch.sequencediagram.toolbox
helpviewer_keywords:
- diagrams - modeling, sequence
- sequence diagrams
- UML diagrams, sequence
- diagrams - modeling, UML sequence
- UML, sequence diagrams
ms.assetid: 366fc324-aeeb-4894-bd13-ec2e40754b8e
caps.latest.revision: 43
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3990d43ae11db3db8eb792883ba62a030cde3a2f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62548576"
---
# <a name="uml-sequence-diagrams-reference"></a>UML 시퀀스 다이어그램: 참조
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에는 *시퀀스 다이어그램* 클래스, 구성 요소, 하위 시스템 또는 행위자 인스턴스 간의 메시지의 시퀀스를 나타내는 상호 작용을 보여 줍니다. 시간은 다이어그램 아래로 진행하고, 참가자 간의 제어 흐름을 보여 줍니다. 시퀀스 다이어그램을 사용하여 클래스와 메서드 대신 인스턴스 및 이벤트를 시각화합니다. 동일한 형식의 인스턴스가 두 개 이상 다이어그램에 나타날 수 있습니다. 동일한 메시지가 두 번 이상 나타날 수도 있습니다.  
  
 UML 시퀀스 다이어그램은 UML 모델의 일부이며 UML 모델링 프로젝트 내에만 존재합니다. UML 시퀀스 다이어그램을 만들려면 하는 **아키텍처** 메뉴에서 클릭 **새 UML 또는 레이어 다이어그램**합니다. 만들고 그리는 방법에 대해 자세히 알아봅니다 [UML 시퀀스 다이어그램](../modeling/uml-sequence-diagrams-guidelines.md) 하거나 [UML 모델링 다이어그램](../modeling/edit-uml-models-and-diagrams.md) 일반적입니다.  
  
 이 기능을 지원하는 Visual Studio 버전을 확인하려면 [아키텍처 및 모델링 도구에 대한 버전 지원](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.  
  
## <a name="reading-sequence-diagrams"></a>시퀀스 다이어그램 읽기  
 다음 표에서는 시퀀스 다이어그램에서 사용할 수 있는 요소에 대해 설명합니다. 이 대해 자세히 알아봅니다 [요소의 속성이](../modeling/properties-of-elements-on-uml-sequence-diagrams.md)합니다.  
  
 ![시퀀스 다이어그램의 부분](../modeling/media/uml-sequence.png "UML_Sequence")  
  
|**셰이프**|**요소**|**설명**|  
|---------------|-----------------|---------------------|  
|1|**수명선**|시간이 줄 아래로 진행되는 동안 상호 작용 중에 참가자에게 발생하는 이벤트 시퀀스를 나타내는 세로줄입니다. 이 참가자는 클래스, 구성 요소 또는 행위자 인스턴스일 수 있습니다.|  
|2|**행위자**|개발 중인 시스템 외부에 있는 참가자입니다.<br /><br /> 행위자 기호를 설정 하 여 수명선의 맨 위에 있는 표시할 수 있게 해당 **행위자** 속성입니다.|  
|3|**동기 메시지**|보낸 사람이 계속하기 전에 동기 메시지에 대한 응답을 기다립니다. 다이어그램에 호출 및 반환이 둘 다 표시됩니다. 동기 메시지는 프로그램 내의 일반 함수 호출과 동일한 방식으로 동작하는 다른 종류의 메시지를 나타내는 데 사용됩니다.|  
|4|**비동기 메시지**|보낸 사람이 계속하기 전에 응답을 요구하지 않는 메시지입니다. 비동기 메시지는 보낸 사람의 호출만 표시합니다. 개별 스레드 간의 통신이나 새 스레드 생성을 나타내는 데 사용합니다.|  
|5|**실행 발생**|참가자 수명선에 표시되고 참가자가 작업을 실행하는 기간을 나타내는 세로 음영 사각형입니다.<br /><br /> 참가자가 메시지를 수신하면 실행이 시작됩니다. 시작 메시지가 동기 메시지인 경우 실행이 종료되고 보낸 사람에게 «반환» 화살표가 돌아갑니다.|  
|6|**콜백 메시지**|이전 호출의 반환을 기다리는 참가자에게 다시 반환되는 메시지입니다. 결과로 생성된 실행 발생이 기존 발생 위에 나타납니다.|  
|7|**자체 메시지**|참가자가 자신에게 보낸 메시지입니다. 결과로 생성된 실행 발생이 전송 실행 위에 나타납니다.|  
|8|**메시지 만들기**|참가자를 만드는 메시지입니다. 참가자가 만들기 메시지를 수신하는 경우 받은 첫 번째 메시지여야 합니다.|  
|10|**찾기 메시지**|알 수 없거나 지정되지 않은 참가자로부터 받은 비동기 메시지입니다.|  
|10|**손실된 메시지**|알 수 없거나 지정되지 않은 참가자에게 보내는 비동기 메시지입니다.|  
|11|**설명**|주석은 수명선의 임의 지점에 연결할 수 있습니다.|  
|12|**상호 작용 사용**|다른 다이어그램에서 정의된 메시지 시퀀스를 묶습니다.<br /><br /> 만들려는 프로그램 **상호 작용 사용**, 도구를 클릭 한 다음 포함 하려는 수명선으로 끕니다.|  
|13|**결합된 조각**|조각 컬렉션입니다. 각 조각이 하나 이상의 메시지를 묶을 수 있습니다. 다양한 종류의 결합 조각이 있습니다. 자세한 내용은 [UML 시퀀스 다이어그램의 조각으로 제어 흐름 Describe](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md)합니다.<br /><br /> 조각을 만들려면 메시지를 마우스 오른쪽 단추로 클릭, 가리킨 **감싸기**, 다음 조각 형식을 클릭 합니다.|  
|14|**조각 가드**|조각이 발생하는지 여부와 관련된 조건을 설명하는 데 사용할 수 있습니다.<br /><br /> 가드를 설정하려면 조각을 선택하고 가드를 선택한 다음 값을 입력합니다.|  
|**X**|**소멸 이벤트**|개체가 삭제되거나 더 이상 액세스할 수 없는 지점을 나타냅니다. 모든 수명선의 맨 아래에 나타납니다.|  
||**상호 작용**|시퀀스 다이어그램에 표시되는 메시지 및 수명선 컬렉션입니다. 상호 작용의 속성을 보려면에서 선택 해야 하면 **UML 모델 탐색기**합니다.|  
||**시퀀스 다이어그램**|상호 작용을 표시하는 다이어그램입니다. 해당 속성을 보려면 다이어그램의 빈 부분을 클릭합니다. **참고:**  시퀀스 다이어그램, 다이어그램에 표시되는 상호 작용 및 다이어그램을 포함하는 파일의 이름이 모두 다를 수 있습니다.|  
  
## <a name="see-also"></a>참고 항목  
 [UML 시퀀스 다이어그램: 지침](../modeling/uml-sequence-diagrams-guidelines.md)   
 [UML 모델 및 다이어그램 편집](../modeling/edit-uml-models-and-diagrams.md)   
 [UML 사용 사례 다이어그램: 참조](../modeling/uml-use-case-diagrams-reference.md)   
 [UML 클래스 다이어그램: 참조](../modeling/uml-class-diagrams-reference.md)   
 [UML 구성 요소 다이어그램: 참조](../modeling/uml-component-diagrams-reference.md)   
 [UML 구성 요소 다이어그램: 참조](../modeling/uml-component-diagrams-reference.md)
