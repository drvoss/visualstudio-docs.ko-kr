---
title: 색 및 스타일 지정
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 257c5944ee1939849c4163fef518abf513183998
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68177026"
---
# <a name="colors-and-styling-for-visual-studio"></a>색 및 Visual Studio에 대 한 스타일 지정
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="using-color-in-visual-studio"></a>Visual Studio에서 색을 사용 하 여
 Visual Studio에서 색 장식 뿐만 아니라 통신 도구는 기본적으로 사용 됩니다. 최소 색을 사용 하 고 하려는 상황에 대 한 예약 합니다.

- 통신 의미 또는 정보 (예: 플랫폼 또는 언어 한정자)

- (예: 상태 표시) 주의 유치

- 가독성을 향상 하 고 UI를 탐색 하기 위한 랜드마크 제공

- 증가 요구 적합성

  Visual Studio에서 UI 요소에 색을 할당 하기 위한 몇 가지 옵션이 있습니다. 경우에 따라 그림 어려울 수 있습니다 올바르게 사용 하는 방법 또는 옵션 아웃 할 수를 사용 합니다. 이 항목에서는 사용 하는 데 도움이 됩니다.

1. 다른 서비스 및 Visual Studio에서 색을 정의 하는 데 사용 하는 시스템을 이해 합니다.

2. 지정된 된 요소에 대 한 올바른 옵션을 선택 합니다.

3. 선택한 옵션을 올바르게 사용 합니다.

   **중요:** 하드 코드 16 진수, RGB 또는 UI 요소에 시스템 색 하지 않습니다. 서비스를 사용 하 여 hue 튜닝의 유연성을 허용 합니다. 또한 서비스 없이 수 없게 됩니다의 테마 전환 기능을 활용 하는 [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)합니다.

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Visual Studio 인터페이스 요소에 색을 할당 하기 위한 메서드
 UI 요소에 가장 적합 한 방법을 선택 합니다.

|UI|메서드|인가요?|
|-------------|------------|--------------------|
|삽입 또는 독립 실행형 대화 상자.|**시스템 색**|운영 체제와 같은 UI 요소의 모양과 색을 공용 대화 상자 컨트롤에 대 한 정의를 허용 하는 시스템 이름입니다.|
|전체 VS 환경과 일관성을 유지 하려는 사용자 지정 UI와 범주 및 공유 토큰의 의미 체계 의미를 일치 하는 UI 요소에 게 있습니다.|**일반적인 공유 색**|특정 UI 요소에 대 한 기존 미리 정의 된 색 토큰 이름|
|개별 기능 또는 기능 그룹 이며 유사한 요소에 대 한 공유 색 없음.|**사용자 지정 색**|영역 관련 되어 있으며 다른 UI를 사용 하 여 공유 하려고 하지는 색 토큰 이름|
|최종 사용자가 사용자 지정 UI 또는 콘텐츠 (예를 들어, 텍스트 편집기 또는 특수 한 디자이너 창)를 허용 하려고 합니다.|**최종 사용자가 사용자 지정**<br /><br /> **(도구 > 옵션 대화 상자)**|"글꼴 및 색" 페이지에 정의 된 설정 합니다 **도구 > 옵션** 대화 또는 특정 한 UI 기능에 특수 한 페이지입니다.|

### <a name="visual-studio-themes"></a>Visual Studio 테마
 Visual Studio의 세 가지 서로 다른 색 테마 기능: 밝게, 어둡게, 및 파란색입니다. 또한 내게 필요한 옵션에 대 한 설계 된 시스템 색 테마를 고대비 모드를 검색 합니다.

 사용자가 Visual Studio의 첫 번째 용도 테마를 선택 하 라는 메시지가 표시 됩니다 및로 이동 하 여 나중에 테마를 전환할 수 있는 **도구 > 옵션 > 환경 > 일반** "색 테마" 드롭다운 메뉴에서 새 테마를 선택 합니다.

 사용자가 여러 고대비 테마 중 하나에 전체 시스템을 전환 하려면 제어판을 이용할 수 있습니다. 사용자가 고대비 테마를 선택 하는 경우 다음 Visual Studio 색 테마 선택기 더 이상 영향을 줍니다 Visual Studio에서 색을 있지만 고대비 모드를 종료 하는 사용자에 대 한 모든 테마 변경 내용이 저장 됩니다. 고대비 모드에 대 한 자세한 내용은 참조 하십시오 [선택 고대비 색](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors)합니다.

