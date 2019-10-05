---
title: '연습: 보기 장식, 명령 및 설정 (열 안내선) 만들기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 4a2df0a3-42da-4f7b-996f-ee16a35ac922
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0cab24a373595ca1257cbdaa50c009eefa713ea7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68148837"
---
# <a name="walkthrough-creating-a-view-adornment-commands-and-settings-column-guides"></a>연습: 보기 장식, 명령 및 설정(열 안내선) 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

명령 및 효과 보기를 사용 하 여 Visual Studio 텍스트/코드 편집기를 확장할 수 있습니다. 이 항목에서는 인기 있는 확장 기능을 열 가이드를 사용 하 여 시작 하는 방법을 보여 줍니다. 열 안내선은 특정 열 너비에 코드를 관리할 수 있도록 텍스트 편집기의 보기에 그려지는 시각적으로 밝은 선입니다. 구체적으로 서식이 지정 된 코드 샘플 문서, 블로그 게시물에서에서 포함 또는 버그 보고서에 대해 중요할 수 있습니다.

이 연습에서는 다음을 수행 해야합니다.

- VSIX 프로젝트를 만듭니다
- 편집기 보기 adornment 추가
- 저장 및 시작 설정 (여기서 그리기 열 안내선과 해당 색)에 대 한 지원 추가
- 명령을 추가 (guides 열 추가/제거, 해당 색을 변경)
- 편집 메뉴에 텍스트 문서 상황에 맞는 메뉴 명령을 배치합니다
- Visual Studio 명령 창에서 명령을 호출 하는 것에 대 한 지원 추가  
  
  이 Visual Studio 갤러리를 사용 하 여 열 안내선 기능의 버전을 사용해 볼 수 있습니다[확장](https://visualstudiogallery.msdn.microsoft.com/da227a0b-0e31-4a11-8f6b-3a149cf2e459?SRC=Home)합니다.  
  
  **참고**:이 연습에서는 visual studio 확장 템플릿에 의해 생성 된 소수의 파일에 많은 양의 코드를 붙여 하지만 곧이 연습에서는 참조 하는 다른 확장 프로그램 예제를 사용 하 여 GitHub에서 완성 된 솔루션입니다. 완성 된 코드는 generictemplate 아이콘을 사용 하는 대신 실제 명령 아이콘에는 약간 다릅니다.

## <a name="getting-started"></a>시작하기
Visual Studio 2015부터 수행 설치 하면 Visual Studio SDK 다운로드 센터에서. Visual Studio 설치에서 선택적 기능으로 포함 됩니다. 또한 VS SDK를 나중에 설치할 수 있습니다. 자세한 내용은 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)합니다.

## <a name="setting-up-the-solution"></a>솔루션 설정
먼저는 VSIX 프로젝트를 만듭니다, 그리고 편집기 보기 adornment, 추가 추가한 다음 (추가 하는 명령은 소유 하기 위해 VSPackage) 명령. 기본 아키텍처는 다음과 같습니다.

- 만든 텍스트 뷰 생성 수신기가는 `ColumnGuideAdornment` 뷰당 개체입니다. 이 개체는 뷰를 변경 하는 방법에 대 한 이벤트를 수신 하거나 필요에 따라 설정 변경, 업데이트 또는 다시 그리기 열 안내 합니다.
- 한 `GuidesSettingsManager` Visual Studio 설정 저장소에서 읽기와 쓰기를 처리 하는 합니다. Settings manager 역시 사용자 명령을 지 원하는 설정을 업데이트 하는 것에 대 한 작업 (열 추가, 열을 제거, 색 변경).
- 사용자 명령에 있는 경우 필요한 VSIP 패키지가 이지만 명령을 구현 개체를 초기화 하는 상용구 코드 뿐입니다.
- `ColumnGuideCommands` .vsct 파일에 선언 된 사용자 명령을 구현 하 고 명령에 대 한 명령 처리기를 후크 하는 개체입니다.
  
  **VSIX**합니다. 사용 하 여 **파일 &#124; 새로 만들기...** 프로젝트를 만들려면 명령입니다. 왼쪽된 탐색 창에서 C#에서 확장 노드를 선택 하 고 선택 **VSIX 프로젝트** 오른쪽 창에서. ColumnGuides 이름을 입력 하 고 선택 **확인** 프로젝트를 만듭니다.
  
  **Adornment 볼**합니다. 솔루션 탐색기에서 프로젝트 노드의 오른쪽 포인터 단추를 누릅니다. 선택 된 **추가 &#124; 새 항목...** 새 보기 adornment 항목을 추가 하려면 명령입니다. 선택할 **확장성 &#124; 편집기** 왼쪽된 탐색 창에서 선택한 **편집기 뷰포트 Adornment** 오른쪽 창에서. 선택한 항목 이름으로 이름 ColumnGuideAdornment **추가** 추가 합니다.
  
  이 항목 템플릿은 두 개의 파일 및에 추가 프로젝트 (뿐만 아니라 참조 등)을 확인할 수 있습니다. ColumnGuideAdornment.cs 및 ColumnGuideAdornmentTextViewCreationListener.cs 합니다. 방금 템플릿 보기에 자주색 사각형을 그립니다. 아래 뷰 생성 수신기에 줄의 몇 가지 변경 및 ColumnGuideAdornment.cs의 내용을 대체 합니다.
  
  **명령을**합니다. 솔루션 탐색기에서 프로젝트 노드의 오른쪽 포인터 단추를 누릅니다. 선택 된 **추가 &#124; 새 항목...** 새 보기 adornment 항목을 추가 하려면 명령입니다. 선택할 **확장성 &#124; VSPackage** 왼쪽된 탐색 창에서 선택한 **사용자 지정 명령** 오른쪽 창에서. 선택한 항목 이름으로 이름 ColumnGuideCommands **추가** 추가 합니다. ColumnGuideCommands.cs, ColumnGuideCommandsPackage.cs, 및 ColumnGuideCommandsPackage.vsct 여러 참조 외에도 추가 명령 및 패키지를 추가 합니다. 다음 정의 하 고 명령을 구현 첫 번째 및 마지막 파일의 내용을 바꿉니다.

## <a name="setting-up-the-text-view-creation-listener"></a>텍스트 뷰 생성 수신기 설정
ColumnGuideAdornmentTextViewCreationListener.cs 편집기에서 엽니다. 이 코드는 Visual Studio 텍스트 뷰를 만듭니다 때마다에 대 한 처리기를 구현 합니다. 보기의 특징에 따라 처리기가 호출 하는 경우를 제어 하는 특성이 있습니다.

또한 코드는 표시 계층을 선언 해야 합니다. 편집기 뷰를 업데이트할 때 adornment 계층 뷰를 가져옵니다 하 고는 adornment 요소를 가져옵니다. 특성을 사용 하 여 다른 사용자를 기준으로 계층의 순서를 선언할 수 있습니다. 다음 줄을 바꿉니다.

```csharp
[Order(After = PredefinedAdornmentLayers.Caret)]
```

 이러한 두 줄:

```csharp
[Order(Before = PredefinedAdornmentLayers.Text)]
[TextViewRole(PredefinedTextViewRoles.Document)]
```

바꿨기 줄 장식 레이어를 선언 하는 특성 그룹입니다.  첫 번째 줄은 변경 된 내용만 열 가이드 선을 표시할 위치를 변경 했습니다. 선이 "이전" 텍스트 뷰에서 의미 뒤 또는 텍스트 아래에 나타납니다. 두 번째 줄은 열 가이드 장식을 개념이 문서에 맞는 텍스트 엔터티에 적용할 수 있지만 편집 가능한 텍스트에 대해서만 작동 하 고 장식을 예를 들어, 선언할 수 있다는 선언 합니다. 에 자세한 정보가 [언어 서비스 및 편집기 확장 지점](../extensibility/language-service-and-editor-extension-points.md)

## <a name="implementing-the-settings-manager"></a>Settings Manager 구현
GuidesSettingsManager.cs 내용의 (아래 설명)를 다음 코드로 바꿉니다.

