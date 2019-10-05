---
title: 글꼴 및 Visual Studio에 대 한 서식 지정 | Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8634ab15a10b59fc21de390e0633d6d91793616d
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67891035"
---
# <a name="fonts-and-formatting-for-visual-studio"></a>글꼴 및 Visual Studio에 대 한 서식 지정
## <a name="BKMK_TheEnvironmentFont"></a> 환경 글꼴
 Visual Studio 내에서 모든 글꼴 사용자 지정에 대 한 사용자에 게 노출 되어야 합니다. 주로 이렇게 합니다 **글꼴 및 색** 페이지에 **도구 > 옵션** 대화 합니다. 글꼴 설정의 세 가지 주요 범주는:

- **환경 글꼴** -대화 상자, 메뉴, 도구 창 및 문서 창을 포함 하 여 모든 인터페이스 요소에 사용 되는 IDE (통합된 개발 환경)에 대 한 기본 글꼴입니다. 기본적으로 최신 버전의 Windows에서 9 pt Segoe UI로 표시 되는 시스템 글꼴은 환경 글꼴이 연결 됩니다. 모든 인터페이스 요소에 대 한 하나의 글꼴을 사용 하 여 IDE 전체에서 일관 된 글꼴 모양이 표시 되도록 하는 데 도움이 됩니다.

- **텍스트 편집기** -요소는 코드 및 기타 화면 편집기 텍스트를 기반으로 사용자 지정할 수 있습니다 텍스트 편집기에서 페이지의 **도구 > 옵션**합니다.

- **특정 컬렉션** -자체 설정 페이지에서 해당 인터페이스 요소의 사용자 지정 디자인 특정 글꼴을 노출할 수를 제공 하는 디자이너 창 표시 **도구 > 옵션**합니다.

### <a name="editor-font-customization-and-resizing"></a>편집기 글꼴 사용자 지정 및 크기 조정
 대개는 확대 사용자나 크기 및/또는 일반 사용자 인터페이스의 독립적인 해당 기본 설정에 따라 편집기에서 텍스트의 색을 확대/축소 합니다. 환경 글꼴 내에서 또는 편집기/designer의 일부로 표시 될 수 있는 요소를 사용할 경우, 이므로 이러한 글꼴 분류 중 하나가 변경 될 때 예상 되는 동작을 명심 해야 합니다.

 일부가 아닌 되지만 편집기에 표시 되는 UI 요소를 만들 때 합니다 *콘텐츠*, 예측 가능한 방식으로 요소의 크기가 조정 되도록 환경 글꼴 및 텍스트 글꼴 대신 사용 해야 합니다.

1. 편집기에서 코드 텍스트에 대 한 코드 텍스트 글꼴 설정을 사용 하 여 크기를 조정 하 고 편집기 텍스트의 확대/축소 수준으로 응답 합니다.

2. 인터페이스의 다른 모든 요소는 환경 글꼴 설정와 연결 해야 하 고 환경에서 모든 전역 변경 응답 합니다. 이 포함 하지만에 제한 되지 않습니다.

    - 상황에 맞는 메뉴의 텍스트

    - 텍스트 편집기 adornment에서 전구 메뉴 텍스트, 빠른 찾기 편집기 창 등의 창으로 이동

    - 같은 대화 상자에서 텍스트 레이블을 **파일에서 찾기** 또는 **리팩터링**

### <a name="accessing-the-environment-font"></a>환경 글꼴에 액세스
 기본 모드 또는 WinForms 코드 환경 글꼴 메서드를 호출 하 여 액세스할 수 있습니다 `IUIHostLocale::GetDialogFont` 에서 해당 인터페이스를 쿼리 한 후의 `SID_SUIHostLocale` 서비스입니다.

 에 대 한 Windows Presentation Foundation (WPF), 셸의에서 대화 상자 창 클래스를 파생 `DialogWindow` WPF의 대신 클래스 `Window` 클래스입니다.

 XAML에서의 코드는 다음과 같습니다.