### <a name="the-vscolor-service"></a>VSColor service
 Visual Studio는 각 Visual Studio 테마에 대 한 색 값이 포함 된 명명된 된 항목의 UI 요소 색상 값에 바인딩할 수 있는 VSColor 서비스 라고 하는 환경 색 서비스를 제공 합니다. 이렇게 하면 색을 현재 사용자가 선택한 테마 또는 시스템 고대비 모드를 반영 하도록 자동으로 변경 됩니다. 사용 하 여 서비스의 모든 색 테마와 관련 된 변경의 구현을 한 곳에서 처리 됩니다 UI 이후 버전의 Visual Studio에서 새 테마를 자동으로 반영 됩니다 서비스에서 일반적인 공유 색을 사용 하는 경우 있음을 의미 합니다.

### <a name="implementation"></a>구현
 Visual Studio 소스 코드는 토큰 이름 및 각 테마에 대해 각 색상 값의 목록이 포함 된 여러 패키지 정의 파일을 포함 합니다. 색 서비스는 이러한 패키지 정의 파일에 정의 된 VSColors를 읽습니다. 이러한 색 코드 또는 XAML 태그에서 참조 되며 다음 중 하나를 통해 로드 된 **IVsUIShell5.GetThemedColor** 메서드나 DynamicResource 매핑.

### <a name="system-colors"></a>시스템 색
 공용 컨트롤 기본적으로 시스템 색을 참조 합니다. UI를 포함 되거나 독립 실행형 대화 상자를 만들 때와 같은 시스템 색 사용 하려는 경우에 아무 작업도 수행할 필요가 없습니다.

### <a name="common-shared-colors-in-the-vscolor-service"></a>VSColor service의 일반적인 공유 색
 사용자 인터페이스 요소에는 전체 Visual Studio 환경을 반영 해야 합니다. 디자인할 UI 구성 요소에 대 한 적합 한 일반적인 공유 색을 다시 사용 하 여 사용자 인터페이스는 다른 Visual Studio 인터페이스를 사용 하 여 일치 하 고 테마 추가 되거나 업데이트 되 면 색은 자동으로 업데이트를 확인 합니다.

 일반적인 공유 색을 사용 하기 전에 올바르게 사용 하는 방법을 이해 해야 합니다. 일반적인 공유 색을 잘못 사용 하면 사용자가 일치 하지 않는, 불편, 또는 혼란 스러운 환경에서 발생할 수 있습니다.