```csharp
using Microsoft.VisualStudio.Settings;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Settings;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Windows.Media;

namespace ColumnGuides
{
    internal static class GuidesSettingsManager
    {
        // Because my code is always called from the UI thred, this succeeds.
        internal static SettingsManager VsManagedSettingsManager =
            new ShellSettingsManager(ServiceProvider.GlobalProvider);

        private const int _maxGuides = 5;
        private const string _collectionSettingsName = "Text Editor";
        private const string _settingName = "Guides";
        // 1000 seems reasonable since primary scenario is long lines of code
        private const int _maxColumn = 1000;

        static internal bool AddGuideline(int column)
        {
            if (! IsValidColumn(column))
                throw new ArgumentOutOfRangeException(
                    "column",
                    "The paramenter must be between 1 and " + _maxGuides.ToString());
            var offsets = GuidesSettingsManager.GetColumnOffsets();
            if (offsets.Count() >= _maxGuides)
                return false;
            // Check for duplicates
            if (offsets.Contains(column))
                return false;
            offsets.Add(column);
            WriteSettings(GuidesSettingsManager.GuidelinesColor, offsets);
            return true;
        }

        static internal bool RemoveGuideline(int column)
        {
            if (!IsValidColumn(column))
                throw new ArgumentOutOfRangeException(
                    "column", "The paramenter must be between 1 and 10,000");
            var columns = GuidesSettingsManager.GetColumnOffsets();
            if (! columns.Remove(column))
            {
                // Not present. Allow user to remove the last column 
                // even if they're not on the right column.
                if (columns.Count != 1)
                    return false;

                columns.Clear();
            }
            WriteSettings(GuidesSettingsManager.GuidelinesColor, columns);
            return true;
        }

        static internal bool CanAddGuideline(int column)
        {
            if (!IsValidColumn(column))
                return false;
            var offsets = GetColumnOffsets();
            if (offsets.Count >= _maxGuides)
                return false;
            return ! offsets.Contains(column);
        }

        static internal bool CanRemoveGuideline(int column)
        {
            if (! IsValidColumn(column))
                return false;
            // Allow user to remove the last guideline regardless of the column.
            // Okay to call count, we limit the number of guides.
            var offsets = GuidesSettingsManager.GetColumnOffsets();
            return offsets.Contains(column) || offsets.Count() == 1;
        }

        static internal void RemoveAllGuidelines()
        {
            WriteSettings(GuidesSettingsManager.GuidelinesColor, new int[0]);
        }

        private static bool IsValidColumn(int column)
        {
            // zero is allowed (per user request)
            return 0 <= column && column <= _maxColumn;
        }

        // This has format "RGB(<int>, <int>, <int>) <int> <int>...".
        // There can be any number of ints following the RGB part,
        // and each int is a column (char offset into line) where to draw.
        static private string _guidelinesConfiguration;
        static private string GuidelinesConfiguration
        {
            get
            {
                if (_guidelinesConfiguration == null)
                {
                    _guidelinesConfiguration =
                        GetUserSettingsString(
                            GuidesSettingsManager._collectionSettingsName,
                            GuidesSettingsManager._settingName)
                        .Trim();
                }
                return _guidelinesConfiguration;
            }

            set
            {
                if (value != _guidelinesConfiguration)
                {
                    _guidelinesConfiguration = value;
                    WriteUserSettingsString(
                        GuidesSettingsManager._collectionSettingsName,
                        GuidesSettingsManager._settingName, value);
                    // Notify ColumnGuideAdornments to update adornments in views.
                    var handler = GuidesSettingsManager.SettingsChanged;
                    if (handler != null)
                        handler();
                }
            }
        }

        internal static string GetUserSettingsString(string collection, string setting)
        {
            var store = GuidesSettingsManager
                            .VsManagedSettingsManager
                            .GetReadOnlySettingsStore(SettingsScope.UserSettings);
            return store.GetString(collection, setting, "RGB(255,0,0) 80");
        }

        internal static void WriteUserSettingsString(string key, string propertyName,
                                                     string value)
        {
            var store = GuidesSettingsManager
                            .VsManagedSettingsManager
                            .GetWritableSettingsStore(SettingsScope.UserSettings);
            store.CreateCollection(key);
            store.SetString(key, propertyName, value);
        }

        // Persists settings and sets property with side effect of signaling
        // ColumnGuideAdornments to update.
        static private void WriteSettings(Color color, IEnumerable<int> columns)
        {
            string value = ComposeSettingsString(color, columns);
            GuidelinesConfiguration = value;
        }

        private static string ComposeSettingsString(Color color,
                                                    IEnumerable<int> columns)
        {
            StringBuilder sb = new StringBuilder();
            sb.AppendFormat("RGB({0},{1},{2})", color.R, color.G, color.B);
            IEnumerator<int> columnsEnumerator = columns.GetEnumerator();
            if (columnsEnumerator.MoveNext())
            {
                sb.AppendFormat(" {0}", columnsEnumerator.Current);
                while (columnsEnumerator.MoveNext())
                {
                    sb.AppendFormat(", {0}", columnsEnumerator.Current);
                }
            }
            return sb.ToString();
        }

        // Parse a color out of a string that begins like "RGB(255,0,0)"
        static internal Color GuidelinesColor
        {
            get
            {
                string config = GuidelinesConfiguration;
                if (!String.IsNullOrEmpty(config) && config.StartsWith("RGB("))
                {
                    int lastParen = config.IndexOf(')');
                    if (lastParen > 4)
                    {
                        string[] rgbs = config.Substring(4, lastParen - 4).Split(',');

                        if (rgbs.Length >= 3)
                        {
                            byte r, g, b;
                            if (byte.TryParse(rgbs[0], out r) &&
                                byte.TryParse(rgbs[1], out g) &&
                                byte.TryParse(rgbs[2], out b))
                            {
                                return Color.FromRgb(r, g, b);
                            }
                        }
                    }
                }
                return Colors.DarkRed;
            }

            set
            {
                WriteSettings(value, GetColumnOffsets());
            }
        }

        // Parse a list of integer values out of a string that looks like
        // "RGB(255,0,0) 1, 5, 10, 80"
        static internal List<int> GetColumnOffsets()
        {
            var result = new List<int>();
            string settings = GuidesSettingsManager.GuidelinesConfiguration;
            if (String.IsNullOrEmpty(settings))
                return new List<int>();

            if (!settings.StartsWith("RGB("))
                return new List<int>();

            int lastParen = settings.IndexOf(')');
            if (lastParen <= 4)
                return new List<int>();

            string[] columns = settings.Substring(lastParen + 1).Split(',');

            int columnCount = 0;
            foreach (string columnText in columns)
            {
                int column = -1;
                // VS 2008 gallery extension didn't allow zero, so per user request ...
                if (int.TryParse(columnText, out column) && column >= 0)
                {
                    columnCount++;
                    result.Add(column);
                    if (columnCount >= _maxGuides)
                        break;
                }
            }
            return result;
        }

        // Delegate and Event to fire when settings change so that ColumnGuideAdornments
        // can update. We need nothing special in this event since the settings manager
        // is statically available.
        //
        internal delegate void SettingsChangedHandler();
        static internal event SettingsChangedHandler SettingsChanged;

    }
}

```

이 코드의 대부분은 바로 만들고 설정 형식을 구문 분석 합니다. "RGB(\<int>,\<int>,\<int>) \<int>, \<int>, …". 끝에 정수는 열 안내선을 원하는 위치 1부터 시작 열. 열 가이드 확장 설정 단일 값 문자열의 모든 설정을 캡처합니다.

강조 표시 된 코드의 몇 가지 부분이 있습니다. 다음 코드 줄 설정 저장소에 대 한 Visual Studio 관리 되는 래퍼를 가져옵니다. 대부분의 경우 Windows 레지스트리를 통해 추출이 있지만이 API는 독립적 저장소 메커니즘입니다.

```csharp
internal static SettingsManager VsManagedSettingsManager =
    new ShellSettingsManager(ServiceProvider.GlobalProvider);
```

 Visual Studio 설정 저장소 설정을 모두를 고유 하 게 식별 하는 범주 식별자와 설정 식별자를 사용 합니다.

```csharp
private const string _collectionSettingsName = "Text Editor";
private const string _settingName = "Guides";
```

사용할 필요가 없습니다 `“Text Editor”` 범주로 이름 및 사용자를 선택할 수 원하는 것입니다.

첫 번째 몇 가지 기능은 설정을 변경 하기 위한 진입점입니다. 최대 허용 하는 가이드와 같은 높은 수준의 제약 조건을 확인 합니다. 호출 후 `WriteSettings` 설정 문자열을 작성 하 고 속성을 설정 하는 `GuideLinesConfiguration`합니다. Visual Studio 설정 저장소에 발생 합니다. 설정 값을 저장이 속성을 설정 합니다 `SettingsChanged` 이벤트를 모두 업데이트는 `ColumnGuideAdornment` 텍스트 뷰를 사용 하 여 연결 된 각 개체입니다.

