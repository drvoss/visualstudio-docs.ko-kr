---
title: 모양 및 연결선을 업데이트하여 모델 반영
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5b4c0c88e9e096836e32ce427ff78cc94f5d1f72
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62906991"
---
# <a name="update-shapes-and-connectors-to-reflect-the-model"></a>모양 및 연결선을 업데이트하여 모델 반영

Visual Studio에서 도메인 특정 언어에서 기본 모델의 상태를 반영 하는 도형의 모양을 만들 수 있습니다.

이 항목의 코드 예제에 추가 해야는 `.cs` 파일에 `Dsl` 프로젝트입니다. 각 파일에 이러한 문이 필요합니다.

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
```

## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>도형 맵에 데코레이터의 가시성을 제어 하는 속성 설정

DSL 정의에서 모양과 도메인 클래스 간의 매핑을 구성 하 여 프로그램 코드를 작성 하지 않고도 데코레이터의 가시성을 제어할 수 있습니다. 자세한 내용은 [도메인별 언어 정의 방법](../modeling/how-to-define-a-domain-specific-language.md)합니다.

## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>색 및 스타일 셰이프를 속성으로 노출

DSL 정의에서 모양 클래스를 마우스 오른쪽 **Add Exposed**, 다음 항목 중 하나를 같은 클릭 **채우기 색**합니다.

셰이프는 이제 프로그램 코드 또는 사용자로 설정할 수 있는 도메인 속성이 있습니다. 예를 들어, 명령 또는 규칙의 프로그램 코드에서 설정, 작성할 수 있습니다.

`shape.FillColor = System.Drawing.Color.Red;`

프로그램 제어만 하 고 사용자가 아니라 속성 변수를 확인 하려는 경우 새 도메인 속성을 같은 선택 **채우기 색** DSL 정의 다이어그램에서. 그런 다음 속성 창에서 설정 **Is Browsable** 를 `false` 설정할지 **UI는 Readonly** 에 `true`.

## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>색, 스타일 또는 모델 요소의 속성에 따라 위치를 확인 하는 변경 규칙 정의
 모델의 다른 부분에 따라 달라 집니다 셰이프 모양을 업데이트 하는 규칙을 정의할 수 있습니다. 예를 들어, 모델 요소의 속성에 따라 달라 집니다 모양의 색을 업데이트 하는 모델 요소에 대해 변경 규칙을 정의할 수 있습니다. 변경 규칙에 대 한 자세한 내용은 참조 하세요. [규칙이 전파 변경 내용을 내에서 모델](../modeling/rules-propagate-changes-within-the-model.md)합니다.

 규칙 실행 취소 명령을 수행 될 때 호출 되지 때문에 저장소에서 유지 관리 되는 속성을 업데이트에 규칙을 사용 해야 합니다. 여기에 크기와 셰이프의 표시 여부와 같은 일부 그래픽 기능은 포함 되지 않습니다. 도형의 이러한 기능을 업데이트 하려면 참조 [업데이트 되지 않은 저장소 그래픽 기능](#OnAssociatedProperty)합니다.

 다음 예제에서는 노출 했다고 가정 `FillColor` 이전 섹션에 설명 된 대로 도메인 속성으로.

```csharp
[RuleOn(typeof(ExampleElement))]
  class ExampleElementPropertyRule : ChangeRule
  {
    public override void ElementPropertyChanged(ElementPropertyChangedEventArgs e)
    {
      base.ElementPropertyChanged(e);
      ExampleElement element = e.ModelElement as ExampleElement;
      // The rule is called for every property that is updated.
      // Therefore, verify which property changed:
      if (e.DomainProperty.Id == ExampleElement.NameDomainPropertyId)
      {
        // There is usually only one shape:
        foreach (PresentationElement pel in PresentationViewsSubject.GetPresentation(element))
        {
          ExampleShape shape = pel as ExampleShape;
          // Replace this with a useful condition:
          shape.FillColor = element.Name.EndsWith("3")
                     ? System.Drawing.Color.Red : System.Drawing.Color.Green;
        }
      }
    }
  }
  // The rule must be registered:
  public partial class OnAssociatedPropertyExptDomainModel
  {
    protected override Type[] GetCustomDomainModelTypes()
    {
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
      types.Add(typeof(ExampleElementPropertyRule));
      // If you add more rules, list them here.
      return types.ToArray();
    }
  }