```xaml
<ui:DialogWindow
    x:Class"MyNameSpace.MyWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:s="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:ui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0"
    ShowInTaskbar="False"
    WindowStartupLocation="CenterOwner"
    Title="My Dialog">
</ui:DialogWindow>
```

코드 숨김:

```csharp
internal partial class WebConfigModificationWindow : DialogWindow
{
}
```

 (대체 `Microsoft.VisualStudio.Shell.11.0` MPF dll의 현재 버전을 사용 하 여.)

 대화 상자를 표시 하려면 호출 "`ShowModal()`"를 통해 클래스에서 `ShowDialog()`합니다. `ShowModal()` 셸에서 올바른 모달 상태를 설정, 대화 상자에서 가운데에 맞춰지고 부모 창과 등을 확인 합니다.

 코드는 다음과 같습니다.

```csharp
MyWindow window = new MyWindow();
window.ShowModal()
```

 `ShowModal` 부울 값을 반환? (null 허용 부울 값) 사용 하 여는 `DialogResult`, 필요한 경우 사용할 수 있습니다. 반환 값은 대화 상자를 사용 하 여 닫힌 경우 true **확인**합니다.

 자체에서 작업을 하 고 호스트 되는 일부 WPF UI를 표시 하는 경우 `HwndSource`, 팝업 창 등 Win32/WinForms 부모 창의 자식 창에 WPF 설정 해야 합니다 `FontFamily` 및 `FontSize` WPF 요소의 루트 요소에 합니다. (주 창에 속성을 설정 하는 셸에서 있지만 지난 상속 되지 것입니다는 `HWND`). 셸에 속성을 바인딩할 수, 다음과 같은 리소스를 제공 합니다.

```xaml
<Setter Property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
<Setter Property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />
```

### <a name="BKMK_Formatting"></a> (확장/굵게 표시) 참조를 서식 지정
 일부 대화 상자에는 특정 텍스트를 굵게 또는 이외의 환경 글꼴 크기를 필요 합니다. 글꼴은 환경 글꼴이 보다 큰로 코딩 된 이전에 "`environment font +2`" 또는 유사한 합니다. 제공 된 코드 조각을 사용 하 여 높은 DPI 모니터 지원 되며 표시 텍스트에 올바른 크기 및 무게 (예: Light 또는 Semilight) 항상 표시 되는지 확인 합니다.

> [!NOTE]
> 서식 지정을 적용 하기 전에 확인 지침에 따르는 [텍스트 스타일](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle). * *

 환경 글꼴의 크기를 조정 하는 TextBlock 또는 Label 표시의 스타일을 설정 합니다. 이러한 코드 조각의 올바르게 사용 되는 각는 적절 한 크기 및 무게 변형을 포함 하 여 올바른 글꼴을 생성 합니다.

 여기서 "`vsui`" 네임 스페이스에 대 한 참조가 `Microsoft.VisualStudio.Shell`:

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

#### <a name="375-environment-font--light"></a>375% 환경 글꼴 + Light

**다음과 같이 나타납니다.** 34 pt Segoe UI Light

::: moniker range="vs-2017"

**사용:** (드물게) 고유한 브랜드 UI와 같은 시작 페이지

::: moniker-end

::: moniker range=">=vs-2019"

**사용:** (드물게) 고유한 브랜드 UI

::: moniker-end

**절차적 코드:** 여기서 `textBlock` 는 이전에 정의 된 textblock 및 `label` 은 이전에 정의 된 레이블입니다.

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);
```

**XAML:** TextBlock 또는 표시 된 것 처럼 레이블 스타일을 설정 합니다.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>
```

#### <a name="310-environment-font--light"></a>310% 환경 글꼴 + Light
 **다음과 같이 나타납니다.** 28 pt Segoe UI Light **사용:** 큰 서명 대화 상자 제목, 주 보고서의 제목

 **절차적 코드:** 여기서 `textBlock` 는 이전에 정의 된 textblock 및 `label` 은 이전에 정의 된 레이블입니다.

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);
```

 **XAML:** TextBlock 또는 표시 된 것 처럼 레이블 스타일을 설정 합니다.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>
```