와 같은 항목 지점 함수의 몇 가지 `CanAddGuideline`, 설정을 변경 하는 명령을 구현 하는 데 사용 되는 합니다. Visual Studio 메뉴에 표시 하는 경우 명령 구현 하는 경우 명령은 현재 설정 되어, 이름 등 쿼리 합니다. 아래 명령 구현에 대 한 이러한 진입점 후크 하는 방법을 표시 됩니다. 참조 [확장 메뉴 및 명령을](../extensibility/extending-menus-and-commands.md) 명령에 대 한 자세한 내용은 합니다.

## <a name="implementing-the-columnguideadornment-class"></a>ColumnGuideAdornment 클래스 구현
`ColumnGuideAdornment` 선의 도구 영역을 가질 수 있는 각 텍스트 보기에 대 한 클래스를 인스턴스화합니다. 이 클래스는 뷰를 변경 하는 방법에 대 한 이벤트를 수신 하거나 필요에 따라 설정 변경, 업데이트 또는 다시 그리기 열 안내 합니다.

ColumnGuideAdornment.cs 내용의 (아래 설명)를 다음 코드로 바꿉니다.

```csharp
using System;
using System.Windows.Media;
using Microsoft.VisualStudio.Text.Editor;
using System.Collections.Generic;
using System.Windows.Shapes;
using Microsoft.VisualStudio.Text.Formatting;
using System.Windows;

namespace ColumnGuides
{
    /// <summary>
    /// Adornment class, one instance per text view that draws a guides on the viewport
    /// </summary>
    internal sealed class ColumnGuideAdornment
    {
        private const double _lineThickness = 1.0;
        private IList<Line> _guidelines;
        private IWpfTextView _view;
        private double _baseIndentation;
        private double _columnWidth;

        /// <summary>
        /// Creates editor column guidelines
        /// </summary>
        /// <param name="view">The <see cref="IWpfTextView"/> upon
        /// which the adornment will be drawn</param>
        public ColumnGuideAdornment(IWpfTextView view)
        {
            _view = view;
            _guidelines = CreateGuidelines();
            GuidesSettingsManager.SettingsChanged +=
                new GuidesSettingsManager.SettingsChangedHandler(SettingsChanged);
            view.LayoutChanged +=
                new EventHandler<TextViewLayoutChangedEventArgs>(OnViewLayoutChanged);
            _view.Closed += new EventHandler(OnViewClosed);
        }

        void SettingsChanged()
        {
            _guidelines = CreateGuidelines();
            UpdatePositions();
            AddGuidelinesToAdornmentLayer();
        }

        void OnViewClosed(object sender, EventArgs e)
        {
            _view.LayoutChanged -= OnViewLayoutChanged;
            _view.Closed -= OnViewClosed;
            GuidesSettingsManager.SettingsChanged -= SettingsChanged;
        }

        private bool _firstLayoutDone;

        void OnViewLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
        {
            bool fUpdatePositions = false;

            IFormattedLineSource lineSource = _view.FormattedLineSource;
            if (lineSource == null)
            {
                return;
            }
            if (_columnWidth != lineSource.ColumnWidth)
            {
                _columnWidth = lineSource.ColumnWidth;
                fUpdatePositions = true;
            }
            if (_baseIndentation != lineSource.BaseIndentation)
            {
                _baseIndentation = lineSource.BaseIndentation;
                fUpdatePositions = true;
            }
            if (fUpdatePositions ||
                e.VerticalTranslation ||
                e.NewViewState.ViewportTop != e.OldViewState.ViewportTop ||
                e.NewViewState.ViewportBottom != e.OldViewState.ViewportBottom)
            {
                UpdatePositions();
            }
            if (!_firstLayoutDone)
            {
                AddGuidelinesToAdornmentLayer();
                _firstLayoutDone = true;
            }
        }

        private static IList<Line> CreateGuidelines()
        {
            Brush lineBrush = new SolidColorBrush(GuidesSettingsManager.GuidelinesColor);
            DoubleCollection dashArray = new DoubleCollection(new double[] { 1.0, 3.0 });
            IList<Line> result = new List<Line>();
            foreach (int column in GuidesSettingsManager.GetColumnOffsets())
            {
                Line line = new Line()
                {
                    // Use the DataContext slot as a cookie to hold the column
                    DataContext = column,
                    Stroke = lineBrush,
                    StrokeThickness = _lineThickness,
                    StrokeDashArray = dashArray
                };
                result.Add(line);
            }
            return result;
        }

        void UpdatePositions()
        {
            foreach (Line line in _guidelines)
            {
                int column = (int)line.DataContext;
                line.X2 = _baseIndentation + 0.5 + column * _columnWidth;
                line.X1 = line.X2;
                line.Y1 = _view.ViewportTop;
                line.Y2 = _view.ViewportBottom;
            }
        }

        void AddGuidelinesToAdornmentLayer()
        {
            // Grab a reference to the adornment layer that this adornment
            // should be added to
            // Must match exported name in ColumnGuideAdornmentTextViewCreationListener
            IAdornmentLayer adornmentLayer =
                _view.GetAdornmentLayer("ColumnGuideAdornment");
            if (adornmentLayer == null)
                return;
            adornmentLayer.RemoveAllAdornments();
            // Add the guidelines to the adornment layer and make them relative
            // to the viewport
            foreach (UIElement element in _guidelines)
                adornmentLayer.AddAdornment(AdornmentPositioningBehavior.OwnerControlled,
                                            null, null, element, null);
        }
    }

}
```

이 클래스의 인스턴스를 연결 유지 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> 목록과 `Line` 보기에서 그린 개체입니다.

생성자 (에서 호출할 `ColumnGuideAdornmentTextViewCreationListener` Visual Studio 새 뷰를 만들 때) 열 안내선이 만들어지고 `Line` 개체입니다. 생성자도에 대 한 처리기를 추가 합니다 `SettingsChanged` 이벤트 (에 정의 된 `GuidesSettingsManager`) 및 이벤트 보기 `LayoutChanged` 및 `Closed`합니다.

`LayoutChanged` 여러 가지 Visual Studio 보기를 만드는 경우를 포함 하 여 보기에서 변경 내용으로 인해 이벤트가 발생 합니다. 합니다 `OnViewLayoutChanged` 처리기 호출 `AddGuidelinesToAdornmentLayer` 실행 합니다. 코드 `OnViewLayoutChanged` 글꼴 크기를 변경, 보기 제본용, 가로 스크롤 등과 같은 변경 내용을 기반으로 하는 줄 위치를 업데이트 해야 하는지 결정 합니다. 코드 `UpdatePositions` 자 또는 텍스트의 줄에 지정 된 문자 오프셋에 있는 텍스트에 있는 열의 바로 뒤에 그릴 안내선 발생 합니다.

설정이 변경 될 때마다 합니다 `SettingsChanged` 함수에 모든 항목을 바로 다시는 `Line` 모든 새 설정을 사용 하 여 개체입니다. 코드는 줄 위치를 설정한 후 모든 이전 제거 `Line` 에서 개체를 `ColumnGuideAdornment` adornment 계층 새로 추가 합니다.

## <a name="defining-the-commands-menus-and-menu-placements"></a>명령, 메뉴 및 메뉴 위치를 정의합니다.
있을 수 있습니다 훨씬 명령 및 메뉴 선언, 기타 다양 한 메뉴 명령 또는 메뉴 그룹에 배치 및 명령 처리기를 연결 합니다. 이 연습에서는이 확장 하지만 심층적인 정보에 대 한 명령이 작동 하는 방법을 강조 표시를 참조 하십시오 [확장 메뉴 및 명령을](../extensibility/extending-menus-and-commands.md)합니다.

### <a name="introduction-to-the-code"></a>코드를 소개
열 안내선 확장 선언에 속하는 명령 그룹을 보여 줍니다 (열 추가, 열을 제거, 선 색 변경) 한 다음 편집기의 상황에 맞는 메뉴의 하위 메뉴에 해당 그룹을 배치 합니다. 열 안내선 확장 기본 명령을 추가 **편집** 메뉴 하지만 계속 보이지 않는, 아래 일반적인 패턴으로 설명 합니다.

