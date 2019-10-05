---
title: 속성 창 사용자 지정 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, Properties window
ms.assetid: b6658de5-4e85-4628-93b2-5cc12f63d25b
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3e391e21ac16bdbee9fc2881b264f964a4b28cc0
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433228"
---
# <a name="customizing-the-properties-window"></a>속성 창 사용자 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

사용자 지정할 수 있습니다 모양 및 동작의 속성 창에서 도메인 특정 언어 (DSL) [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]합니다. DSL 정의에서 각 도메인 클래스에 도메인 속성을 정의합니다. 기본적으로 모델 탐색기 또는 다이어그램에서 클래스의 인스턴스를 선택 하면 속성 창에서 모든 도메인 속성 나열 됩니다. 이 수 다이어그램에서 셰이프 필드에 매핑되지 않은 하는 경우에 하 고 도메인 속성의 값을 편집 합니다.  
  
## <a name="names-descriptions-and-categories"></a>이름, 설명 및 범주  
 **이름 및 표시 이름을**입니다. 도메인 속성의 정의에서 속성의 표시 이름 속성 창에서 런타임에 표시 되는 이름입니다. 반면, 이름 속성을 업데이트 하는 프로그램 코드를 작성 하는 경우 사용 됩니다. 이름에는 올바른 CLR 영숫자 이름 이어야 합니다. 하지만 표시 이름은 공백을 포함할 수 있습니다.  
  
 DSL 정의에서 속성의 이름으로 설정 하면 해당 표시 이름은 이름의 복사본을 자동 설정 됩니다. "FuelGauge"와 같은 파스칼식 대/소문자 이름, 작성 하는 경우 표시 이름을 공간을 자동으로 포함 됩니다. "연료 계기"입니다. 그러나 다른 값으로 명시적으로 표시 이름을 설정할 수 있습니다.  
  
 **설명**합니다. 도메인 속성 설명은 두 곳에 나타납니다.  
  
- 속성을 선택 하면 속성 창의 맨 아래입니다. 속성이 무엇을 나타내는지 사용자에 게 설명 하기 위해 사용할 수 있습니다.  
  
- 생성 된 프로그램 코드입니다. API 설명서를 추출 하려면 설명서 기능을 사용 하는 경우 API에서이 속성의 설명으로 표시 됩니다.  
  
  **범주**. 범주는 속성 창의 제목입니다.  
  
## <a name="exposing-style-features"></a>스타일 기능을 노출합니다.  
 그래픽 요소 동적 기능 중 일부를 나타낼 수 있습니다 또는 *노출* 도메인 속성으로. 사용자가이 방식으로 노출 된 기능을 업데이트할 수 있습니다 하 고 더 쉽게 업데이트할 수 있습니다 프로그램 코드입니다.  
  
 DSL 정의에서 모양 클래스를 마우스 오른쪽 **Add Exposed**, 한 다음 기능을 선택 합니다.  
  
 모양에 노출할 수 있습니다 합니다 **FillColor**, **OutlineColor**를 **TextColor**를 **OutlineDashStyle**,  **OutlineThickness** 하 고 **FillGradientMode** 속성입니다. 커넥터를 노출할 수 있습니다 합니다 **색**`,`**TextColor**를 **DashStyle**, 및 **두께** 속성입니다. 다이어그램에 노출할 수 있습니다 합니다 **FillColor** 하 고 **TextColor** 속성입니다.  
  
## <a name="forwarding-displaying-properties-of-related-elements"></a>전달 합니다. 관련 요소의 속성 표시  
 DSL의 사용자가 모델에서 요소를 선택 하면 속성 창에서 해당 요소의 속성이 표시 됩니다. 그러나 지정 된 관련 요소의 속성을 표시할 수 있습니다. 함께 작동 하는 요소 그룹을 정의 하는 경우에 유용 합니다. 예를 들어, 기본 요소 및 선택적 플러그 인 요소를 정의할 수 있습니다. 기본 요소는 도형에 매핑된 다른 경우 한 요소에 있는 것 처럼 해당 속성을 보려는 유용 합니다.  
  
 이 효과 라고 *속성 전달*, 여러 사례에서 자동으로 발생 합니다. 다른 경우에는 도메인 형식 설명자를 정의 하 여 전달 하는 속성을 얻을 수 있습니다.  
  
