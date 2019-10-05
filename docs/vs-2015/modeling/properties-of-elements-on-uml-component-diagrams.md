---
title: UML 구성 요소 다이어그램 요소의 속성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.componentdiagram.shapes.properties
helpviewer_keywords:
- component diagrams, properties
- UML, element properties
ms.assetid: fa0a9460-6675-4642-aa00-50f8719a892d
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c7f3f30d08fb62defec5e783da286e968a6b17c9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444424"
---
# <a name="properties-of-elements-on-uml-component-diagrams"></a>UML 구성 요소 다이어그램 요소의 속성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML 구성 요소 다이어그램에서 다이어그램의 각 요소에는 속성이 있습니다. 요소의 속성을 보려면 다이어그램 또는 요소를 마우스 오른쪽 단추로 **UML 모델 탐색기** 을 클릭 한 다음 **속성**합니다. 속성에 표시 된 **속성** 창입니다.  
  
> [!NOTE]
> 이 항목은 UML 구성 요소 다이어그램 요소의 속성에 대한 것입니다. UML 구성 요소 다이어그램을 읽는 방법에 대 한 자세한 내용은 참조 하세요. [UML 구성 요소 다이어그램: 참조](../modeling/uml-component-diagrams-reference.md)를 참조하세요. UML 구성 요소 다이어그램을 그리는 방법에 대 한 자세한 내용은 참조 하세요. [UML 구성 요소 다이어그램: 지침](../modeling/uml-component-diagrams-guidelines.md)합니다.  
  
## <a name="properties-of-elements"></a>요소의 속성  
  
|속성|기본|요소|설명|  
|--------------|-------------|-------------|-----------------|  
|**이름**|기본 이름|모두|요소를 식별합니다.|  
|**정규화 된 이름**|Namespace:: 이름|모두|요소를 고유하게 식별합니다.<br /><br /> 구성 요소 또는 형식의 이름에는 요소를 포함하는 패키지의 정규화된 이름이 접두사로 추가됩니다.<br /><br /> 파트 또는 포트의 이름에는 요소를 소유하는 구성 요소의 정규화된 이름이 접두사로 추가됩니다.|  
|**작업 항목**|0 associated|모두|이 요소와 연결된 작업 항목 수입니다. 작업 항목에 연결 하려면을 참조 하세요 [모델 요소에 연결 하 고 작업 항목](../modeling/link-model-elements-and-work-items.md)합니다.|  
|**설명**|(없음)|모두|여기서 요소에 대한 일반적인 메모를 만들 수 있습니다.|  
|**색**|(형식 기본값)|구성 요소, 파트, 위임 및 파트 어셈블리|도형의 색입니다. 다른 속성과 달리, 모양이 표시하는 모델 요소가 아닌 모양의 색입니다.|  
|**간접 인스턴스화 됨**|True|구성 요소|구성 요소는 디자인 아티팩트로만 존재합니다. 런타임에는 해당 파트만 존재합니다.|  
|**추상 클래스**|False|구성 요소|구성 요소 정의는 다른 구성 요소가 특수화될 수 있는 일반화로만 사용할 수 있습니다.|  
|**표시 유형**|Public|구성 요소, 파트, 포트|**공용** -전체적으로 표시 합니다.<br /><br /> **패키지** -패키지 내에 표시 합니다.<br /><br /> **개인** -의 소유 구성 요소 내에 표시 합니다.<br /><br /> **보호 된** -소유자 로부터 파생 된 구성 요소에 표시 합니다.|  
|**Type**|생성 시 형식|파트<br /><br /> 포트|파트 형식은 구성 요소 또는 클래스입니다.<br /><br /> 포트 형식은 인터페이스입니다.|  
|**다중성**|1|파트<br /><br /> 포트|부모 구성 요소의 파트를 구성하는 지정된 형식 인스턴스 수를 나타냅니다.<br /><br /> `1` - 정확히 하나.<br /><br /> `0..1` - 하나 또는 없음.<br /><br /> `*` - 개수 제한 없는 컬렉션.<br /><br /> `n..m` - n~m개 인스턴스의 컬렉션|  
|**동작은**|False|포트|True이면 이 포트에 대한 메시지는 해당 파트가 아니라 구성 요소 파트로 설명된 동작 또는 작업에 의해 처리됩니다.|  
|**서비스**|False|포트|True이면 이 포트는 이 구성 요소의 게시된 인터페이스 파트입니다.|  
|**LinkedPackage**|모델|다이어그램|이 다이어그램에 추가된 요소에 대한 기본 네임스페이스입니다.|  
  
## <a name="see-also"></a>참고 항목  
 [UML 사용 사례 다이어그램: 참조](../modeling/uml-use-case-diagrams-reference.md)   
 [UML 사용 사례 다이어그램: 지침](../modeling/uml-use-case-diagrams-guidelines.md)