명령이 구현에 세 부분이 있습니다. ColumnGuideCommandsPackage.cs ColumnGuideCommandsPackage.vsct, 하며 ColumnGuideCommands.cs 합니다. 템플릿에서 생성 된 코드 명령을 배치 합니다 **도구** 구현으로 대화 상자가 표시 되는 메뉴입니다. 하는 방법에 구현 되는 ColumnGuideCommands.cs 파일과.vsct 이므로 상당히 간단 하 게 살펴볼 수 있습니다. 아래 이러한 파일의 코드를 바꿉니다.

패키지 코드는 Visual Studio 확장 명령 및 명령을 배치 하는 위치를 제공 하는 검색에 필요한 상용구 선언입니다. 패키지를 초기화 하는 경우에 명령을 구현 클래스를 인스턴스화합니다. 명령에 관련 된 패키지에 대 한 자세한 내용은 위에 링크 명령을 참조 하십시오.

### <a name="a-common-commands-pattern"></a>일반적인 명령 패턴
열 안내선 확장의 명령은 Visual Studio의 매우 일반적인 패턴의 예입니다. 그룹에 관련 된 명령을 배치 하 고 해당 그룹에 놓으면 주 메뉴에서 자주 사용 하 여 "`<CommandFlag>CommandWellOnly</CommandFlag>`" 명령이 표시 되지 않도록 설정 합니다. 주 메뉴 명령을 배치 (같은 **편집**)이이 방법은 유용한 이름을 제공 (같은 **Edit.AddColumnGuide**)는 키 바인딩에 다시 할당할 때 명령을 찾는 데 유용  **도구 옵션** 하 고 명령을 호출할 때 완료를 가져오기 위한 합니다 **명령 창**합니다.

그런 다음 상황에 맞는 메뉴에 명령 그룹을 추가 하 하거나 하위 메뉴 명령을 사용 하 여 사용자를 예상 하는 위치. Visual Studio에서 처리 `CommandWellOnly` 주 메뉴의 경우에 표시 안 함 플래그를으로 합니다. 상황에 맞는 메뉴 또는 하위 메뉴 명령의 동일한 그룹에 배치 하는 경우 명령이 표시 됩니다.

일반적인 패턴의 일부로 열 안내선 확장 단일 하위 메뉴를 포함 하는 두 번째 그룹을 만듭니다. 하위 메뉴에는 네 개의 열 가이드 명령 사용 하 여 첫 번째 그룹에 포함 됩니다. 하위 메뉴를 포함 하는 두 번째 그룹은 다시 사용할 수 있는 자산 다양 한 상황에 맞는 메뉴에 배치 하는 이러한 상황에 맞는 메뉴에서 하위 메뉴를 배치 하는 경우

### <a name="the-vsct-file"></a>.Vsct 파일
.Vsct 파일 명령과 어디로 이동 아이콘 함께 등을 선언 합니다. .Vsct 파일의 내용을 (아래 설명)를 다음 코드로 바꿉니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">

  <!--  This is the file that defines the actual layout and type of the commands.
        It is divided in different sections (e.g. command definition, command
        placement, ...), with each defining a specific set of properties.
        See the comment before each section for more details about how to
        use it. -->

  <!--  The VSCT compiler (the tool that translates this file into the binary
        format that VisualStudio will consume) has the ability to run a preprocessor
        on the vsct file; this preprocessor is (usually) the C++ preprocessor, so
        it is possible to define includes and macros with the same syntax used
        in C++ files. Using this ability of the compiler here, we include some files
        defining some of the constants that we will use inside the file. -->

  <!--This is the file that defines the IDs for all the commands exposed by
      VisualStudio. -->
  <Extern href="stdidcmd.h"/>

  <!--This header contains the command ids for the menus provided by the shell. -->
  <Extern href="vsshlids.h"/>

  <!--The Commands section is where commands, menus, and menu groups are defined.
      This section uses a Guid to identify the package that provides the command
      defined inside it. -->
  <Commands package="guidColumnGuideCommandsPkg">
    <!-- Inside this section we have different sub-sections: one for the menus, another
    for the menu groups, one for the buttons (the actual commands), one for the combos
    and the last one for the bitmaps used. Each element is identified by a command id
    that is a unique pair of guid and numeric identifier; the guid part of the identifier
    is usually called "command set" and is used to group different command inside a
    logically related group; your package should define its own command set in order to
    avoid collisions with command ids defined by other packages. -->

    <!-- In this section you can define new menu groups. A menu group is a container for
         other menus or buttons (commands); from a visual point of view you can see the
         group as the part of a menu contained between two lines. The parent of a group
         must be a menu. -->
    <Groups>

      <!-- The main group is parented to the edit menu. All the buttons within the group
           have the "CommandWellOnly" flag, so they're actually invisible, but it means
           they get canonical names that begin with "Edit". Using placements, the group
           is also placed in the GuidesSubMenu group. -->
      <!-- The priority 0xB801 is chosen so it goes just after
           IDG_VS_EDIT_COMMANDWELL -->
      <Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
             priority="0xB801">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />
      </Group>

      <!-- Group for holding the "Guidelines" sub-menu anchor (the item on the menu that
           drops the sub menu). The group is parented to
           the context menu for code windows. That takes care of most editors, but it's
           also placed in a couple of other windows using Placements -->
      <Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
             priority="0x0600">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_CTXT_CODEWIN" />
      </Group>

    </Groups>

    <Menus>
      <Menu guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" priority="0x1000"
            type="Menu">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup" />
        <Strings>
          <ButtonText>&Column Guides</ButtonText>
        </Strings>
      </Menu>
    </Menus>

    <!--Buttons section. -->
    <!--This section defines the elements the user can interact with, like a menu command or a button
        or combo box in a toolbar. -->
    <Buttons>
      <!--To define a menu group you have to specify its ID, the parent menu and its
          display priority.
          The command is visible and enabled by default. If you need to change the
          visibility, status, etc, you can use the CommandFlag node.
          You can add more than one CommandFlag node e.g.:
              <CommandFlag>DefaultInvisible</CommandFlag>
              <CommandFlag>DynamicVisibility</CommandFlag>
          If you do not want an image next to your command, remove the Icon node or
          set it to <Icon guid="guidOfficeIcon" id="msotcidNoIcon" /> -->

      <Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"
              priority="0x0100" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <Icon guid="guidImages" id="bmpPicAddGuide" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <CommandFlag>AllowParams</CommandFlag>
        <Strings>
          <ButtonText>&Add Column Guide</ButtonText>
        </Strings>
      </Button>

      <Button guid="guidColumnGuidesCommandSet" id="cmdidRemoveColumnGuide"
              priority="0x0101" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <Icon guid="guidImages" id="bmpPicRemoveGuide" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <CommandFlag>AllowParams</CommandFlag>
        <Strings>
          <ButtonText>&Remove Column Guide</ButtonText>
        </Strings>
      </Button>

      <Button guid="guidColumnGuidesCommandSet" id="cmdidChooseGuideColor"
              priority="0x0103" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <Icon guid="guidImages" id="bmpPicChooseColor" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <Strings>
          <ButtonText>Column Guide &Color...</ButtonText>
        </Strings>
      </Button>

      <Button guid="guidColumnGuidesCommandSet" id="cmdidRemoveAllColumnGuides"
              priority="0x0102" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <Strings>
          <ButtonText>Remove A&ll Columns</ButtonText>
        </Strings>
      </Button>
    </Buttons>

    <!--The bitmaps section is used to define the bitmaps that are used for the
        commands.-->
    <Bitmaps>
      <!--  The bitmap id is defined in a way that is a little bit different from the
            others:
            the declaration starts with a guid for the bitmap strip, then there is the
            resource id of the bitmap strip containing the bitmaps and then there are
            the numeric ids of the elements used inside a button definition. An important
            aspect of this declaration is that the element id
            must be the actual index (1-based) of the bitmap inside the bitmap strip. -->
      <Bitmap guid="guidImages" href="Resources\ColumnGuideCommands.png"
              usedList="bmpPicAddGuide, bmpPicRemoveGuide, bmpPicChooseColor" />
    </Bitmaps>

  </Commands>

  <CommandPlacements>

    <!-- Define secondary placements for our groups -->

    <!-- Place the group containing the three commands in the sub-menu -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
                      priority="0x0100">
      <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />
    </CommandPlacement>

    <!-- The HTML editor context menu, for some reason, redefines its own groups
         so we need to place a copy of our context menu there too. -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_HTML" />
    </CommandPlacement>

    <!-- The HTML context menu in Dev12 changed. -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp_Dev12" id="IDMX_HTM_SOURCE_HTML_Dev12" />
    </CommandPlacement>

    <!-- Similarly for Script -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_SCRIPT" />
    </CommandPlacement>

    <!-- Similarly for ASPX  -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_ASPX" />
    </CommandPlacement>

    <!-- Similarly for the XAML editor context menu -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x0600">
      <Parent guid="guidXamlUiCmds" id="IDM_XAML_EDITOR" />
    </CommandPlacement>

  </CommandPlacements>

  <!-- This defines the identifiers and their values used above to index resources
       and specify commands. -->
  <Symbols>
    <!-- This is the package guid. -->
    <GuidSymbol name="guidColumnGuideCommandsPkg"
                value="{e914e5de-0851-4904-b361-1a3a9d449704}" />

    <!-- This is the guid used to group the menu commands together -->
    <GuidSymbol name="guidColumnGuidesCommandSet"
                value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">
      <IDSymbol name="GuidesContextMenuGroup" value="0x1020" />
      <IDSymbol name="GuidesMenuItemsGroup" value="0x1021" />
      <IDSymbol name="GuidesSubMenu" value="0x1022" />
      <IDSymbol name="cmdidAddColumnGuide" value="0x0100" />
      <IDSymbol name="cmdidRemoveColumnGuide" value="0x0101" />
      <IDSymbol name="cmdidChooseGuideColor" value="0x0102" />
      <IDSymbol name="cmdidRemoveAllColumnGuides" value="0x0103" />
    </GuidSymbol>

    <GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">
      <IDSymbol name="bmpPicAddGuide" value="1" />
      <IDSymbol name="bmpPicRemoveGuide" value="2" />
      <IDSymbol name="bmpPicChooseColor" value="3" />
    </GuidSymbol>

    <GuidSymbol name="CMDSETID_HtmEdGrp_Dev12"
                value="{78F03954-2FB8-4087-8CE7-59D71710B3BB}">
      <IDSymbol name="IDMX_HTM_SOURCE_HTML_Dev12" value="0x1" />
    </GuidSymbol>

    <GuidSymbol name="CMDSETID_HtmEdGrp" value="{d7e8c5e1-bdb8-11d0-9c88-0000f8040a53}">
      <IDSymbol name="IDMX_HTM_SOURCE_HTML" value="0x33" />
      <IDSymbol name="IDMX_HTM_SOURCE_SCRIPT" value="0x34" />
      <IDSymbol name="IDMX_HTM_SOURCE_ASPX" value="0x35" />
    </GuidSymbol>

    <GuidSymbol name="guidXamlUiCmds" value="{4c87b692-1202-46aa-b64c-ef01faec53da}">
      <IDSymbol name="IDM_XAML_EDITOR" value="0x103" />
    </GuidSymbol>
  </Symbols>