### <a name="default-property-forwarding-cases"></a>기본 속성 전달 사례  
 탐색기에서 도형 또는 연결선 또는 요소를 선택 하는 사용자, 속성 창에서 다음 속성이 표시 됩니다.  
  
- 기본 클래스에 정의 된 포함 하 여 모델 요소의 도메인 클래스에 정의 된 도메인 속성입니다. 예외는 도메인 속성을 설정한 **Is Browsable** 에 `False`입니다.  
  
- 복합성이 0..1 관계를 통해 연결 된 요소의 이름입니다. 관계에 대 한 커넥터 매핑을 정의 하지 않은 경우에 필요에 따라 표시 되는 편리한 방법을 연결 요소를 제공 합니다.  
  
- 요소를 대상으로 하는 포함 관계의 도메인 속성입니다. 포함 관계는 일반적으로 표시 되지 않으면 명시적으로 하므로 해당 속성을 볼 수 있게 해줍니다.  
  
- 선택한 셰이프 또는 연결선에 정의 된 도메인 속성입니다.  
  
### <a name="adding-property-forwarding"></a>추가 속성 전달  
 속성을 전달 하기 도메인 형식 설명자를 정의 합니다. 두 도메인 클래스 간에 도메인 관계에 있는 경우에 두 번째 도메인 클래스의 도메인 속성의 첫 번째 클래스 값의에서 도메인 속성을 설정 하려면 도메인 형식 설명자를 사용할 수 있습니다. 예를 들어, 관계가 있는 경우는 **책** 도메인 클래스 및 **작성자** 도메인 클래스에 도메인 형식 설명자를 만드는 데 사용할 수 있습니다 합니다 **이름** 의 속성을 책 **작성자** 책을 선택 하면 속성 창에 나타납니다.  
  
> [!NOTE]
> 사용자가 모델을 편집할 때 속성 창만 적용 하는 속성이 전달 됩니다. 받는 클래스에 도메인 속성을 정의 하지 않습니다. 프로그램 코드 또는 DSL 정의의 다른 부분에 전달 된 도메인 속성에 액세스 하려는 경우 전달 요소를 액세스 해야 합니다.  
  
 다음 절차에서는 DSL을 만들었다고 가정 합니다. 몇 가지는 첫 번째 단계는 필수 구성 요소를 요약합니다.  
  
##### <a name="to-forward-a-property-from-another-element"></a>다른 요소에서 속성을 전달 하도록  
  
1. 만들기는 [!INCLUDE[dsl](../includes/dsl-md.md)] 이 예에서 이라고 하는 두 개 이상의 클래스를 포함 하는 솔루션 **책** 하 고 **작성자**합니다. 간의 두 종류의 관계가 없어야 **책** 하 고 **작성자**합니다.  
  
     소스 역할의 복합성 (에서 역할에는 **책** 쪽) 0..1 또는 1.. 1로, 해야 하므로 각 **책** 하나에 **작성자**합니다.  
  
2. **DSL 탐색기**를 마우스 오른쪽 단추로 클릭 합니다 **책** 도메인 클래스 및 클릭 **새의 DomainTypeDescriptor 추가**합니다.  
  
     라는 노드가 **사용자 지정 속성 설명자 경로** 아래에 표시 됩니다는 **사용자 지정 형식 설명자** 노드.  
  
3. 마우스 오른쪽 단추로 클릭 합니다 **사용자 지정 형식 설명자** 노드를 차례로 클릭 한 다음 **새 PropertyPath 추가**합니다.  
  
     새 속성 경로 아래에 표시 됩니다는 **사용자 지정 속성 설명자 경로** 노드.  
  
4. 새 속성 경로 선택 및를 **속성** 창에서 **속성의 경로를** 적절 한 모델 요소의 경로에 있습니다.  
  
     이 속성의 오른쪽에 있는 아래쪽 화살표를 클릭 하 여 트리 뷰의 경로 편집할 수 있습니다. 도메인 경로 대 한 자세한 내용은 참조 하세요. [도메인 경로 구문](../modeling/domain-path-syntax.md)합니다. 경로 편집한 경우와 유사 **BookReferencesAuthor.Author/! 작성자**합니다.  
  