### <a name="user-customizable-colors"></a>사용자 지정 가능한 색
 참조 [최종 사용자에 대 한 색을 노출합니다.](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

 경우에 따라 최종 사용자가 코드 편집기 또는 디자인 화면을 만들 때와 같은 UI를 사용자 지정할 수 있도록 해야 합니다. 사용자 지정 가능한 UI 구성 요소에서 발견 되는 **글꼴 및 색** 섹션을 **도구 > 옵션** 전경색, 배경색, 또는 둘 다를 변경 하려면 사용자가 선택할 수 있는 대화 상자에서.

 ![도구 &#62; Visual Studio의 옵션 대화 상자](../../extensibility/ux-guidelines/media/0301-a-toolsoptionsdialog.png "a_ToolsOptionsDialog 0301")

 **도구 > 옵션 대화 상자**

## <a name="BKMK_TheVSColorService"></a> VSColor Service
 Visual Studio VSColor service 또는 셸 색 서비스 라고도 하는 환경 색 서비스를 제공 합니다. 이 서비스를 사용 하면 각 테마에 대 한 색을 포함 하는 집합 이름-값 색에 UI 요소의 색 값을 바인딩할 수 있습니다. 색이 자동으로 현재 사용자가 선택한 테마에 맞게 변경 되 고 UI 환경 색 서비스에 바인딩된 있도록는 통합 새 테마를 사용 하 여 이후 버전의 Visual Studio VSColor service 모든 UI 요소에 대해 사용 되어야 합니다.

### <a name="how-the-service-works"></a>서비스의 작동 방식
 환경 색 서비스 VSColors UI 구성 요소에 대 한.pkgdef의 정의 읽습니다. 이러한 VSColors XAML 태그 또는 코드에서 참조 한 다음 되 고 중 하나를 통해 로드 되는 **IVsUIShell5.GetThemedColor** 또는 DynamicResource 매핑.

 ![환경 색 서비스 아키텍처](../../extensibility/ux-guidelines/media/0302-a-environmentcolorservicearchitecture.png "0302 a_EnvironmentColorServiceArchitecture")

 **환경 색 서비스 아키텍처**

### <a name="accessing-the-service"></a>서비스에 액세스
 어떤 종류의 색 토큰 수에 따라 VSColor service를 사용 하는 액세스 및 설치 된 코드의 종류는 여러 가지가 있습니다.

#### <a name="predefined-environment-colors"></a>미리 정의 된 환경 색

##### <a name="from-native-code"></a>네이티브 코드에서
 셸은 COLORREF 색의에 대 한 액세스를 제공 하는 서비스를 제공 합니다. 서비스/인터페이스 다음과 같습니다.

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

 파일 VSShell80.idl, 열거형 **__VSSYSCOLOREX** 셸 색 상수에 있습니다. 사용 하 여 MSDN에 설명 된 열거형 __VSSYSCOLOREX 값 중 하나는 인덱스 값 또는 일반 인덱스를 Windows 시스템 API를 제공 하는 숫자에 전달할 **GetSysColor**를 허용 합니다. 이 작업을 수행할 두 번째 매개 변수에서 사용 해야 하는 색의 RGB 값을 다시 가져옵니다.

 펜 또는 새 색을 사용 하 여 브러시를 저장 하는 경우 AdviseBroadcastMessages (Visual Studio 셸)에서 하며 WM_SYSCOLORCHANGE 및 WM_THEMECHANGED 메시지를 수신 합니다.

```
// To access the color service in native code, you'll make a call that resembles this:
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);

```

 **참고:** 반환한 COLORREF 값 **GetVSSysColorEx()** 포함 방금 R, G, B 부분은 테마 색을 합니다. 테마 항목 투명도 사용 하는 경우에 알파 채널 값을 반환 하기 전에 삭제 됩니다. 따라서 관심 환경 색에 투명도 채널은 중요 한 위치를 대신 사용할 해야 하는 경우이 항목의 뒷부분에 설명 된 대로 IVsUIShell2::GetVSSysColorEx, 대신 IVsUIShell5.GetThemedColor 사용 해야 있습니다.

##### <a name="from-managed-code"></a>관리 코드에서
 네이티브 코드를 통해 VSColor service에 액세스 하는 것은 매우 간단 합니다. 그러나 관리 되는 코드를 통해 작업 하는 경우 서비스를 사용 하는 방법을 결정 하기 까다로울 수 있습니다. 이 점을 염두에서를 사용 하 여이 프로세스를 보여 주는 C# 코드 조각은 다음과 같습니다.

```
private void VSColorPaint(object sender, System.Windows.Forms.PaintEventArgs e)
{
    //getIVSUIShell2
    IVsUIShell2 uiShell2 = Package.GetService(typeof(SVsUIShell)) as IVsUIShell2;
    Debug.Assert (uiShell2 != null, "failed to get IVsUIShell2");

    if (uiShell2 != null)
    {
        //get the COLORREF structure
        uint win32Color;
        uiShell.GetVSSysColorEx(VSSYSCOLOREX.VSCOLOR_SMARTTAG_HOVER_FILL, out win32Color);

        //translate it to a managed Color structure
        Color myColor = ColorTranslator.FromWin32((int)win32Color);
        //use it
        e.Graphics.FillRectangle(new SolidBrush(myColor), 0, 0, 100, 100);
    }
}
```

 Visual Basic에서 작업 하는 경우 사용 합니다.

```
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)
```

##### <a name="from-wpf-ui"></a>WPF UI에서
 응용 프로그램의 ResourceDictionary를 내보낸 값을 통해 Visual Studio 색에 바인딩할 수 있습니다. 다음은 XAML의 환경 글꼴 데이터를 바인딩할 수 있을 뿐만 아니라 리소스 색상표를 사용 하는 예제입니다.

```
<Style TargetType="{x:Type Button}">
    <Setter Property="TextBlock.FontFamily"
            Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
    <Setter Property="TextBlock.FontSize"
            Value="{DynamicResource VsFont.EnvironmentFontSize}" />
    <Setter Property="Background"
            Value="{DynamicResource VsBrush.EnvironmentBackgroundGradient}" />
</Style>
```

#### <a name="helper-classes-and-methods-for-managed-code"></a>관리 코드에 대 한 메서드와 도우미 클래스
 관리 코드에 대해 셸의 관리 패키지 프레임 워크 라이브러리 (Microsoft.VisualStudio.Shell.12.0.dll) 몇 가지 테마가 지정 된 색의 사용을 촉진 하는 도우미 클래스를 포함 합니다.

 도우미 메서드를 **Microsoft.VisualStudio.Shell.VsColors** MPF 클래스 포함 **GetThemedGDIColor()** 하 고 **GetThemedWPFColor()** . 이러한 도우미 메서드는 System.Drawing.Color 또는 System.Windows.Media.Color, WinForms 또는 WPF UI에서 사용할 테마 항목의 색 값을 반환 합니다.

```
IVsUIShell5 shell5;
Button button = new Button();
button.BackColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemBrushKey);
button.ForeColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemTextBrushKey);

/// <summary>
/// Gets a System.Drawing.Color value from the current theme for the given color key.
/// </summary>
/// <param name="vsUIShell">The IVsUIShell5 service, used to get the color's value.</param>
/// <param name="themeResourceKey">The key to find the color for.</param>
/// <returns>The current theme's value of the named color.</returns>
public static System.Drawing.Color GetThemedGDIColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Validate.IsNotNull(vsUIShell, "vsUIShell");
   Validate.IsNotNull(themeResourceKey, "themeResourceKey");

   byte[] colorComponents = GetThemedColorRgba(vsUIShell, themeResourceKey);

   // Note: The Win32 color we get back from IVsUIShell5.GetThemedColor is ABGR
   return System.Drawing.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]);
}

private static byte[] GetThemedColorRgba(IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Guid category = themeResourceKey.Category;
   __THEMEDCOLORTYPE colorType = __THEMEDCOLORTYPE.TCT_Foreground
   if (themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundColor || themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundBrush)
   {
      colorType = __THEMEDCOLORTYPE.TCT_Background;
   }

   // This call will throw an exception if the color is not found
   uint rgbaColor = vsUIShell.GetThemedColor(ref category, themeResourceKey.Name, (uint)colorType);
   return BitConverter.GetBytes(rgbaColor);
}
public static System.Windows.Media.Color GetThemedWPFColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Validate.IsNotNull(vsUIShell, "vsUIShell");
   Validate.IsNotNull(themeResourceKey, "themeResourceKey");

   byte[] colorComponents = GetThemedColorComponents(vsUIShell, themeResourceKey);

    return System.Windows.Media.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]);
}

```

 지정 된 WPF 색 리소스 키에 대 한 VSCOLOR 식별자를 가져오려면 클래스를 사용할 수도 있습니다 또는 그 반대의 경우도 마찬가지입니다.

```
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

 메서드 **VsColors** 클래스 VSColor service 호출 될 때마다 색 값을 반환 하도록 쿼리 합니다. 로 색 값을 얻으려면 **System.Drawing.Color**, 향상 된 성능 대 안으로 대신의 메서드를 사용 하는 것은 **Microsoft.VisualStudio.PlatformUI.VSThemeColor** 클래스는 캐시 VSColor service에서 가져온 색 값입니다. 클래스는 내부적으로 셸에서 브로드캐스트 메시지 이벤트를 구독할 하 고 테마 변경 이벤트가 발생할 때 캐시 된 값을 무시 합니다. 또한이 클래스는 제공 된 합니다. 테마 변경 구독할 NET 친화적인 이벤트입니다. 사용 하 여는 **ThemeChanged** 새 처리기를 추가 하 고 사용 하는 이벤트를 **GetThemedColor()** 색을 가져오는 방법에 대 한 값을 **ThemeResourceKeys** 관심. 샘플 코드는 다음과 같습니다.

```
public MyWindowPanel()
{
    InitializeComponent();

    // Subscribe to theme changes events so we can refresh the colors
    VSColorTheme.ThemeChanged += VSColorTheme_ThemeChanged;

    RefreshColors();
}

private void VSColorTheme_ThemeChanged(ThemeChangedEventArgs e)
{
    RefreshColors();

    // Also post a message to all the children so they can apply the current theme appropriately
    foreach (System.Windows.Forms.Control child in this.Controls)
    {
        NativeMethods.SendMessage(child.Handle, e.Message, IntPtr.Zero, IntPtr.Zero);
    }
}

private void RefreshColors()
{
    this.BackColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowBackgroundColorKey);
    this.ForeColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowTextColorKey);
}