#### <a name="200-environment-font--semilight"></a>200% 환경 글꼴 + Semilight
 **다음과 같이 나타납니다.** 18pt Segoe UI Semilight **사용:** 소규모 및 중간 규모 대화 상자에 제목, 부제목

 **절차적 코드:** 여기서 `textBlock` 는 이전에 정의 된 textblock 및 `label` 은 이전에 정의 된 레이블입니다.

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);
```

 **XAML:** TextBlock 또는 표시 된 것 처럼 레이블 스타일을 설정 합니다.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>
```

#### <a name="155-environment-font"></a>155% 환경 글꼴
 **다음과 같이 나타납니다.** 14pt Segoe UI **사용:** 문서의 섹션 제목 및 UI 또는 보고서

 **절차적 코드:** 여기서 `textBlock` 는 이전에 정의 된 textblock 및 `label` 은 이전에 정의 된 레이블입니다.

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);
```

 **XAML:** TextBlock 또는 표시 된 것 처럼 레이블 스타일을 설정 합니다.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>
```

#### <a name="133-environment-font"></a>133% 환경 글꼴
 **다음과 같이 나타납니다.** 12pt Segoe UI **사용:** 서명 대화 상자 및 문서에서 더 작은 부제목 및 UI

 **절차적 코드:** 여기서 `textBlock` 는 이전에 정의 된 textblock 및 `label` 은 이전에 정의 된 레이블입니다.

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);
```

 **XAML:** TextBlock 또는 표시 된 것 처럼 레이블 스타일을 설정 합니다.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>
```

#### <a name="122-environment-font"></a>122% 환경 글꼴
 **다음과 같이 나타납니다.** 11 pt Segoe UI **사용:** 서명 대화 상자에서 머리글 섹션, 세로 탭 탐색 트리 뷰에서 노드 최상위

 **절차적 코드:** 여기서 `textBlock` 는 이전에 정의 된 textblock 및 `label` 은 이전에 정의 된 레이블입니다.

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);
```

 **XAML:** TextBlock 또는 표시 된 것 처럼 레이블 스타일을 설정 합니다.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>
```

#### <a name="environment-font--bold"></a>환경 글꼴 + 굵게
 **으로 표시 됩니다:** 굵게 표시 된 9 pt Segoe UI **하는 데:** 레이블과 부제가 서명 대화 상자, 보고서 및 문서에도 UI

 **절차적 코드:** 여기서 `textBlock` 는 이전에 정의 된 textblock 및 `label` 은 이전에 정의 된 레이블입니다.

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironmentBoldStyleKey);
```

 **XAML:** TextBlock 또는 표시 된 것 처럼 레이블 스타일을 설정 합니다.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>
```

### <a name="localizable-styles"></a>지역화할 수 있는 스타일
 일부 경우에 지역화 담당자는 동아시아 언어에 대 한 텍스트에서 굵게 표시를 제거 하는 등의 다양 한 로캘에 대 한 글꼴 스타일을 수정 해야 합니다. 글꼴 스타일의 지역화를 가능 하 게 하려면 해당 스타일은.resx 파일 이어야 합니다. 이 작업을 수행 하 고 여전히 Visual Studio 폼 디자이너에서 글꼴 스타일을 편집 하는 최상의 방법은 명시적으로 디자인 타임에 글꼴 스타일을 설정 하는 것입니다. 전체 글꼴 개체를 만듭니다.이 부모 글꼴의 상속 것 처럼 보일 수 있지만 FontStyle 속성만 글꼴을 설정 하려면 사용 됩니다.

 솔루션은 연결 대화 상자 폼의 `FontChanged` 이벤트입니다. 에 `FontChanged` 이벤트 모든 컨트롤을 탐색 하 고 해당 글꼴 설정 되어 있는지 확인 합니다. 이 속성을 설정 하는 경우 폼의 글꼴 및 컨트롤의 이전 글꼴 스타일에 따라 새 글꼴을 변경 합니다. 코드에서이 예제는 다음과 같습니다.