5. 설정 **속성** 에 **이름** 의 도메인 속성 **작성자**합니다.  
  
6. 설정할 **표시 이름** 하 **이름을 작성**합니다.  
  
7. 모든 템플릿 변환 빌드하고 DSL을 실행 합니다.  
  
8. 모델 다이어그램에서 책, 저자 만들고 참조 관계를 사용 하 여 연결 합니다. Book 요소를 선택 하 고 속성 창에서 책 외에도 작성자 이름이 표시 됩니다. 연결된 작성자의 이름을 변경 하거나 다른 작성자, 책 연결할 하 고 책의 저자 이름이 변경를 관찰 합니다.  
  
## <a name="custom-property-editors"></a>사용자 지정 속성 편집기  
 속성 창에는 편집 환경을 각 도메인 속성의 형식에 대 한 적절 한 기본값을 제공 합니다. 예를 들어, 열거 형식에 대 한 드롭 다운 목록을 사용자에 게 표시 및 사용자 숫자 속성에 대 한 숫자를 입력할 수 있습니다. 기본 제공 형식에만 그렇습니다. 외부 형식을 지정 하면, 사용자 속성의 값을 표시 하지만 편집할 수는 없습니다 수 됩니다.  
  
 그러나 다음 편집기 및 형식을 지정할 수 있습니다.  
  
1. 표준 형식으로 사용 되는 다른 편집기입니다. 예를 들어 문자열 속성에 대 한 파일 경로 편집기를 지정할 수 있습니다.  
  
2. 도메인 속성에 대 한 편집기에는 외부 형식입니다.  
  
3. 파일 경로 편집기 등.NET 편집기를 사용자 고유의 사용자 지정 속성 편집기를 만들 수 있습니다.  
  
    외부 형식 및 문자열 기본 편집기에는 같은 형식 간에 변환 합니다.  
  
   DSL에는 *외부 형식* 해당 하는 단순 형식 (예: 부울 또는 Int32) 또는 문자열 중 하나가 아닙니다.  
  
#### <a name="to-define-a-domain-property-that-has-an-external-type"></a>도메인 속성을 정의 하는 외부 형식 포함  
  
1. **솔루션 탐색기**, 외부 형식에 포함 된 어셈블리 (DLL)에 대 한 참조를 추가 합니다 **Dsl** 프로젝트입니다.  
  
    어셈블리는.NET 어셈블리 또는 사용자가 제공 하는 어셈블리 수 있습니다.  
  
2. 형식을 추가 합니다 **도메인 형식** 있습니다 아직 하지 않는 한 목록입니다.  
  
   1. DslDefinition.dsl을 엽니다 및 **DSL 탐색기**루트 노드를 마우스 오른쪽 단추로 클릭 한 다음 클릭 **새 외부 형식 추가**합니다.  
  
        아래에 새 항목이 표시 됩니다는 **도메인 형식** 노드.  
  
       > [!WARNING]
       > 메뉴 항목은 DSL 루트 노드에서 아닙니다 합니다 **도메인 형식** 노드.  
  
   2. 속성 창에서 이름 및 새 형식의 네임 스페이스를 설정 합니다.  
  
3. 일반적인 방법으로 도메인 클래스에 도메인 속성을 추가 합니다.  
  
    속성 창에서 드롭 다운 목록에서 외부 형식을 선택 합니다 **형식** 필드입니다.  
  
   이 단계에서는 사용자 속성의 값을 볼 수 있지만 편집할 수 없습니다. 표시 된 값에서 가져온는 `ToString()` 함수입니다. 명령 또는 규칙의 예를 들어 속성의 값을 설정 하는 프로그램 코드를 작성할 수 있습니다.  
  
### <a name="setting-a-property-editor"></a>속성 편집기를 설정합니다.  
 도메인 속성에 다음과 같은 형태로 CLR 특성을 추가 합니다.  
  