</CommandTable>

```

**GUIDS**. GUID (프로젝트 항목 템플릿에서 생성 된) ColumnGuideCommandsPackage.cs 파일에 선언 된 패키지 GUID (위에서 복사한.vsct 파일에 선언 된 패키지와 일치 하도록 해야 명령 처리기를 찾아 호출할 Visual Studio 용 ). 이 샘플 코드를 다시 사용 하는 경우에이 코드를 복사한 수 있는 다른 모든 사용자와 충돌 하지 않는 다른 GUID 있는지 확인 해야 합니다.

ColumnGuideCommandsPackage.cs에서이 줄을 찾아 따옴표 사이 있는 GUID를 복사 합니다.

```csharp
public const string PackageGuidString = "ef726849-5447-4f73-8de5-01b9e930f7cd";
```

다음 GUID를 붙여 넣습니다.vsct 파일에 있는 다음 줄 프로그램 `Symbols` 선언 합니다.

```xml
<GuidSymbol name="guidColumnGuideCommandsPkg" 
            value="{ef726849-5447-4f73-8de5-01b9e930f7cd}" />
```

명령의 Guid 설정 하 고 비트맵 이미지 파일을 너무 확장에 대해 고유 해야 합니다.

```xml
<GuidSymbol name="guidColumnGuidesCommandSet"
            value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">
<GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">
```

그러나 명령 집합을 변경 하려면 코드를 가져오려면이 연습의 이미지 Guid를 비트맵 필요가 없습니다. 명령을 ColumnGuideCommands.cs 파일의 선언과 일치 해야 하는 GUID를 설정 하지만 해당 파일의 내용이 너무; 바꿉니다. 따라서 Guid 일치 합니다.

.Vsct 파일에서 다른 Guid 변경 되지 않도록, 열 가이드 명령을 추가 되는 기존 메뉴를 식별 합니다.

**파일 섹션**합니다. .Vsct 세 개의 외부 섹션: 명령, 배치 및 기호입니다. 명령 섹션에는 명령 그룹, 메뉴, 단추 또는 메뉴 항목 및 아이콘에 대 한 비트맵 정의합니다. 배치 섹션 메뉴 또는 기존 메뉴에 추가 배치 그룹을 이동 하는 위치를 선언 합니다. Symbols 섹션 하면.vsct 코드 Guid 및 16 진수 숫자를 어디에서 나 것 보다 더 쉽게 읽을 수.vsct 파일에서 다른 곳에서 사용 되는 식별자를 선언 합니다.

**명령 섹션, 그룹 정의**합니다. 먼저 명령을 섹션 명령 그룹을 정의합니다. 명령 그룹은 그룹을 구분 하는 약간의 회색 선을 사용 하 여 메뉴에 표시 되는 명령입니다. 그룹에이 예에서 같이 전체 하위 메뉴를 채울 수도 수 있습니다 하 고이 경우 줄을 구분 하는 회색으로 표시 되지 합니다. .Vsct 파일을 두 개의 그룹을 선언 합니다 `GuidesMenuItemsGroup` 부모가 되는 `IDM_VS_MENU_EDIT` (주 **편집** 메뉴) 및 `GuidesContextMenuGroup` 부모가 되는 `IDM_VS_CTXT_CODEWIN` (코드 편집기의 상황에 맞는 메뉴).

두 번째 그룹 선언에는 `0x0600` 우선 순위:

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
             priority="0x0600">
```

열에 삽입할 하위 메뉴 그룹을 추가 하는 모든 상황에 맞는 메뉴의 끝에 있는 하위 메뉴를 안내 합니다. 그러나 가정 하지 않아야 가장 잘 하는 하위 메뉴를 사용 하려면 항상 마지막의 우선 순위를 사용 하 여 강제로 `0xFFFF`입니다. 어디에 배치 하는 상황에 맞는 메뉴에 하위 메뉴에 있는 참조를이 번호로 이리저리 조정 해야 합니다. 이 경우 `0x0600` 이 너무 관련해 서 볼 수 있지만 바람직하지 않은 경우 열 안내선 확장 보다 낮을 수에 해당 확장을 디자인 하는 다른 사람이 여지가 메뉴의 끝에 배치 합니다.

**명령 섹션에서는 메뉴 정의**합니다. 명령 섹션 하위 메뉴를 정의 하는 다음 `GuidesSubMenu`부모가는 `GuidesContextMenuGroup`합니다. `GuidesContextMenuGroup` 모든 관련 상황에 맞는 메뉴에 추가 그룹입니다. 배치 섹션에서 코드를이 하위 메뉴에서 4 개의 열 가이드 명령 사용 하 여 그룹을 배치합니다.

**명령 섹션, 정의 단추**합니다. 단추 4 개 열 수 있는 명령을 안내 하거나 명령을 섹션 다음 메뉴 항목을 정의 합니다. `CommandWellOnly`를 위에서 설명한, 명령을 주 메뉴에 배치 되는 경우에 표시 되지 않습니다.을 의미 합니다. 선언 단추 메뉴 항목의 두 가이드를 추가 및 제거 가이드도는 `AllowParams` 플래그:

```xml
<CommandFlag>AllowParams</CommandFlag>
```

이 플래그를 사용 하면, 함께 사용 하 여 주 메뉴 배치를 Visual Studio 명령 처리기를 호출할 때 인수를 수신 하는 명령을 합니다. 명령 창에서 명령을 호출 하는 사용자를 가져옵니다 전달 되는 인수 명령 처리기로 이벤트 인수입니다.