```csharp
private void Form1_FontChanged(object sender, System.EventArgs e)
{
          SetFontStyles();
}

/// <summary>
/// SetFontStyles - This function will iterate all controls on a page
/// and recreate their font with the desired fontstyle.
/// It should be called in the OnFontChanged handler (and also in the constructor
/// in case the IUIService is not available so OnFontChange doesn't fire).
/// This way, when the VS shell font is given to us the controls that have
/// a different style for the font (bolded for example) will recreate their font
/// and use the VS shell font but with a style variation (bolded ...).
/// </summary>
protected void SetFontStyles()
{
     SetFontStyles(this, this, this.Font);
}

protected static void SetFontStyles(Control topControl, Control parent, Font referenceFont)
{
     foreach(Control c in parent.Controls)
     {
          if (c.Controls != null && c.Controls.Count > 0) {
               SetFontStyles(topControl, c, referenceFont);
          }
          if (c.Font != topControl.Font) {
               c.Font = new Font(referenceFont, c.Font.Style);
          }
     }
}
```

 이 코드를 사용 하는 폼의 글꼴 업데이트 되 면 컨트롤의 글꼴은 업데이트도 보장 합니다. 대화의 인스턴스를 가져오려면 실패할 수 있으므로이 메서드가 폼의 생성자에서 호출 되도록 수도 `IUIService` 하며 `FontChanged` 이벤트는 발생 하지 않습니다. 연결 `FontChanged` 대화 상자가 이미 열려 있는 경우에를 동적으로 새 글꼴 선택 대화 상자를 사용 하면 됩니다.

### <a name="testing-the-environment-font"></a>테스트 환경 글꼴
 UI 환경 글꼴을 사용 하는 하는 크기 설정을 위해 엽니다 **도구 > 옵션 > 환경 > 글꼴 및 색** 아래에서 "환경 글꼴"를 선택 하 고는 "설정 표시:" 드롭다운 메뉴입니다.

 ![도구에서 글꼴 및 색 설정을 &gt; 옵션 대화 상자](../../extensibility/ux-guidelines/media/0201-a_optionsfonts.png "a_OptionsFonts 0201")<br />도구에서 글꼴 및 색 설정을 &gt; 옵션 대화 상자

 기본값 보다 매우 다른 글꼴을 설정 합니다. 를 하 게 확실 한 UI를 업데이트 하지 않습니다는 세리프 (예: "Times New Roman")를 사용 하 여 글꼴을 선택 하 고 매우 큰 크기를 설정 합니다. 그런 다음 환경을 반영 하기 위해 UI를 테스트 합니다. 라이선스 대화 상자를 사용 하는 예제는 다음과 같습니다.

 ![환경 글꼴을 고려 하지 않습니다는 UI 텍스트 예가](../../extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "b_WrongFontDialog 0201")<br />환경 글꼴을 고려 하지 않는 UI 텍스트의 예

 이 경우 "사용자 정보" 및 "제품 정보" 글꼴을 존중 되지 됩니다. 명시적 글꼴 검토 사양의 일부로 지정 하지 않으면 버그 수 있지만 일부 경우가를 명시적으로 디자인 선택 될 수 있습니다.

 글꼴을 재설정 하려면 "기본값 사용"에서 클릭 **도구 > 옵션 > 환경 > 글꼴 및 색**합니다.

## <a name="BKMK_TextStyle"></a> 텍스트 스타일
 텍스트 스타일 글꼴 크기, 두께 및 대/소문자를 가리킵니다. 구현 지침은 [글꼴로](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)합니다.

### <a name="text-casing"></a>텍스트 대/소문자 구분

#### <a name="all-caps"></a>모두 대문자
 Visual Studio에서 레이블 또는 타이틀에 대 한 모든 대문자를 사용 하지 마세요.