```  
[System.ComponentModel.Editor (  
   typeof(AnEditor),  
   typeof(System.Drawing.Design.UITypeEditor))]  
  
```  
  
 사용 하 여 속성에 특성을 설정할 수는 **사용자 지정 특성** 속성 창에서 항목입니다.  
  
 형식의 `AnEditor` 두 번째 매개 변수에 지정 된 형식에서 파생 되어야 합니다. 두 번째 매개 변수는이 중 하나 여야 <xref:System.Drawing.Design.UITypeEditor> 또는 <xref:System.ComponentModel.ComponentEditor>합니다. 자세한 내용은 <xref:System.ComponentModel.EditorAttribute>을 참조하세요.  
  
 에 제공 된 편집기 또는 자체 편집기를 지정할 수 있습니다 합니다 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]와 같은 <xref:System.Windows.Forms.Design.FileNameEditor> 또는 <xref:System.Drawing.Design.ImageEditor>합니다. 예를 들어, 다음 절차를 사용 하 여 사용자 파일 이름을 입력할 수 있는 속성이 있어야 합니다.  
  
##### <a name="to-define-a-file-name-domain-property"></a>파일 이름 도메인 속성을 정의 하려면  
  
1. 도메인 속성이 DSL 정의에서 도메인 클래스에 추가 합니다.  
  
2. 새 속성을 선택 합니다. 에 **사용자 지정 특성** 속성 창에서 필드에 다음 특성을 입력 합니다. 이 특성을 입력 하려면 줄임표 **[...]**  다음 특성 이름 및 매개 변수를 개별적으로 입력 합니다.  
  
    ```  
    [System.ComponentModel.Editor (  
       typeof(System.Windows.Forms.Design.FileNameEditor)  
       , typeof(System.Drawing.Design.UITypeEditor))]  
  
    ```  
  
3. 기본 설정 도메인 속성의 형식으로 그대로 둡니다 **문자열**합니다.  
  
4. 편집기를 테스트 하려면 사용자가 도메인 속성을 편집 하려면 파일 이름을 편집기를 열 수를 확인 합니다.  
  
    1. Ctrl+f5 또는 F5 키를 누릅니다. 디버깅 솔루션에 테스트 파일을 엽니다. 도메인 클래스의 요소를 만들고이 선택 합니다.  
  
    2. 속성 창에서 도메인 속성을 선택 합니다. 값 필드에 줄임표가 표시 **[...]** .  
  
    3. 줄임표를 클릭 합니다. 파일 대화 상자가 나타납니다. 파일을 선택 하 고 대화 상자를 닫습니다. 파일 경로 이제 도메인 속성의 값입니다.  
  
### <a name="defining-your-own-property-editor"></a>사용자 고유의 속성 편집기를 정의합니다.  
 사용자 고유의 편집기를 정의할 수 있습니다. 이렇게 하려면 사용자가 정의한 형식을 편집 하거나 특별 한 방식으로 표준 형식을 편집 하려면 사용자를 허용 하도록 합니다. 예를 들어 수식을 나타내는 문자열을 입력 하 여 허용할 수 있습니다.  
  
 편집기에서 파생 된 클래스를 작성 하 여 정의한 <xref:System.Drawing.Design.UITypeEditor>합니다. 클래스를 재정의 해야 합니다.  
  
- <xref:System.Drawing.Design.UITypeEditor.EditValue%2A>를 사용자와 상호 작용 하 여 속성 값을 업데이트 합니다.  
  
- <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>를 편집기 대화 상자를 엽니다는 또는 드롭 다운 메뉴를 제공 하는지 여부를 지정할 수 있습니다.  
  
  또한 그래픽으로 표현한 속성 표에 표시 되는 속성의 값을 제공할 수 있습니다. 이 작업을 수행 하려면 재정의 `GetPaintValueSupported`, 및 `PaintValue`합니다.  자세한 내용은 <xref:System.Drawing.Design.UITypeEditor>을 참조하세요.  
  
> [!NOTE]
> 별도 코드 파일에서 코드를 추가 합니다 **Dsl** 프로젝트입니다.  
  
 예를 들어:  
  
```  
internal class TextFileNameEditor : System.Windows.Forms.Design.FileNameEditor  
{  
  protected override void InitializeDialog(System.Windows.Forms.OpenFileDialog openFileDialog)  
  {  
    base.InitializeDialog(openFileDialog);  
    openFileDialog.Filter = "Text files(*.txt)|*.txt|All files (*.*)|*.*";  
    openFileDialog.Title = "Select a text file";  
  }  
}  
  
```  
  
 이 편집기를 사용 하려면 설정 합니다 **사용자 지정 특성** 도메인 속성:  
  