```

## <a name="use-onchildconfigured-to-initialize-a-shapes-properties"></a>OnChildConfigured 모양 속성을 초기화 하는 데

첫 번째 경우 셰이프 속성을 설정 하려면 만들어지면 재정의 `OnChildConfigured()` 다이어그램 클래스의 부분 정의에서. 다이어그램 클래스는 DSL 정의에서 지정 되 고 생성 된 코드는 **Dsl\Generated Code\Diagram.cs**합니다. 예를 들어:

```csharp
partial class MyLanguageDiagram
{
  protected override void OnChildConfigured(ShapeElement child, bool childWasPlaced, bool createdDuringViewFixup)
  {
    base.OnChildConfigured(child, childWasPlaced, createdDuringViewFixup);
    ExampleShape shape = child as ExampleShape;
    if (shape != null)
    {
      if (!createdDuringViewFixup) return; // Ignore load from file.
      ExampleElement element = shape.ModelElement as ExampleElement;
      // Replace with a useful condition:
      shape.FillColor = element.Name.EndsWith("3")
          ? System.Drawing.Color.Red : System.Drawing.Color.Green;
    }
    // else deal with other types of shapes and connectors.
  }
}
```

이 메서드는 모두 도메인 속성 및 도형의 크기와 같은 비 저장소 기능을 사용할 수 있습니다.

## <a name="OnAssociatedProperty"></a> AssociateValueWith() 모양의 다른 기능을 업데이트 하는 데

그림자를 또는 연결선의 화살표 스타일에 있는지 여부와 같은 모양의 일부 기능에 대 한 도메인 속성으로 기능을 노출 기본 설정 방법이 있습니다.  이러한 기능에 변경이 트랜잭션 시스템에 의해 제어 됩니다. 따라서 하기에 적합 하지 업데이트 규칙 실행 취소 명령을 수행할 때 호출 되지 때문에 규칙을 사용 하 여 합니다.

대신 사용 하 여 이러한 기능을 업데이트할 수 있습니다 <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A>합니다. 다음 예제에서는 화살표 스타일을 커넥터는 커넥터를 표시 하는 관계의 도메인 속성의 값으로 제어 됩니다.

```csharp
public partial class ArrowConnector // My connector class.
{
    /// <summary>
    /// Called whenever a registered property changes in the associated model element.
    /// </summary>
    /// <param name="e"></param>
    protected override void OnAssociatedPropertyChanged(VisualStudio.Modeling.Diagrams.PropertyChangedEventArgs e)
    {
      base.OnAssociatedPropertyChanged(e);
      // Can be called for any property change. Therefore,
      // Verify that this is the property we're interested in:
      if ("IsDirected".Equals(e.PropertyName))
      {
        if (e.NewValue.Equals(true))
        { // Update the shape's built-in Decorator feature:
          this.DecoratorTo = LinkDecorator.DecoratorEmptyArrow;
        }
        else
        {
          this.DecoratorTo = null; // No arrowhead.
        }
      }
    }

    // OnAssociatedPropertyChanged is called only for properties
    // that have been registered using AssociateValueWith().
    // InitializeResources is a convenient place to call this.
    // This method is invoked only once per class, even though
    // it is an instance method.
    protected override void InitializeResources(StyleSet classStyleSet)
    {
      base.InitializeResources(classStyleSet);
      AssociateValueWith(this.Store, Wire.IsDirectedDomainPropertyId);
      // Add other properties here.
    }
}
```

`AssociateValueWith()` 등록 하려는 각 도메인 속성에 한 번씩을 호출 되어야 합니다. 지정된 된 속성에 변경 내용을 호출 호출 된 후 `OnAssociatedPropertyChanged()` 속성의 모델 요소를 제공 하는 모든 셰이프에 있습니다.

호출 하는 데 필요한 아닙니다 `AssociateValueWith()` 각 인스턴스에 대 한 합니다. InitializeResources 인스턴스 메서드인 경우에 각 모양 클래스에 대 한 번만 호출 됩니다.
