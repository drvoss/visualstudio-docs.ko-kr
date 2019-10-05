---
title: 요소 도구 사용자 지정 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6dac48b6-db68-4bcd-8aa2-422c2ad5d28b
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 72457070c63cdf6c76207bd92521ab7944d4318a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199853"
---
# <a name="customizing-element-tools"></a>요소 도구 사용자 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

일부 DSL 정의에서 요소 그룹으로 단일 개념을 나타냅니다. 예를 들어, 구성 요소에 고정된 된 포트 집합 모델을 만들려면 항상 하려는 경우 해당 부모 구성 요소와 같은 시간에는 포트입니다. 따라서 요소 하나가 아닌 그룹에 있도록 요소 작성 도구를 사용자 지정 해야 합니다. 이 위해 요소 작성 도구를 초기화 하는 방법을 사용자 지정할 수 있습니다.  
  
 도구는 다이어그램 또는 요소를 끌 경우 재정의할 수 있습니다.  
  
## <a name="customizing-the-content-of-an-element-tool"></a>요소 도구의 콘텐츠를 사용자 지정  
 인스턴스를 저장 하는 각 요소 도구는 <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> EGP ()에 있는 하나 이상의 모델 요소 및 링크의 serialize 된 버전입니다. 기본적으로 요소 도구의 EGP를 도구용 지정 하는 클래스의 인스턴스 하나를 포함 합니다. 재정의 하 여이 변경할 수 있습니다 *YourLanguage*`ToolboxHelper.CreateElementToolPrototype`합니다. 이 메서드는 DSL 패키지를 로드할 때 호출 됩니다.  
  
 메서드의 매개 변수는 DSL 정의에서 지정한 클래스의 ID입니다. 관심 있는 클래스와 메서드가 호출 되 면 추가 요소는 EGP에 추가할 수 있습니다.  
  
 EGP 보조 요소에 대 한 기본 요소에서 링크 포함 포함 해야 합니다. 참조 링크를 포함할 수도 있습니다.  
  
 다음 예제에서는 기본 요소 및 두 개의 포함 된 요소를 만듭니다. 저항기, 라고 하는 기본 클래스 있고 터미널 라는 요소에 두 개의 포함 관계입니다. 포함 하는 역할 속성의 이름은 Terminal1 및 Terminal2, 둘 다 복합성이 1.. 1 인 하며  
  
```  
using Microsoft.VisualStudio.Modeling; ...    
public partial class CircuitDiagramToolboxHelper  
{  
  protected override ElementGroupPrototype    CreateElementToolPrototype(Store store, Guid domainClassId)  
  {  
    // A case for each tool to customize:    
    if (domainClassId == Resistor.DomainClassId)  
    {  
      // Set up the prototype elements and links:  
      Resistor resistor = new Resistor(store);  
      resistor.Terminal1 = new Terminal(store);   
      resistor.Terminal2 = new Terminal(store);  
      resistor.Terminal1.Name = "T1"; // embedding  
      resistor.Terminal2.Name = "T2"; // embedding  
      // We could also set up reference links.  
  
      // Create an element group prototype for the toolbox:  
      ElementGroup egp = new ElementGroup(store.DefaultPartition);  
      egp.AddGraph(resistor, true);  
      // We do not have to explicitly include embedded children.  
      return egp.CreatePrototype();  
    }  
    // Element tools for other classes:  
    else  
      return base.CreateElementToolPrototype(store, domainClassId);  
  }  
}  
```  
  
## <a name="see-also"></a>관련 항목  
 [요소 만들기 및 이동 사용자 지정](../modeling/customizing-element-creation-and-movement.md)