#### <a name="all-lowercase"></a>모두 소문자
 사용 하지 마십시오 모두 소문자 제목 또는 Visual Studio의 레이블 지정에 대 한 합니다.

#### <a name="sentence-and-title-case"></a>문장 및 제목 대/소문자
 Visual Studio의 텍스트는 상황에 따라 문장 대/소문자 또는 첫 글자를 대문자로 사용 해야 합니다.

|에 대 한 첫 글자를 대문자로 사용 합니다.|에 대 한 문장 사례를 사용 합니다.|
|-------------------------|----------------------------|
|대화 상자 제목|레이블|
|그룹 상자|확인란|
|메뉴 항목|라디오 단추|
|컨텍스트 메뉴 항목|목록 상자 항목|
|단추|상태 표시줄|
|테이블 레이블||
|열 머리글||
|도구 설명||

##### <a name="title-case"></a>첫 글자를 대문자로
 첫 글자를 대문자로 대부분 또는 모든 구 내에서 단어의 첫 글자를 대문자로 작성 하는 스타일입니다. Visual Studio에서 첫 글자를 대문자로 비롯 한 여러 항목에 대 한 사용 됩니다.

- **Tooltips.** 예제: "선택한 항목 미리 보기"

- **열 헤더입니다.** 예제: "시스템 응답"

- **메뉴 항목입니다.** 예제: "모두 저장"

  첫 글자를 대문자로 사용 하는 경우 이러한은 단어를 활용 하는 경우 및 소문자 상태로 유지 하는 경우에 대 한 지침입니다.

|대문자|설명 및 예제|
|---------------|---------------------------|
|모든 명사||
|모든 동사|"Is" 및 "되려면 일"의 다른 폼을 포함 하 여|
|모든 부사|"보다" 및 "When"를 포함 하 여|
|모든 형용사|"That" 및 "This"를 포함 하 여|
|모든 대명사|소유격이 포함 하 여 "는"도 그대로","의 대명사 축약 "it" 동사 "이며"|
|품사에 관계 없이 첫 번째 및 마지막 단어||
|전치사 동사 구의 일부인|"모든 Windows 아웃 closing" 또는 "시스템 종료"|
|머리 글자어의 모든 문자|HTML, XML, URL, IDE, RGB|
|명사 또는 형용사 적절 한 경우 또는 동일한 가중치 단어 경우 두 번째 복합 단어에서 단어|상호 참조, 이전 Microsoft 소프트웨어의 경우 읽기/쓰기 액세스, 런타임|

|소문자|예|
|---------------|--------------|
|다른 음성 또는 첫 번째 단어를 수정 하는 분사 이면 복합 단어의 두 번째 단어|방법, 사용 해제|
|문서 제목에 첫 번째 단어 하나가 아닌 경우|a, an, the|
|접속사를 조정 합니다.|하지만, nor, 또는|
|동사 구 외부 네 개 이하인 문자의 전치사 단어를 사용 하 여|되기로 한의 상단에서의 출력|
|"To"는 그려야 하는지를 구를 사용 하는 경우|"하드 디스크를 포맷 하는 방법"|

##### <a name="sentence-case"></a>문장
 문장만 문장의 첫 번째 단어는 대문자로 시작에 명사와 대명사 작성 하기 위한 표준 대/소문자 메서드는 "I" 합니다. 일반적으로 문장 전세계 고객에 게 특히 경우 콘텐츠는 번역할 컴퓨터에 대 한 읽기 쉽습니다. 에 대 한 문장 사례를 사용 합니다.

1. **상태 표시줄 메시지입니다.** 상태 정보만 제공 이며 즉, 간단 하 게 됩니다. 예제: "프로젝트 파일을 로드"

2. **다른 모든 UI 요소의**, 레이블, 확인란, 라디오 단추 및 목록 상자 항목입니다. 예제: "목록의 모든 항목을 선택 합니다."