**명령 섹션, 비트맵 정의**합니다. 마지막 명령 섹션 비트맵 또는 명령에 사용 되는 아이콘을 선언 합니다. 이 프로젝트 리소스를 식별 하 고 사용 되는 아이콘의 인덱스 1부터 나열 하는 간단한 선언입니다. .Vsct 파일의 symbols 섹션 인덱스로 사용 되는 식별자의 값을 선언 합니다. 이 연습에서는 프로젝트에 추가 하는 사용자 지정 명령 항목 템플릿과 함께 제공 되는 비트맵 스트립을 사용 합니다.

**배치 섹션**합니다. 명령 뒤 섹션 배치 섹션이입니다. 첫 번째는 여기서 코드는 위에서 설명한 첫 번째 그룹 보유 네 열 가이드 하위 메뉴 명령을 명령을 표시 하는 위치를 추가 합니다.

```xml
<CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
                  priority="0x0100">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />
</CommandPlacement>
```

다른 배치의 모든 추가 합니다 `GuidesContextMenuGroup` (포함 하는 `GuidesSubMenu`) 다른 편집기 상황에 맞는 메뉴를 합니다. 코드를 선언 하는 경우는 `GuidesContextMenuGroup`, 코드 편집기의 상황에 맞는 메뉴 부모로 지정 되었습니다. 코드 편집기의 상황에 맞는 메뉴에 대 한 배치를 보이지 않는 이유입니다.

**섹션 기호**합니다. 위에서 설명한 대로 symbols 섹션 하면.vsct 코드 Guid 및 16 진수 숫자를 어디에서 나 것 보다 더 쉽게 읽을 수.vsct 파일에서 다른 곳에서 사용 되는 식별자를 선언 합니다. 이 섹션의 중요 한 사안이 패키지 GUID를 GUID 명령 구현 클래스의 선언에 동의 해야 합니다 명령 집합 패키지 클래스에 선언에 동의 해야 합니다는 됩니다.

## <a name="implementing-the-commands"></a>명령 구현
ColumnGuideCommands.cs 파일 명령을 구현 하 고 처리기 후크합니다. Visual Studio 패키지를 로드 하 고 초기화 하는 경우 패키지 호출 `Initialize` 명령 구현 클래스에 있습니다. 단순히 명령을 초기화 클래스를 인스턴스화하고 생성자는 모든 명령 처리기를 연결 합니다.

ColumnGuideCommands.cs 파일의 내용을 (아래 설명)를 다음 코드로 바꿉니다.

```csharp
using System;
using System.ComponentModel.Design;
using System.Globalization;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Interop;
using Microsoft.VisualStudio.TextManager.Interop;
using Microsoft.VisualStudio.Text.Editor;
using Microsoft.VisualStudio;

namespace ColumnGuides
{
    /// <summary>
    /// Command handler
    /// </summary>
    internal sealed class ColumnGuideCommands
    {

        const int cmdidAddColumnGuide = 0x0100;
        const int cmdidRemoveColumnGuide = 0x0101;
        const int cmdidChooseGuideColor = 0x0102;
        const int cmdidRemoveAllColumnGuides = 0x0103;

        /// <summary>
        /// Command menu group (command set GUID).
        /// </summary>
        static readonly Guid CommandSet =
            new Guid("c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e");

        /// <summary>
        /// VS Package that provides this command, not null.
        /// </summary>
        private readonly Package package;

        OleMenuCommand _addGuidelineCommand;
        OleMenuCommand _removeGuidelineCommand;

        /// <summary>
        /// Initializes the singleton instance of the command.
        /// </summary>
        /// <param name="package">Owner package, not null.</param>
        public static void Initialize(Package package)
        {
            Instance = new ColumnGuideCommands(package);
        }

        /// <summary>
        /// Gets the instance of the command.
        /// </summary>
        public static ColumnGuideCommands Instance
        {
            get;
            private set;
        }

        /// <summary>
        /// Initializes a new instance of the <see cref="ColumnGuideCommands"/> class.
        /// Adds our command handlers for menu (commands must exist in the command
        /// table file)
        /// </summary>
        /// <param name="package">Owner package, not null.</param>
        private ColumnGuideCommands(Package package)
        {
            if (package == null)
            {
                throw new ArgumentNullException("package");
            }

            this.package = package;

            // Add our command handlers for menu (commands must exist in the .vsct file)

            OleMenuCommandService commandService =
                this.ServiceProvider.GetService(typeof(IMenuCommandService))
                    as OleMenuCommandService;
            if (commandService != null)
            {
                // Add guide
                _addGuidelineCommand =
                    new OleMenuCommand(AddColumnGuideExecuted, null,
                                       AddColumnGuideBeforeQueryStatus,
                                       new CommandID(ColumnGuideCommands.CommandSet,
                                                     cmdidAddColumnGuide));
                _addGuidelineCommand.ParametersDescription = "<column>";
                commandService.AddCommand(_addGuidelineCommand);
                // Remove guide
                _removeGuidelineCommand =
                    new OleMenuCommand(RemoveColumnGuideExecuted, null,
                                       RemoveColumnGuideBeforeQueryStatus,
                                       new CommandID(ColumnGuideCommands.CommandSet,
                                                     cmdidRemoveColumnGuide));
                _removeGuidelineCommand.ParametersDescription = "<column>";
                commandService.AddCommand(_removeGuidelineCommand);
                // Choose color
                commandService.AddCommand(
                    new MenuCommand(ChooseGuideColorExecuted,
                                    new CommandID(ColumnGuideCommands.CommandSet,
                                                  cmdidChooseGuideColor)));
                // Remove all
                commandService.AddCommand(
                    new MenuCommand(RemoveAllGuidelinesExecuted,
                                    new CommandID(ColumnGuideCommands.CommandSet,
                                                  cmdidRemoveAllColumnGuides)));
            }
        }

        /// <summary>
        /// Gets the service provider from the owner package.
        /// </summary>
        private IServiceProvider ServiceProvider
        {
            get
            {
                return this.package;
            }
        }

        private void AddColumnGuideBeforeQueryStatus(object sender, EventArgs e)
        {
            int currentColumn = GetCurrentEditorColumn();
            _addGuidelineCommand.Enabled =
                GuidesSettingsManager.CanAddGuideline(currentColumn);
        }

        private void RemoveColumnGuideBeforeQueryStatus(object sender, EventArgs e)
        {
            int currentColumn = GetCurrentEditorColumn();
            _removeGuidelineCommand.Enabled =
                GuidesSettingsManager.CanRemoveGuideline(currentColumn);
        }

        private int GetCurrentEditorColumn()
        {
            IVsTextView view = GetActiveTextView();
            if (view == null)
            {
                return -1;
            }

            try
            {
                IWpfTextView textView = GetTextViewFromVsTextView(view);
                int column = GetCaretColumn(textView);

                // Note: GetCaretColumn returns 0-based positions. Guidelines are 1-based
                // positions.
                // However, do not subtract one here since the caret is positioned to the
                // left of
                // the given column and the guidelines are positioned to the right. We
                // want the
                // guideline to line up with the current caret position. e.g. When the
                // caret is
                // at position 1 (zero-based), the status bar says column 2. We want to
                // add a
                // guideline for column 1 since that will place the guideline where the
                // caret is.
                return column;
            }
            catch (InvalidOperationException)
            {
                return -1;
            }
        }

        /// <summary>
        /// Find the active text view (if any) in the active document.
        /// </summary>
        /// <returns>The IVsTextView of the active view, or null if there is no active
        /// document or the
        /// active view in the active document is not a text view.</returns>
        private IVsTextView GetActiveTextView()
        {
            IVsMonitorSelection selection =
                this.ServiceProvider.GetService(typeof(IVsMonitorSelection))
                                                    as IVsMonitorSelection;
            object frameObj = null;
            ErrorHandler.ThrowOnFailure(
                selection.GetCurrentElementValue(
                    (uint)VSConstants.VSSELELEMID.SEID_DocumentFrame, out frameObj));

            IVsWindowFrame frame = frameObj as IVsWindowFrame;
            if (frame == null)
            {
                return null;
            }

            return GetActiveView(frame);
        }

        private static IVsTextView GetActiveView(IVsWindowFrame windowFrame)
        {
            if (windowFrame == null)
            {
                throw new ArgumentException("windowFrame");
            }

            object pvar;
            ErrorHandler.ThrowOnFailure(
                windowFrame.GetProperty((int)__VSFPROPID.VSFPROPID_DocView, out pvar));

            IVsTextView textView = pvar as IVsTextView;
            if (textView == null)
            {
                IVsCodeWindow codeWin = pvar as IVsCodeWindow;
                if (codeWin != null)
                {
                    ErrorHandler.ThrowOnFailure(codeWin.GetLastActiveView(out textView));
                }
            }
            return textView;
        }

        private static IWpfTextView GetTextViewFromVsTextView(IVsTextView view)
        {

            if (view == null)
            {
                throw new ArgumentNullException("view");
            }

            IVsUserData userData = view as IVsUserData;
            if (userData == null)
            {
                throw new InvalidOperationException();
            }

            object objTextViewHost;
            if (VSConstants.S_OK
                   != userData.GetData(Microsoft.VisualStudio
                                                .Editor
                                                .DefGuidList.guidIWpfTextViewHost,
                                       out objTextViewHost))
            {
                throw new InvalidOperationException();
            }

            IWpfTextViewHost textViewHost = objTextViewHost as IWpfTextViewHost;
            if (textViewHost == null)
            {
                throw new InvalidOperationException();
            }

            return textViewHost.TextView;
        }

        /// <summary>
        /// Given an IWpfTextView, find the position of the caret and report its column
        /// number. The column number is 0-based
        /// </summary>
        /// <param name="textView">The text view containing the caret</param>
        /// <returns>The column number of the caret's position. When the caret is at the
        /// leftmost column, the return value is zero.</returns>
        private static int GetCaretColumn(IWpfTextView textView)
        {
            // This is the code the editor uses to populate the status bar.
            Microsoft.VisualStudio.Text.Formatting.ITextViewLine caretViewLine =
                textView.Caret.ContainingTextViewLine;
            double columnWidth = textView.FormattedLineSource.ColumnWidth;
            return (int)(Math.Round((textView.Caret.Left - caretViewLine.Left)
                                       / columnWidth));
        }

        /// <summary>
        /// Determine the applicable column number for an add or remove command.
        /// The column is parsed from command arguments, if present. Otherwise
        /// the current position of the caret is used to determine the column.
        /// </summary>
        /// <param name="e">Event args passed to the command handler.</param>
        /// <returns>The column number. May be negative to indicate the column number is
        /// unavailable.</returns>
        /// <exception cref="ArgumentException">The column number parsed from event args
        /// was not a valid integer.</exception>
        private int GetApplicableColumn(EventArgs e)
        {
            var inValue = ((OleMenuCmdEventArgs)e).InValue as string;
            if (!string.IsNullOrEmpty(inValue))
            {
                int column;
                if (!int.TryParse(inValue, out column) || column < 0)
                    throw new ArgumentException("Invalid column");
                return column;
            }

            return GetCurrentEditorColumn();
        }

        /// <summary>
        /// This function is the callback used to execute a command when the a menu item
        /// is clicked. See the Initialize method to see how the menu item is associated
        /// to this function using the OleMenuCommandService service and the MenuCommand
        /// class.
        /// </summary>
        private void AddColumnGuideExecuted(object sender, EventArgs e)
        {
            int column = GetApplicableColumn(e);
            if (column >= 0)
            {
                GuidesSettingsManager.AddGuideline(column);
            }
        }

        private void RemoveColumnGuideExecuted(object sender, EventArgs e)
        {
            int column = GetApplicableColumn(e);
            if (column >= 0)
            {
                GuidesSettingsManager.RemoveGuideline(column);
            }
        }

        private void RemoveAllGuidelinesExecuted(object sender, EventArgs e)
        {
            GuidesSettingsManager.RemoveAllGuidelines();
        }

        private void ChooseGuideColorExecuted(object sender, EventArgs e)
        {
            System.Windows.Media.Color color = GuidesSettingsManager.GuidelinesColor;

            using (System.Windows.Forms.ColorDialog picker =
                new System.Windows.Forms.ColorDialog())
            {
                picker.Color = System.Drawing.Color.FromArgb(255, color.R, color.G,
                                                             color.B);
                if (picker.ShowDialog() == System.Windows.Forms.DialogResult.OK)
                {
                    GuidesSettingsManager.GuidelinesColor =
                        System.Windows.Media.Color.FromRgb(picker.Color.R,
                                                           picker.Color.G,
                                                           picker.Color.B);
                }
            }
        }

    }
}

```