```  
[System.ComponentModel.Editor (  
   typeof(MyNamespace.TextFileNameEditor)  
   , typeof(System.Drawing.Design.UITypeEditor))]  
  
```  
  
 자세한 내용은 <xref:System.Drawing.Design.UITypeEditor>을 참조하세요.  
  
## <a name="providing-a-drop-down-list-of-values"></a>값의 드롭다운 목록을 제공합니다.  
 값에서 선택 하는 사용자 목록을 제공할 수 있습니다.  
  
> [!NOTE]
> 이 방법은 런타임 시 변경할 수 있는 값의 목록을 제공 합니다. 변경 되지 않는 목록이 제공 하려는 경우 대신 고려 도메인 속성의 형식으로 열거 형식을 사용 합니다.  
  
 표준 값 목록이 정의 하려면 속성을 추가 하 여 도메인 형식은 CLR 특성을 합니다.  
  
```  
[System.ComponentModel.TypeConverter   
(typeof(MyTypeConverter))]  
  
```  
  
 <xref:System.ComponentModel.TypeConverter>에서 파생된 클래스를 정의합니다. 별도 파일에 코드를 추가 합니다 **Dsl** 프로젝트입니다. 예를 들어:  
  
```csharp  
/// <summary>  
/// Type converter that provides a list of values   
/// to be displayed in the property grid.  
/// </summary>  
/// <remarks>This type converter returns a list   
/// of the names of all "ExampleElements" in the   
/// current store.</remarks>  
public class MyTypeConverter : System.ComponentModel.TypeConverter  
{  
  /// <summary>  
  /// Return true to indicate that we return a list of values to choose from  
  /// </summary>  
  /// <param name="context"></param>  
  public override bool GetStandardValuesSupported  
    (System.ComponentModel.ITypeDescriptorContext context)  
  {  
    return true;  
  }  
  
  /// <summary>  
  /// Returns true to indicate that the user has   
  /// to select a value from the list  
  /// </summary>  
  /// <param name="context"></param>  
  /// <returns>If we returned false, the user would   
  /// be able to either select a value from   
  /// the list or type in a value that is not in the list.</returns>  
  public override bool GetStandardValuesExclusive  
      (System.ComponentModel.ITypeDescriptorContext context)  
  {  
    return true;  
  }  
  
  /// <summary>  
  /// Return a list of the values to display in the grid  
  /// </summary>  
  /// <param name="context"></param>  
  /// <returns>A list of values the user can choose from</returns>  
  public override StandardValuesCollection GetStandardValues  
      (System.ComponentModel.ITypeDescriptorContext context)  
  {  
    // Try to get a store from the current context  
    // "context.Instance"  returns the element(s) that   
    // are currently selected i.e. whose values are being  
    // shown in the property grid.   
    // Note that the user could have selected multiple objects,   
    // in which case context.Instance will be an array.  
    Store store = GetStore(context.Instance);  
  
    List<string> values = new List<string>();  
  
    if (store != null)  
    {  
      values.AddRange(store.ElementDirectory  
        .FindElements<ExampleElement>()  
        .Select<ExampleElement, string>(e =>   
      {  
        return e.Name;  
      }));  
    }  
    return new StandardValuesCollection(values);  
  }  
  
  /// <summary>  
  /// Attempts to get to a store from the currently selected object(s)  
  /// in the property grid.  
  /// </summary>  
  private Store GetStore(object gridSelection)  
  {  
    // We assume that "instance" will either be a single model element, or   
    // an array of model elements (if multiple items are selected).  
  
    ModelElement currentElement = null;  
  
    object[] objects = gridSelection as object[];  
    if (objects != null && objects.Length > 0)  
    {  
      currentElement = objects[0] as ModelElement;  
    }  
    else  
    {  
        currentElement = gridSelection as ModelElement;  
    }  
  
    return (currentElement == null) ? null : currentElement.Store;  
  }  
  
}  
  
```  
  
## <a name="see-also"></a>참고 항목  
 [프로그램 코드에서 모델 탐색 및 업데이트](../modeling/navigating-and-updating-a-model-in-program-code.md)