### <a name="text-formatting"></a>텍스트 서식 지정
 Visual Studio 2013의 서식 지정 하는 기본 텍스트에 의해 제어 됩니다 [글꼴로](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)합니다. 이 서비스는 IDE (통합된 개발 환경), 전체에서 일관 된 글꼴 모양이 표시 되도록 하 고 사용자에 게 일관 된 환경을 보장 하기 위해 사용 해야 합니다.

 Visual Studio 글꼴 서비스에서 사용 되는 기본 크기는 Windows에서 오며 9 (태평양 표준시)로 표시 됩니다.

 환경 글꼴 서식 지정을 적용할 수 있습니다. 이 항목에서는 방법 및 위치 스타일을 사용 하도록 합니다. 구현 정보에 대 한 참조 [글꼴로](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)합니다.

#### <a name="bold-text"></a>굵은 텍스트
 Visual Studio에서 자주 사용 됩니다 하 고에 예약 되어야 하는 굵은 텍스트:

- 마법사에서 질문 레이블

- 솔루션 탐색기에서 활성 프로젝트를 지정합니다.

- 속성 도구 창에서 재정의 된 값

- Visual Basic 편집기 드롭다운 목록에서 특정 이벤트

- 웹 페이지에 대 한 문서 개요의 서버에서 생성 된 콘텐츠

- 섹션 헤더 복잡 한 대화 또는 UI 디자이너

#### <a name="italics"></a>기울임꼴
 Visual Studio에서 기울임꼴 또는 굵게 기울임꼴 텍스트를 사용 하지 않습니다.

#### <a name="color"></a>색

- 파랑 (탐색 및 명령 실행)의 하이퍼링크에 대 한 예약 되어 있으므로 방향에 대해 사용 하지 말아야 합니다.

- 이러한 목적을 위해 더 큰 머리글 (환경 글꼴 x 155% 이상)를 색칠 할 수 있습니다.:

  - 눈에 띄는 서명 Visual Studio UI를 제공 합니다.

  - 특정 영역을 강조할

  - 표준 진한 회색/검은색 환경 텍스트 색의 릴리프를 제공 합니다.

- 머리글 색 기존 Visual Studio 브랜드 색 주 자주색 주로 #FF68217A 활용 해야 합니다.

- 머리글에서 색을 사용 하는 경우 따라야 합니다 [Windows 색 지침](/windows/desktop/uxguide/vis-color), 대비 비율은 등 다른 접근성 고려 합니다.

### <a name="font-size"></a>글꼴 크기
 Visual Studio UI 디자인 자세한 공백으로 밝은 모양을 갖추고 있습니다. 가능한 경우, chrome 및 제목 표시줄 감소 되거나 제거 되었습니다. 정보 밀도 Visual Studio에서 요구 사항 이지만, 입력 체계 개방적인 줄 간격 및 글꼴 크기 및 중량의 변형에 중점을 두어 중요 한 것으로 계속 됩니다.

 다음 표에서 디자인 세부 정보 및 Visual Studio에서 사용 되는 표시 글꼴에 대 한 시각적인 예가 포함 되어 있습니다. 일부 표시 글꼴 변형의 경우 크기와 Semilight 모양을에 코딩 광원 등의 가중치

 모든 표시 글꼴에 대 한 구현 코드 조각에서 확인할 수 있습니다 [(확장/굵게 표시) 참조를 서식 지정](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting)합니다.

#### <a name="375-environment-font--light"></a>375% 환경 글꼴 + Light

|||
|-|-|
|**사용법:** 드물게 발생 합니다. 고유한 브랜드 UI만 해당 합니다.<br /><br /> **수행 합니다.**<br /><br /> --문장의 첫 글자를 사용 하는 중<br />-간단한 항상 사용<br /><br /> **안 함:**<br /><br /> -사용 하 여 UI에 대 한 서명 시작 페이지와 같은 UI 이외의<br />-굵게, 기울임꼴 또는 굵게 기울임꼴<br />-본문 텍스트 사용<br />-도구 창에서 사용 합니다.|**다음과 같이 나타납니다.** 34 pt Segoe UI Light<br /><br /> **예를 보여 줍니다.**<br /><br /> *현재 사용 되지 않습니다. Visual Studio 2017 시작 페이지에서 사용할 수 있습니다.*|