**참조 수정**합니다. 이 시점에 대 한 참조를 요소가 없습니다. 솔루션 탐색기에서 참조 노드 오른쪽 포인터 단추를 누릅니다. 선택 된 **추가...** 명령을 통해 Visual Studio의 대화형 창에 직접 통합됩니다. 합니다 **참조 추가** 대화 상자에 검색 상자 오른쪽 위 모퉁이에서. "편집기" (큰따옴표)를 입력 합니다. 선택 된 **Microsoft.VisualStudio.Editor** (확인 해야 합니다 하지 선택 항목의 왼쪽 상자 항목) 항목 선택 **확인** 참조를 추가 합니다.

**초기화**합니다. 패키지 클래스를 초기화 하는 경우 호출 `Initialize` 명령 구현 클래스에 있습니다. `ColumnGuideCommands` 초기화는 클래스를 인스턴스화하고 클래스 멤버에 클래스 인스턴스 및 패키지 참조를 저장 합니다.

클래스 생성자에서 명령 처리기 후크 ups 중 하나에 대해 살펴보겠습니다.

```csharp
_addGuidelineCommand =
    new OleMenuCommand(AddColumnGuideExecuted, null,
                       AddColumnGuideBeforeQueryStatus,
                       new CommandID(ColumnGuideCommands.CommandSet,
                                     cmdidAddColumnGuide));

```

만든는 `OleMenuCommand`합니다. Visual Studio는 Microsoft Office 명령 시스템을 사용합니다. 인스턴스화하는 OleMenuCommand 명령을 구현 하는 경우 키 인수 (`AddColumnGuideExecuted`), Visual Studio 메뉴 명령 사용 하 여 표시 되 면 호출할 함수입니다 (`AddColumnGuideBeforeQueryStatus`), 및 명령 id입니다. 명령이 보이지 않거나 메뉴의 특정 디스플레이 대 한 회색 자체 내릴 수 있도록 명령을 메뉴에 표시 하기 전에 쿼리 상태 함수를 호출 하는 visual studio (예를 들어, 사용 안 함 **복사** 선택 영역이 없는 경우), 해당 아이콘을 변경 하거나도 해당 이름 (예를 들어 추가 무언가를 제거)를 변경 하 고 등입니다. 명령 ID.vsct 파일에 선언 된 명령 ID와 일치 해야 합니다. 명령에 대 한 문자열을 설정 하 고 열 안내선 추가 명령을.vsct 파일 사이 ColumnGuideCommands.cs 일치 해야 합니다.

다음 줄에서는 사용자 명령 창 (아래 설명)를 통해 명령을 호출에 대 한 지원을 보여 줍니다.

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";
```

**상태를 쿼리**합니다. 쿼리 상태 함수 `AddColumnGuideBeforeQueryStatus` 및 `RemoveColumnGuideBeforeQueryStatus` 일부 설정 (예: 가이드 또는 최대 열 최대 수)를 확인 또는 제거할 열 가이드 경우. 조건이 올바른 경우 명령을 사용 합니다. 쿼리 상태 함수는 Visual Studio 메뉴의 각 명령에 대 한 메뉴 표시 될 때마다 실행 되므로 매우 효율적인 되도록 해야 합니다.

**AddColumnGuideExecuted 함수**합니다. 지침을 추가 하는 흥미로운 부분은 현재 편집기 뷰와 캐럿 위치를 파악 하는 합니다. 이 함수는 먼저 호출 `GetApplicableColumn` 에서는 명령 처리기의 이벤트 인수에 사용자가 제공한 인수를 확인 하 고 없는 경우 다음 함수 편집기의 뷰에서 검사 합니다.

```csharp
private int GetApplicableColumn(EventArgs e)
{
    var inValue = ((OleMenuCmdEventArgs)e).InValue as string;
    if (!string.IsNullOrEmpty(inValue))
    {
        int column;
        if (!int.TryParse(inValue, out column) || column < 0)
            throw new ArgumentException("Invalid column");
        return column;
    }

    return GetCurrentEditorColumn();
}

