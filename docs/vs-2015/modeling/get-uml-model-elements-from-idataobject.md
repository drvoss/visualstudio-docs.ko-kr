---
title: IDataObject에서 UML 모델 요소 가져오기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, copy and paste
ms.assetid: e0b9cec8-3b93-4a24-8bd3-3e086501d387
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a5f60338a8a856b4c6ef8fa913d6d7168ff67bb9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63427034"
---
# <a name="get-uml-model-elements-from-idataobject"></a>IDataObject에서 UML 모델 요소 가져오기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

사용자가 소스에서 다이어그램으로 요소를 끌어 오면 끌어 온 요소가 `System.Windows.Forms.IDataObject`에서 인코딩됩니다. 인코딩은 소스 개체 형식에 따라 다릅니다. 다음 조각에서는 소스가 UML 다이어그램일 때 요소를 검색하는 방법을 보여 줍니다.  
  
> [!NOTE]
> 형식을 사용 하 여 UML 모델에서 수행 해야 하는 작업의 대부분을 수행할 수 있는 어셈블리에서 정의 **Microsoft.VisualStudio.Uml.Interfaces** 고  **Microsoft.VisualStudio.ArchitectureTools.Extensibility**합니다. 하지만 이 예제에서는 UML 모델링 도구 구현의 파트인 일부 클래스를 사용해야 합니다. 예를 들어 이 조각의 `ShapeElement`는 UML `IShape`와 같지 않습니다. UML 모델 및 다이어그램이 불일치 상태로 전환되는 위험을 줄이려면 대체 방법이 없는 경우를 제외하고 이들 구현 클래스에서 메서드를 사용하지 않는 것이 좋습니다.  
  
## <a name="code-sample"></a>코드 샘플  
 프로젝트는 다음을 참조 해야 [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] 어셈블리:  
  
 **Microsoft.VisualStudio.Modeling.Sdk.[version]**  
  
 **Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]**  
  
 **System.Windows.Forms**  
  
```  
using Microsoft.VisualStudio.Modeling;    
  // for ElementGroupPrototype  
using Microsoft.VisualStudio.Modeling.Diagrams;    
  // for ShapeElement, DiagramDragEventArgs, DiagramPointEventArgs  
…   
  /// <summary>  
  /// Retrieves UML IElements from drag arguments.  
  /// Works for drags from UML diagrams.  
  /// </summary>  
  private IEnumerable<IElement> GetModelElementsFromDragEvent  
                  (DiagramDragEventArgs dragEvent)  
  {  
     //ElementGroupPrototype is the container for  
     //dragged and copied elements and toolbox items.  
     ElementGroupPrototype prototype =  
        dragEvent.Data.  
        GetData(typeof(ElementGroupPrototype))  
                     as ElementGroupPrototype;  
     // Locate the originals in the implementation store.  
     IElementDirectory implementationDirectory =   
        dragEvent.DiagramClientView.Diagram.Store.ElementDirectory;  
  
     return  prototype.ProtoElements.Select(  
       prototypeElement =>   
       {  
          ModelElement element = implementationDirectory  
                .FindElement(prototypeElement.ElementId);  
          ShapeElement shapeElement = element as ShapeElement;  
          if (shapeElement != null)  
          {   
            // Dragged from a diagram.  
            return shapeElement.ModelElement as IElement;  
          }  
          else  
          {   
            // Dragged from UML Model Explorer.  
            return element as IElement;  
          }  
        });  
    }  
```  
  
 에 대 한 자세한 내용은 `ElementGroupPrototype` 및 `Store` 표시는 UML 모델링 도구가 구현 되 [Modeling SDK for Visual Studio-도메인별 언어](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [UML API를 사용한 프로그래밍](../modeling/programming-with-the-uml-api.md)   
 [모델링 다이어그램의 메뉴 명령 정의](../modeling/define-a-menu-command-on-a-modeling-diagram.md)