protected override void Dispose(bool disposing)
{
    if (disposing)
    {
        VSColorTheme.ThemeChanged -= this.VSColorTheme_ThemeChanged;
        base.Dispose(disposing);}
}
```

## <a name="BKMK_ChoosingHighContrastColors"></a> 고대비 색 선택

### <a name="overview"></a>개요
 Windows 보다 분명 화면에 표시 되는 요소, 배경, 텍스트 및 이미지의 색상 대비를 증가 시키는 여러 고대비 시스템 수준 테마를 사용 합니다. 내게 필요한 옵션의 이유로 반드시 사용자가 고대비 테마를 전환할 때 Visual Studio 인터페이스 요소 올바르게 응답 합니다.

 고대비 테마에 대 한 시스템 색의 일부만 사용할 수 있습니다. 시스템 색 이름을 선택할 때 다음 팁을 기억해 야 합니다.

1. **동일한 의미 체계 의미를 갖는 시스템 색 선택** 색 지정 되는 요소와 합니다. 예를 들어 창 내에서 텍스트에 대 한 고대비 색을 선택 하는 경우 WindowText 및 없습니다 ControlText를 사용 합니다.

2. **전경/배경 쌍 선택** 함께 또는 색 선택한 모든 고대비 테마에서 작동 하는지 확신할 수 없습니다.

3. **가장 중요 한 UI 부분 확인 하 고 콘텐츠 영역 차별화를 확인 합니다.** 다른 콘텐츠 영역에 대 한 색상 변형이 있습니다 때문에 강력한 테두리 색을 사용 하 여 콘텐츠 영역을 정의 하는 공용 이므로 한 색상의 미묘한 차이, 일반적으로 구분 하는 세부 정보가 손실 됩니다.

### <a name="system-color-set"></a>시스템 색 집합
 테이블에 [WPF 팀 블로그: SystemColors 참조](http://blogs.msdn.com/b/wpf/archive/2010/11/30/systemcolors-reference.aspx) 시스템 색 이름 및 각 테마에 표시 된 해당 색상의 전체 집합을 나타냅니다.

 UI, 색 집합을 제한이 적용 될 때 *"일반" 테마에서 표시 된 미묘한 세부 정보를 잃게 될*합니다. 도구 창 내에서 영역을 구분 하는 데 사용 되는 미묘한 회색 색을 사용 하 여 UI의 예는 다음과 같습니다. 고대비 모드에서 표시 하는 동일한 창을 함께 사용 하면 모든 배경 색상을 나타내는 동일한를 해당 영역의 테두리 테두리 단독으로 표시 됩니다을 확인할 수 있습니다.

 ![속성 창](../../extensibility/ux-guidelines/media/030303-a-propertieswindow.png "030303 a_PropertiesWindow")

 **어떻게 미묘한 세부 정보의 예제가 고대비에서 손실 됩니다.**

#### <a name="choosing-text-colors-in-an-editor"></a>편집기에서 텍스트 색을 선택합니다.
 컬러로 텍스트는 유사 항목 그룹의 쉽게 식별할 수 있도록 허용 하는 등의 의미를 나타내려면 편집기 또는 디자인 화면에서 사용 됩니다. 그러나 고대비 테마에서 필요가 없습니다 세 개 이상의 텍스트 색을 구분할 수 있습니다. WindowText, GrayText HotTrackText와 WindowBackground 화면에서 사용할 수 있는 유일한 색입니다. 4 가지 이상의 색을 사용할 수 없으므로 신중 하 게 고대비 모드에 있을 때 표시 하려는 가장 중요 한 차이점을 선택 합니다.

 각 고대비 테마에 표시 되는 편집기 화면에서 허용 하는 토큰 이름 각각에 대 한 색상:

 ![고대비 편집기 비교](../../extensibility/ux-guidelines/media/030303-b-hceditorcomparison.png "030303 b_HCEditorComparison")

 **고대비 편집기 비교**

 파란색 테마의 편집기 화면을의 예:

 ![파란색 테마의 편집기](../../extensibility/ux-guidelines/media/030303-c-editorblue.png "030303 c_EditorBlue")

 **파란색 테마의 편집기**

 ![고대비 테마의 편집기](../../extensibility/ux-guidelines/media/030303-d-editorhc1.png "030303 d_EditorHC1")

 **고대비 #1 테마의 편집기**

### <a name="usage-patterns"></a>사용 패턴
 많은 일반적인 UI 요소에 이미 정의 된 고대비 색입니다. 참조할 수 있습니다 이러한 사용 패턴 색 이름을 사용자 고유의 시스템을 선택할 때 UI 요소는 비슷한 구성 요소와 일치 합니다.

|시스템 색|사용|
|------------------|-----------|
|ActiveCaption|-현재 IDE 및 rafted 창 단추 가리키기 및 키를 눌러 문자 모양<br />IDE 및 rafted windows에 대 한 제목 표시줄 배경<br />기본 상태 표시줄 배경|
|ActiveCaptionText|-현재 IDE 및 rafted 창의 제목 표시줄 전경 (텍스트 및 문자 모양)<br />-배경 및 테두리 hover에 키를 눌러 활성 창 단추|
|컨트롤|-기본 및 드롭다운 단추를 포함 하 여 사용할 수 없는 백그라운드 콤보 상자, 드롭다운 목록 및 검색 컨트롤<br />--대상 단추 배경을 도킹 하는 중<br />명령 모음 배경<br />도구 창 배경|
|ControlDark|-IDE 배경<br />메뉴 및 명령 모음 구분 기호<br />명령 모음 테두리<br />메뉴 그림자<br />-도구 창 탭 기본 및 가리킨 항목 테두리 및 구분 기호<br />-문서 오버플로 단추 배경을<br />-도킹 대상 문자 모양 테두리|
|ControlDarkDark|-포커스가 없는 선택한 문서 탭 창|
|ControlLight|-자동 숨기기 탭 테두리<br />-콤보 상자 및 드롭다운 목록 테두리<br />-대상 배경 및 테두리 도킹|
|ControlLightLight|-선택한 포커스가 있는 provisional 테두리|
|ControlText|-콤보 상자 및 드롭다운 목록 문자 모양<br />도구 창 선택 하지 않은 탭 텍스트|
|GrayText|-테두리, 드롭다운 문자 모양, 텍스트 및 메뉴 항목 텍스트 콤보 상자 및 드롭다운 목록을 사용 안 함<br />-비활성화 된 메뉴 텍스트<br />검색 컨트롤 '검색 옵션' 헤더 텍스트<br />검색 컨트롤 섹션 구분 기호|
|Highlight|-All 놓고 배경, 테두리, 콤보 상자 드롭다운을 제외 하 고 누른 단추 배경 및 문서도 오버플로 단추 테두리<br />-선택한 항목 배경|
|HighlightText|-모든 가리키기 및 누름된 foregrounds (텍스트 및 문자 모양)<br />-포커스가 있는 도구 창과 문서 탭 창 컨트롤 전경<br />-포커스가 있는 도구 창 제목 표시줄 테두리<br />--임시 탭 포커스가 있는, 선택한 전경<br />Hover에 키를 눌러 문서 잘 오버플로 단추 테두리<br />-선택한 아이콘 테두리|
|HotTrack|-Scrollbar의 thumb 배경 및 테두리 누를<br />-누를 스크롤 막대 화살표 문자 모양|
|InactiveCaption|-비활성 IDE 및 rafted 창 단추 문자 모양 가리키기<br />IDE 및 rafted windows에 대 한 제목 표시줄 배경<br />-컨트롤 배경에 검색 사용 안 함된|
|InactiveCaptionText|-비활성 IDE 및 rafted windows 제목 표시줄 전경색 (텍스트 및 문자 모양)<br />-비활성 창 단추가 배경과 테두리가 가리키기<br />-포커스가 없는 도구 창 단추 배경 및 테두리<br />-사용 안 함된 검색 컨트롤 전경|
|메뉴|-드롭다운 메뉴 배경<br />-Checked 및 사용 안 함 확인 표시 배경|
|MenuText|-드롭다운 메뉴 테두리<br />-확인 확인<br />메뉴 문자 모양<br />-드롭 다운 메뉴 텍스트<br />-선택한 아이콘 테두리|
|스크롤 막대|-Scrollbar와 스크롤 막대 화살표 백그라운드 모든 상태|
|창|-자동 숨기기 탭 배경<br />메뉴 모음 및 명령 선반 배경에<br />-포커스가 없는 또는 선택 되지 않은 문서 창 탭 배경 및 열기 및 임시 탭에 대 한 문서 테두리<br />-포커스가 없는 도구 창 제목 표시줄 배경<br />도구 창 탭 배경, 선택 및 선택 취소|
|WindowFrame|-IDE 테두리|
|WindowText|-자동 숨기기 탭 전경<br />-선택한 도구 창 탭 전경<br />-포커스가 없는 문서 창의 탭 및 포커스 없음 또는 선택 취소-임시 탭 전경<br />-트리 보기 기본 전경 가리키기 선택 하지 않은 문자 위로<br />도구 창 선택된 된 탭 테두리<br />-Scrollbar의 thumb 배경, 테두리 및 문자 모양|

## <a name="BKMK_ExposingColorsForEndUsers"></a> 최종 사용자에 대 한 색을 노출합니다.

### <a name="overview"></a>개요
 경우에 따라 최종 사용자가 코드 편집기 또는 디자인 화면을 만들 때와 같은 UI를 사용자 지정할 수 있도록 해야 합니다. 이 작업을 수행 하는 가장 일반적인 방법은 사용 하는 것은 **도구 > 옵션** 대화 합니다. 통해 사용자 지정을 제공 하는 가장 쉬운 방법은 특수 한 컨트롤을 필요로 하는 UI 매우 특수화 된 경우가 아니면 합니다 **글꼴 및 색** 내에서 페이지를 **환경** 섹션 대화 상자. 사용자 지정에 대 한 노출 하는 각 요소에 대해 사용자는 전경색, 배경색, 또는 둘 다를 변경 하도록 선택할 수 있습니다.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>사용자 지정 가능한 색에 대 한 VSPackage를 빌드
 VSPackage는 글꼴 및 색 사용자 지정 범주를 통해 제어 하 고 글꼴 및 색 속성 페이지에서 항목을 표시할 수 있습니다. 이 메커니즘을 사용 하는 경우 Vspackage를 구현 해야 합니다 [IVsFontAndColorDefaultsProvider](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.aspx) 인터페이스와 해당 관련된 인터페이스입니다.

 원칙적으로이 메커니즘 모든 기존 항목을 포함 하는 범주를 수정 하려면 사용할 수 있습니다. 그러나이 해서는 안 텍스트 편집기 범주 또는 해당 표시 항목을 수정 합니다. 텍스트 편집기 범주에 대 한 자세한 내용은 참조 하세요. [글꼴 및 색 개요](https://msdn.microsoft.com/library/bb165065.aspx)합니다.

 VSPackage를 사용자 지정 범주를 구현 하거나 항목을 표시 하려면 다음을 해야 합니다.

- **만들거나 레지스트리에서 범주를 식별 합니다.** IDE의 구현의 합니다 **글꼴 및 색** 속성 페이지에서이 정보를 사용 하 여 올바르게 지정된 된 범주를 지 원하는 서비스에 대 한 쿼리 합니다.

- **만들거나 레지스트리 (선택 사항)에서 그룹을 식별 합니다.** 두 개 이상 범주의 합집합을 나타내는 그룹을 정의 하면 유용할 수 있습니다. 그룹을 정의 하는 경우 IDE 자동으로 하위 범주를 병합 한이 그룹 내에서 표시 항목을 배포 합니다.

- **IDE 지원을 구현 합니다.**

- **글꼴 및 색 변경 내용을 처리 합니다.**

#### <a name="to-create-or-identify-categories"></a>만들거나 범주를 식별 합니다.
 특수 한 유형의 범주 아래에 레지스트리 항목 구성 [HKLM\SOFTWARE\Microsoft \Visual Studio\\< Visual Studio 버전\>\FontAndColors\\< 범주\>]. \<범주 > 범주의 지역화 되지 않은 이름입니다.

 두 값을 사용 하 여 레지스트리를 채웁니다.

|이름|형식|보기|설명|
|----------|----------|----------|-----------------|
|범주|REG_SZ|GUID|범주를 식별 하는 GUID 생성|
|패키지|REG_SZ|GUID|범주를 지 원하는 VSPackage 서비스의 GUID|

 레지스트리에 지정 된 서비스의 구현을 제공 해야 합니다 [IVsFontAndColorDefaults](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) 해당 범주에 대 한 합니다.

#### <a name="to-create-or-identify-groups"></a>그룹을 만들거나 식별 하려면
 특수 한 유형의 범주 아래에 레지스트리 항목 구성 [HKLM\SOFTWARE\Microsoft \Visual Studio\\< Visual Studio 버전\>\FontAndColors\\< 그룹\>]. \<그룹 > 그룹의 지역화 되지 않은 이름입니다.

 두 값을 사용 하 여 레지스트리를 채웁니다.

|이름|형식|보기|설명|
|----------|----------|----------|-----------------|
|범주|REG_SZ|GUID|범주를 식별 하는 GUID 생성|
|패키지|REG_SZ|GUID|범주를 지 원하는 VSPackage 서비스의 GUID|

 레지스트리에 지정 된 서비스의 구현을 제공 해야 합니다 **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** 해당 그룹에 대 한 합니다.

 ![IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a-fontandcolorgroup.png "0304-a_FontAndColorGroup")

### <a name="to-implement-ide-support"></a>IDE 지원 기능을 구현 하려면
 구현 [GetObject](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject.aspx)를 반환 하는 [IVsFontAndColorDefaults](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) 인터페이스 또는 **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** 각 범주 또는 그룹 GUID가 제공을 위한 ide 인터페이스입니다.

 VSPackage 지 원하는 모든 범주에 대 한 별도의 인스턴스를 구현 합니다 [IVsFontAndColorDefaults](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) 인터페이스입니다.

 메서드를 통해 구현 [IVsFontAndColorDefaults](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) 사용 하 여 IDE를 제공 해야 합니다.

- 범주의 표시 항목 목록

- 표시 항목에 대 한 지역화할 수 있는 이름

- 범주의 각 멤버에 대 한 정보를 표시 합니다.

  **참고:** 모든 범주에는 표시 항목을 하나 이상 있어야 합니다.

  IDE를 사용 합니다 **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** 여러 범주의 합집합을 정의 하는 인터페이스입니다.

  구현을 사용 하 여 IDE를 제공합니다.

- 지정된 된 그룹을 구성 하는 범주 목록

- 인스턴스에 액세스 [IVsFontAndColorDefaults](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) 그룹 내에서 각 범주를 지원 합니다.

- 지역화할 수 있는 그룹 이름

#### <a name="updating-the-ide"></a>IDE를 업데이트 하는 중
 IDE 글꼴 및 색 설정에 대 한 정보를 캐시합니다. 따라서 IDE 글꼴 및 색 구성의 모든 수정 후 캐시를 최신 상태로 것이 좋습니다.

 통해 이루어집니다 캐시를 업데이트 합니다 [IvsFontAndColorCacheManager](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) 인터페이스 및 전역으로 또는 뿐만 아니라 선택한 항목 수행된 될 수 있습니다.

### <a name="handling-font-and-color-changes"></a>글꼴 및 색 변경 내용 처리
 VSPackage를 표시 하는 텍스트의 색 지정을 올바르게 지원 하려면 VSPackage를 지 원하는 색 지정 서비스는 글꼴 및 색 속성 페이지를 통해 사용자가 시작한 변경 내용에 응답 해야 합니다.

 이 작업을 수행 하려면 VSPackage 해야 합니다.

- **IDE에서 생성 된 이벤트를 처리할** 를 구현 하 여 합니다 [IVsFontAndColorEvents](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.aspx) 인터페이스입니다. IDE 글꼴 및 색 페이지의 사용자 수정 다음 적절 한 메서드를 호출 합니다. 예를 들어 호출을 [OnFontChanged](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged.aspx) 새 글꼴을 선택 하는 경우 메서드.

  **OR**

- **변경 내용에 대 한 IDE를 폴링할**합니다. 시스템이 구현 통해 수행할 수 있습니다 [IVsFontAndColorStorage](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) 인터페이스입니다. 하지만 주로 지원용 지 속성을 [GetItem](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem.aspx) 메서드 표시 항목에 대 한 글꼴 및 색 정보를 가져올 수 있습니다. 글꼴 및 색 설정에 대 한 자세한 내용은 MSDN 문서를 참조 하세요 [에 액세스 하는 저장 된 글꼴 및 색 설정](https://msdn.microsoft.com/library/bb166382.aspx)합니다.

  **참고:** 폴링 결과가 올바른지 확인 하려면 사용 합니다 [IVsFontAndColorCacheManager](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) 캐시 플러시 및 업데이트의 검색 메서드를 호출 하는 데 필요한 경우를 결정 하는 인터페이스를 [IVsFontAndColorStorage ](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) 인터페이스입니다.

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>인터페이스를 구현 하지 않고 사용자 지정 글꼴 및 색 범주를 등록
 다음 코드 예제에서는 사용자 지정 글꼴을 등록 하 고 인터페이스를 구현 하지 않고도 색 범주 하는 방법을 보여 줍니다.

```xml
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

 **참고:**