#### <a name="310-environment-font--light"></a>310% 환경 글꼴 + Light

::: moniker range="vs-2017"

|||
|-|-|
|**사용법:**<br /><br /> -더 큰 서명 대화 상자 제목<br />-기본 보고서 제목<br /><br /> **수행 합니다.**<br /><br /> --문장의 첫 글자를 사용 하는 중<br />-간단한 항상 사용<br /><br /> **안 함:**<br /><br /> -사용 하 여 UI에 대 한 서명 시작 페이지와 같은 UI 이외의<br />-굵게, 기울임꼴 또는 굵게 기울임꼴<br />-본문 텍스트 사용<br />-도구 창에서 사용 합니다.|**다음과 같이 나타납니다.** 28 pt Segoe UI Light<br /><br /> **예를 보여 줍니다.**<br /><br /> ![310% 환경 글꼴의 예 &#43; Light 제목의](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202 a_EF310")|

::: moniker-end

::: moniker range=">=vs-2019"

|||
|-|-|
|**사용법:**<br /><br /> -더 큰 서명 대화 상자 제목<br />-기본 보고서 제목<br /><br /> **수행 합니다.**<br /><br /> --문장의 첫 글자를 사용 하는 중<br />-간단한 항상 사용<br /><br /> **안 함:**<br /><br /> -사용 하 여 UI에 대 한 서명 UI 이외의<br />-굵게, 기울임꼴 또는 굵게 기울임꼴<br />-본문 텍스트 사용<br />-도구 창에서 사용 합니다.|**다음과 같이 나타납니다.** 28 pt Segoe UI Light<br /><br /> **예를 보여 줍니다.**<br /><br /> ![310% 환경 글꼴의 예 &#43; Light 제목의](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202 a_EF310")|

::: moniker-end

#### <a name="200-environment-font--semilight"></a>200% 환경 글꼴 + Semilight

|||
|-|-|
|**사용법:**<br /><br /> -부제목<br />-대화 상자에서 소규모 및 중간 규모 제목<br /><br /> **수행 합니다.**<br /><br /> --문장의 첫 글자를 사용 하는 중<br />-항상 Semilight 가중치를 사용 하 여<br /><br /> **안 함:**<br /><br /> -굵게, 기울임꼴 또는 굵게 기울임꼴<br />-본문 텍스트 사용<br />-도구 창에서 사용 합니다.|**다음과 같이 나타납니다.** 18pt Segoe UI Semillight<br /><br /> **예를 보여 줍니다.**<br /><br /> ![200% 환경 글꼴의 예 &#43; Semilight](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202 b_EF200")|

#### <a name="155-environment-font"></a>155% 환경 글꼴

|||
|-|-|
|**사용법:**<br /><br /> 문서의 섹션 제목 및 UI<br />-보고서<br /><br /> **수행 합니다.** 문장의 첫 글자를 사용 합니다.<br /><br /> **안 함:**<br /><br /> -굵게, 기울임꼴 또는 굵게 기울임꼴<br />-본문 텍스트 사용<br />-표준 Visual Studio 컨트롤에서 사용 합니다.<br />-도구 창에서 사용 합니다.|**다음과 같이 나타납니다.** 14pt Segoe UI<br /><br /> **예를 보여 줍니다.**<br /><br /> ![155% 환경 글꼴 제목의 예](../../extensibility/ux-guidelines/media/0202-c_ef155.png "0202 c_EF155")|

#### <a name="133-environment-font"></a>133% 환경 글꼴

|||
|-|-|
|**사용법:**<br /><br /> 서명 대화 상자에서 더 작은 부제목<br />문서에서 더 작은 부제목 및 UI<br /><br /> **수행 합니다.** 문장의 첫 글자를 사용 합니다.<br /><br /> **안 함:**<br /><br /> -굵게, 기울임꼴 또는 굵게 기울임꼴<br />-본문 텍스트 사용<br />-표준 Visual Studio 컨트롤에서 사용 합니다.<br />-도구 창에서 사용 합니다.|**다음과 같이 나타납니다.** 12pt Segoe UI<br /><br /> **예를 보여 줍니다.**<br /><br /> ![133% 환경 글꼴 제목의 예](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202 d_EF133")|

#### <a name="122-environment-font"></a>122% 환경 글꼴

|||
|-|-|
|**사용법:**<br /><br /> 대화 상자에서 서명 섹션 제목<br />-트리 뷰에서 상위 노드<br />-세로 탭 탐색<br /><br /> **수행 합니다.** 문장의 첫 글자를 사용 합니다.<br /><br /> **안 함:**<br /><br /> -굵게, 기울임꼴 또는 굵게 기울임꼴<br />-본문 텍스트 사용<br />-표준 Visual Studio 컨트롤에서 사용 합니다.<br />-도구 창에서 사용 합니다.|**다음과 같이 나타납니다.** 11 pt Segoe UI<br /><br /> **예를 보여 줍니다.**<br /><br /> ![122% 환경 글꼴 제목의 예](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202 e_EF122")|

#### <a name="environment-font--bold"></a>환경 글꼴 + 굵게

|||
|-|-|
|**사용법:**<br /><br /> -레이블 및 서명 대화 상자에서 부제목<br />-레이블 및 보고서의 부제목<br />-레이블 및 문서의 부제목이 있는 변경과 UI<br /><br /> **수행 합니다.**<br /><br /> --문장의 첫 글자를 사용 하는 중<br />--굵게 두께 사용 하는 중<br /><br /> **안 함:**<br /><br /> -기울임꼴 또는 굵게 기울임꼴<br />-본문 텍스트 사용<br />-표준 Visual Studio 컨트롤에서 사용 합니다.<br />-도구 창에서 사용 합니다.|**으로 표시 됩니다:** 굵게 표시 된 9 pt Segoe UI<br /><br /> **예를 보여 줍니다.**<br /><br /> ![환경 글꼴의 예 &#43; 굵게 제목의](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202 f_EFB")|

#### <a name="environment-font"></a>환경 글꼴

|||
|-|-|
|**사용법:** 다른 모든 텍스트<br /><br /> **수행 합니다.** 문장의 첫 글자를 사용 합니다.<br /><br /> **안 함:** 기울임꼴 또는 굵게 기울임꼴|**다음과 같이 나타납니다.** 9 (태평양 표준시) Segoe UI<br /><br /> **예를 보여 줍니다.**<br /><br /> ![환경 글꼴의 예](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202 g_EF")|

### <a name="padding-and-spacing"></a>안쪽 여백 및 간격
 머리글에는 적절 한 강조를 제공 하도록 주위에 공간이 필요 합니다. 이 공간은 포인트 크기 및 다른 새로운 수평선 등 환경 글꼴의 텍스트 줄을 머리글 근처에 따라 달라 집니다.

- 이상적인 자체로 머리글 안쪽 여백을 자본 문자 높이 공간의 90% 여야 합니다. 예를 들어, 28 pt Segoe UI Light 제목을 26 pt cap 높이 있고 23 pt 또는 약 31 픽셀 안쪽 여백을 약 있어야 합니다.

- 제목 주위에 최소 공간 자본 문자 높이의 50% 이어야 합니다. 머리글을 함께 다른 긴밀 하 게 맞춤 요소나 규칙을 더 적은 공간을 사용할 수 있습니다.

- 환경 글꼴 텍스트 굵게 표시 된 기본 줄 높이 간격 및 안쪽 여백 따라야 합니다.

## <a name="see-also"></a>참고자료

- [MSDN: 글꼴 (Windows)](/windows/desktop/uxguide/vis-fonts)
- [MSDN: 사용자 인터페이스 텍스트 (Windows)](/windows/desktop/uxguide/text-ui)