```

`GetCurrentEditorColumn` 자세히 살펴봅니다 가져오려는는 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> 코드의 보기입니다. 통해 추적 하는 경우 `GetActiveTextView`, `GetActiveView`, 및 `GetTextViewFromVsTextView`, 작업을 수행 하는 방법을 살펴볼 수 있습니다. 다음은 관련 코드를 추상화 하 고, 현재 선택 영역을 사용 하 여 시작을 차례로 선택의 프레임을 시작으로 프레임의 DocView 가져오기는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>를 가져오는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> 보기 호스트 가져오기는 IVsTextView에서 및 마지막으로 IWpfTextView:

```csharp
   IVsMonitorSelection selection =
       this.ServiceProvider.GetService(typeof(IVsMonitorSelection))
           as IVsMonitorSelection;
   object frameObj = null;

ErrorHandler.ThrowOnFailure(selection.GetCurrentElementValue(
                                (uint)VSConstants.VSSELELEMID.SEID_DocumentFrame,
                                out frameObj));

   IVsWindowFrame frame = frameObj as IVsWindowFrame;
   if (frame == null)
       <<do nothing>>;

...
   object pvar;
   ErrorHandler.ThrowOnFailure(frame.GetProperty((int)__VSFPROPID.VSFPROPID_DocView,
                                                  out pvar));

   IVsTextView textView = pvar as IVsTextView;
   if (textView == null)
   {
       IVsCodeWindow codeWin = pvar as IVsCodeWindow;
       if (codeWin != null)
       {
           ErrorHandler.ThrowOnFailure(codeWin.GetLastActiveView(out textView));
       }
   }

...
   if (textView == null)
       <<do nothing>>

   IVsUserData userData = textView as IVsUserData;
   if (userData == null)
       <<do nothing>>

   object objTextViewHost;
   if (VSConstants.S_OK
           != userData.GetData(Microsoft.VisualStudio.Editor.DefGuidList
                                                            .guidIWpfTextViewHost,
                                out objTextViewHost))
   {
       <<do nothing>>
   }

   IWpfTextViewHost textViewHost = objTextViewHost as IWpfTextViewHost;
   if (textViewHost == null)
       <<do nothing>>

   IWpfTextView textView = textViewHost.TextView;

```

IWpfTextView를 만든 후에 캐럿 배치 될 열을 가져올 수 있습니다.

```csharp
private static int GetCaretColumn(IWpfTextView textView)
{
    // This is the code the editor uses to populate the status bar.
    Microsoft.VisualStudio.Text.Formatting.ITextViewLine caretViewLine =
        textView.Caret.ContainingTextViewLine;
    double columnWidth = textView.FormattedLineSource.ColumnWidth;
    return (int)(Math.Round((textView.Caret.Left - caretViewLine.Left)
                                / columnWidth));
}

```

현재 열을 사용 하 여 수입 사용자가 클릭 하는 경우 코드 호출을 추가 하거나 열을 제거할 settings manager에서. Settings manager는 모든 이벤트를 발생 시킵니다. `ColumnGuideAdornment` 개체를 수신 합니다. 이벤트가 발생할 때 이러한 개체는 새 열 가이드 설정을 사용 하 여 해당 연결 된 텍스트를 보기를 업데이트 합니다.

## <a name="invoking-command-from-the-command-window"></a>명령 창에서 호출 명령
열 가이드 샘플을 사용 하면 확장성의 형태로 명령 창에서 두 명령을 호출할 수 있습니다. 사용 하는 경우는 **보기 &#124; 다른 Windows &#124; 명령 창** 명령, 명령 창에 표시 합니다. "편집"을 입력 하 여 명령 창 상호 작용할 수 있습니다 하 고 명령 이름 완성을 120 인수를 제공 해야 다음 키를 누릅니다.

```
> Edit.AddColumnGuide 120
>
```

.Vsct 파일 선언에이는이 사용 하도록 설정 하는 샘플의 부분을 `ColumnGuideCommands` 명령 처리기와 이벤트 인수를 확인 하는 명령 처리기 구현을 연결 하는 경우 클래스 생성자입니다.

본 "`<CommandFlag>CommandWellOnly</CommandFlag>`".vsct 파일 뿐만 아니라 편집 주 메뉴의 배치도에서는 표시 안 함 명령에는 **편집** UI 메뉴. 과 같은 이름을 제공 주 편집 메뉴에 있는 것 **Edit.AddColumnGuide**합니다. 명령을 그룹 4 개 명령은 편집 메뉴에서 직접 그룹을 배치를 보유 하는 선언:

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
             priority="0xB801">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />
      </Group>

```

단추 섹션에는 나중에 명령을 선언 `CommandWellOnly` 주 메뉴에서 보이지 않게 유지 하기 위해 사용 하 여 선언 `AllowParams`:

```xml
<Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide" 
        priority="0x0100" type="Button">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
  <Icon guid="guidImages" id="bmpPicAddGuide" />
  <CommandFlag>CommandWellOnly</CommandFlag>
  <CommandFlag>AllowParams</CommandFlag>

```

명령 처리기에 코드를 후크 살펴보았습니다를 `ColumnGuideCommands` 클래스 생성자에 허용 된 매개 변수의 설명을 제공 합니다.

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";

```

본 합니다 `GetApplicableColumn` 검사 함수 `OleMenuCmdEventArgs` 현재 열에 대 한 편집기의 보기를 확인 하기 전에 값:

```csharp
private int GetApplicableColumn(EventArgs e)
{
    var inValue = ((OleMenuCmdEventArgs)e).InValue as string;
    if (!string.IsNullOrEmpty(inValue))
    {
        int column;
        if (!int.TryParse(inValue, out column) || column < 0)
            throw new ArgumentException("Invalid column");
        return column;
    }

```

## <a name="trying-your-extension"></a>확장을 시도
이제 눌러도 **F5** 열 안내선 확장 프로그램을 실행 합니다. 텍스트 파일을 열고 안내선 추가, 제거 및 해당 색을 변경 하려면 편집기의 상황에 맞는 메뉴를 사용 합니다. 텍스트를 클릭 해야 (공백 문자는 줄의 끝을 통과 하는 데 사용) 열을 추가할 가이드 또는 편집기에 추가 줄에서 마지막 열입니다. 명령 창을 사용 하는 인수를 사용 하 여 명령을 호출 하는 경우 어디서 나 열 안내선을 추가할 수 있습니다.

다른 명령 배치를 시도, 이름 변경, 아이콘 및 등을 변경 하려는 경우 메뉴에서 최신 코드를 보여 주는 Visual Studio를 사용 하 여 문제가 발생 하면 디버깅 하는 실험 하이브를 재설정할 수 있습니다. 표시 된 **Windows 시작 메뉴** "재설정"을 입력 합니다. 에 대 한 검색 하 고 명령을 호출 **다음 Visual Studio 실험적 인스턴스 재설정**합니다. 이 확장에 대 한 구성 요소를 전체 실험적 레지스트리 하이브를 정리합니다. 하지 않는 구성 요소에서 설정을 정리 초과 하므로 Visual Studio의 실험 하이브에서를 종료할 때 사용 했던 모든 가이드 계속 그곳 코드 다음 시작 시 설정 저장소를 읽을 때.

## <a name="finished-code-project"></a>완성 된 코드 프로젝트
Visual Studio 확장성 샘플 GitHub 프로젝트 되 곧 하 고 완료 된 프로젝트로 표시 됩니다. 가리키도록 있을 경우이 항목에서는 업데이트 됩니다. 완성 된 샘플 프로젝트 다른 guid가 있고 명령 아이콘에 대 한 다른 비트맵 스트립을 갖습니다.

이 Visual Studio 갤러리를 사용 하 여 열 안내선 기능의 버전을 사용해 볼 수 있습니다[확장](https://visualstudiogallery.msdn.microsoft.com/da227a0b-0e31-4a11-8f6b-3a149cf2e459?SRC=Home)합니다.

## <a name="see-also"></a>관련 항목
[편집기 안쪽](../extensibility/inside-the-editor.md)
[편집기 및 언어 서비스 확장](../extensibility/extending-the-editor-and-language-services.md)
[언어 서비스 및 편집기 확장 지점](../extensibility/language-service-and-editor-extension-points.md) 
 [메뉴 및 명령 확장](../extensibility/extending-menus-and-commands.md)
[메뉴에 하위 메뉴 추가](../extensibility/adding-a-submenu-to-a-menu.md)
[편집기 항목 템플릿을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-an-editor-item-template.md)