- "NameID" 패키지에서 지역화 된 범주 이름의 리소스 ID =

- "ToolWindowPackage" = Package GUID

- "Category" = "{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"은 예 시일 뿐 이며 실제 값은 구현자에 의해 제공 되는 새 GUID를 수 있습니다.

### <a name="set-the-font-and-color-property-category-guid"></a>글꼴 및 색 속성 범주의 GUID를 설정 합니다.
 아래 코드 예제에서는 범주 Guid를 설정 하는 방법을 보여 줍니다.

```cs
// m_pView is your IVsTextView
IVsTextEditorPropertyCategoryContainer spPropCatContainer =
(IVsTextEditorPropertyCategoryContainer)m_pView;
if (spPropCatContainer != null)
{
  IVsTextEditorPropertyContainer spPropContainer;
  Guid GUID_EditPropCategory_View_MasterSettings =
  new Guid("{D1756E7C-B7FD-49a8-B48E-87B14A55655A}");
  hr = spPropCatContainer.GetPropertyCategory(
  ref GUID_EditPropCategory_View_MasterSettings, out spPropContainer);
  if(hr == 0)
  {
    hr = spPropContainer.SetProperty(VSEDITPROPID.VSEDITPROPID_ViewGeneral_FontCategory, catGUID);
    hr = spPropContainer.SetProperty(VSEDITPROPID.VSEDITPROPID_ViewGeneral_ColorCategory, catGUID);
  }
}
```
