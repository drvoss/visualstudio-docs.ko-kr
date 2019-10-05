---
title: 도구 창에 검색 추가 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ab733e42e883816e5f9a6e8fb513bfd6267a9b5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309909"
---
# <a name="add-search-to-a-tool-window"></a>도구 창에 검색 추가
를 작성 하거나 도구 창 확장 프로그램에서 업데이트할 때 Visual Studio에서 다른 곳에 표시 되는 동일한 검색 기능을 추가할 수 있습니다. 이 기능에는 다음 기능이 포함 됩니다.

- 도구 모음 사용자 지정 영역에 항상 있는 검색 상자입니다.

- 자체 검색 상자에 중첩 하는 진행률 표시기입니다.

- 각 문자 (빠른 검색)을 입력 하거나 선택한 후에 결과 표시 하는 기능을 **Enter** 키 (요청 시 검색).

- 한 가장 최근에 검색 용어를 보여 주는 목록입니다.

- 특정 필드 또는 검색 대상의 측면에서 검색을 필터링 할 수 있습니다.

이 연습을 수행 하 여 다음 작업을 수행 하는 방법을 알아봅니다.

1. VSPackage 프로젝트를 만듭니다.

2. 읽기 전용 텍스트 상자를 사용 하 여 UserControl을 포함 하는 도구 창을 만듭니다.

3. 도구 창에 검색 상자를 추가 합니다.

4. 검색 구현을 추가 합니다.

5. 빠른 검색 및 진행률 표시줄의 표시를 사용 하도록 설정 합니다.

6. 추가 된 **대/소문자** 옵션입니다.

7. 추가 된 **도 줄만 검색** 필터입니다.

## <a name="to-create-a-vsix-project"></a>VSIX 프로젝트를 만들려면

1. 라는 VSIX 프로젝트를 만듭니다 `TestToolWindowSearch` 라는 도구 창 **TestSearch**합니다. 이 작업을 수행 하는 도움이 필요한 경우 참조 [도구 창으로 확장을 만드는](../extensibility/creating-an-extension-with-a-tool-window.md)합니다.

## <a name="to-create-a-tool-window"></a>도구 창을 만들려면

1. 에 `TestToolWindowSearch` 프로젝트를 열고는 *TestSearchControl.xaml* 파일입니다.

2. 기존 대체 `<StackPanel>` 읽기 전용을 추가 하는 다음 블록을 사용 하 여 블록 <xref:System.Windows.Controls.TextBox> 에 <xref:System.Windows.Controls.UserControl> 도구 창에서.

    ```xaml
    <StackPanel Orientation="Vertical">
        <TextBox Name="resultsTextBox" Height="800.0"
            Width="800.0"
            IsReadOnly="True">
        </TextBox>
    </StackPanel>
    ```

3. 에 *TestSearchControl.xaml.cs* 파일을 다음 추가 문을 사용 하 여:

    ```csharp
    using System.Text;
    ```

4. 제거 된 `button1_Click()` 메서드.

     에 **TestSearchControl** 클래스에 다음 코드를 추가 합니다.

     이 코드는 추가 공용 <xref:System.Windows.Controls.TextBox> 라는 속성이 **SearchResultsTextBox** 고 이라는 public 문자열 속성을 **SearchContent**합니다. 생성자 SearchResultsTextBox 텍스트 상자에 설정 되 고 SearchContent 줄 바꿈 구분 된 문자열 집합이 초기화 됩니다. 또한 입력란의 내용은 문자열 집합에 초기화 됩니다.

     [!code-csharp[ToolWindowSearch#1](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs)]
     [!code-vb[ToolWindowSearch#1](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]

5. 프로젝트를 빌드하고 디버깅을 시작합니다. Visual Studio의 실험적 인스턴스가 표시 됩니다.

6. 메뉴 모음에서 선택 **뷰** > **기타 Windows** > **TestSearch**합니다.

     도구 창이 표시 되지만 검색 컨트롤은 아직 표시 하지 않습니다.

## <a name="to-add-a-search-box-to-the-tool-window"></a>도구 창에 검색 상자를 추가 하려면

1. 에 *TestSearch.cs* 파일을 다음 코드를 추가 합니다 `TestSearch` 클래스. 코드를 재정의 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> 속성을 get 접근자를 반환 하도록 `true`합니다.

     검색을 사용 하도록 설정 하려면 재정의 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> 속성입니다. 합니다 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> 구현 클래스 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> 검색을 사용 하지 않습니다 하는 기본 구현을 제공 합니다.

    ```csharp
    public override bool SearchEnabled
    {
        get { return true; }
    }
    ```

2. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스가 표시 됩니다.

3. Visual Studio의 실험적 인스턴스에서에서 엽니다 **TestSearch**합니다.

     도구 창의 맨 위에 있는 검색 컨트롤을 사용 하 여 표시를 **검색** 워터 마크와는 돋보기 모양 아이콘이 있습니다. 그러나 검색 프로세스가 구현 되어 있지 않은 때문에 검색 아직 작동 하지 않습니다.

## <a name="to-add-the-search-implementation"></a>검색 구현을 추가 하려면
 검색을 사용 하는 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>처럼 이전 절차에서 도구 창을 검색 호스트를 만듭니다. 이 호스트를 설정 하 고 항상 백그라운드 스레드에서 발생 하는 검색 프로세스를 관리 합니다. 때문에 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> 클래스를 검색의 검색 호스트 및 설정의 생성을 관리, 사용자 검색 작업 만들기 및 검색 메서드를 제공 합니다. 검색 프로세스는 백그라운드 스레드에서 발생 하 고 도구 창 컨트롤에 대 한 호출이 UI 스레드에서 발생 합니다. 따라서를 사용 해야 합니다 [ThreadHelper.Invoke*](https://msdn.microsoft.com/data/ee197798(v=vs.85)) 컨트롤과 처리에서 모든 통화를 관리 하는 방법입니다.

1. 에 *TestSearch.cs* 파일을 다음 추가 `using` 문:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Runtime.InteropServices;
    using System.Text;
    using System.Windows.Controls;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.PlatformUI;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

2. 에 `TestSearch` 클래스를 다음 작업을 수행 하는 다음 코드를 추가 합니다.

    - 재정의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> 검색 작업을 만드는 방법.

    - 재정의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> 입력란의 상태를 복원 하는 방법입니다. 이 메서드는 검색 작업 및 사용자 설정 하거나 옵션 또는 필터 unsets 경우 사용자가 취소할 때 호출 됩니다. 둘 다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> 고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> UI 스레드에서 호출 됩니다. 따라서 이용 하 여 텍스트 상자에 액세스할 필요가 없습니다 합니다 [ThreadHelper.Invoke*](https://msdn.microsoft.com/data/ee197798(v=vs.85)) 메서드.

    - 이라고 하는 클래스를 만듭니다 `TestSearchTask` 에서 상속 되는 <xref:Microsoft.VisualStudio.Shell.VsSearchTask>의 기본 구현을 제공 하는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>합니다.

         `TestSearchTask`, 도구 창 참조 하는 개인 필드를 설정 하는 생성자입니다. 재정의 검색 메서드를 제공 하는 <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> 및 <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> 메서드. <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> 메서드는 검색 프로세스를 구현 하는 위치입니다. 이 프로세스는 검색을 수행 하 고 텍스트 상자에 검색 결과 표시 합니다. 검색 완료 되었음을 보고 합니다.이 메서드의 기본 클래스 구현을 호출을 포함 합니다.

    ```csharp
    public override IVsSearchTask CreateSearch(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback)
    {
        if (pSearchQuery == null || pSearchCallback == null)
            return null;
         return new TestSearchTask(dwCookie, pSearchQuery, pSearchCallback, this);
    }

    public override void ClearSearch()
    {
        TestSearchControl control = (TestSearchControl)this.Content;
        control.SearchResultsTextBox.Text = control.SearchContent;
    }

    internal class TestSearchTask : VsSearchTask
    {
        private TestSearch m_toolWindow;

        public TestSearchTask(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback, TestSearch toolwindow)
            : base(dwCookie, pSearchQuery, pSearchCallback)
        {
            m_toolWindow = toolwindow;
        }

        protected override void OnStartSearch()
        {
            // Use the original content of the text box as the target of the search.
            var separator = new string[] { Environment.NewLine };
            TestSearchControl control = (TestSearchControl)m_toolWindow.Content;
            string[] contentArr = control.SearchContent.Split(separator, StringSplitOptions.None);

            // Get the search option.
            bool matchCase = false;
            // matchCase = m_toolWindow.MatchCaseOption.Value;

                // Set variables that are used in the finally block.
                StringBuilder sb = new StringBuilder("");
                uint resultCount = 0;
                this.ErrorCode = VSConstants.S_OK;

                try
                {
                    string searchString = this.SearchQuery.SearchString;

                    // Determine the results.
                    uint progress = 0;
                    foreach (string line in contentArr)
                    {
                        if (matchCase == true)
                        {
                            if (line.Contains(searchString))
                            {
                                sb.AppendLine(line);
                                resultCount++;
                            }
                        }
                        else
                            {
                                if (line.ToLower().Contains(searchString.ToLower()))
                                {
                                    sb.AppendLine(line);
                                    resultCount++;
                                }
                            }

                            // SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));

                            // Uncomment the following line to demonstrate the progress bar.
                            // System.Threading.Thread.Sleep(100);
                        }
                    }
                    catch (Exception e)
                    {
                        this.ErrorCode = VSConstants.E_FAIL;
                    }
                    finally
                    {
                        ThreadHelper.Generic.Invoke(() =>
                        { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });

                        this.SearchResults = resultCount;
                    }

            // Call the implementation of this method in the base class.
            // This sets the task status to complete and reports task completion.
            base.OnStartSearch();
        }

        protected override void OnStopSearch()
        {
            this.SearchResults = 0;
        }
    }
    ```

3. 다음 단계를 수행 하 여 검색 구현 테스트:

    1. 프로젝트를 다시 작성 하 고 디버깅을 시작 합니다.

    2. Visual Studio의 실험적 인스턴스에서 도구 창을 열고 다시 검색 창에 검색 텍스트를 입력 하 고 클릭 **ENTER**합니다.

         올바른 결과 표시 됩니다.

## <a name="to-customize-the-search-behavior"></a>검색 동작을 사용자 지정
 검색 설정을 변경 하 여 검색 컨트롤의 표시 방법을 검색을 수행 하는 방법에 다양 한 변화를 만들 수 있습니다. 예를 들어, 워터 마크 (검색 상자에 표시 되는 기본 텍스트), 최소 및 검색 컨트롤의 최대 너비 및 진행률 표시줄을 표시할지 여부를 변경할 수 있습니다. 또한 시점 (요청 또는 빠른 검색)에 표시할 검색 결과 시작 및 최근에 검색 한 용어 목록을 표시할지 여부를 변경할 수 있습니다. 설정의 전체 목록을 찾을 수 있습니다는 <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource> 클래스입니다.

1. 에 * TestSearch.cs* 파일을 다음 코드를 추가 합니다 `TestSearch` 클래스. 이 코드에서는 주문형으로 검색 하는 대신 빠른 검색 (사용자 클릭 없는 의미 **ENTER**). 코드를 재정의 합니다 `ProvideSearchSettings` 에서 메서드는 `TestSearch` 기본 설정을 변경 하는 데 필요한 클래스입니다.

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}
    ```

2. 새 테스트 솔루션을 다시 작성 하 고 디버거를 다시 시작 하 여 설정 합니다.

     검색 결과 검색 상자에 문자를 입력 하면 될 때마다 표시 됩니다.

3. 에 `ProvideSearchSettings` 메서드를 진행률 표시줄을 표시할 수 있는 다음 줄을 추가 합니다.

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
             (uint)VSSEARCHSTARTTYPE.SST_INSTANT);
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchProgressTypeProperty.Name,
             (uint)VSSEARCHPROGRESSTYPE.SPT_DETERMINATE);
    }
    ```

     표시할 진행률 표시줄에 대 한 진행률을 보고 해야 합니다. 진행률을 보고 하기 위해 다음 코드를 주석 처리를 제거 합니다 `OnStartSearch` 메서드는 `TestSearchTask` 클래스:

    ```csharp
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));
    ```

4. 다음 줄의 주석 처리 제거 진행률 정도의 처리 속도가 느린 막대를 표시 합니다 `OnStartSearch` 메서드는 `TestSearchTask` 클래스:

    ```csharp
    System.Threading.Thread.Sleep(100);
    ```

5. 솔루션 다시 빌드 및 디버깅 하기 시작 하 여 새 설정을 테스트 합니다.

     진행률 표시줄으로 표시 됩니다 검색 창 (검색 텍스트 상자 아래 파란색 선) 될 때마다 검색을 수행 하면 됩니다.

## <a name="to-enable-users-to-refine-their-searches"></a>검색을 구체화할 수 있도록 하려면
 와 같은 옵션을 사용 하 여 검색을 구체화할 수 있습니다 **대/소문자 구분** 하거나 **단어 단위로**합니다. 확인란 또는 단추로 표시 되는 명령으로 표시 하는 옵션, 부울 수 있습니다. 이 연습에서는 부울 옵션을 만들어야 합니다.

1. 에 *TestSearch.cs* 파일을 다음 코드를 추가 합니다 `TestSearch` 클래스. 코드를 재정의 합니다 `SearchOptionsEnum` 메서드를 지정된 된 옵션이 설정 되었는지 아니면 해제 여부를 검색할 검색 구현을 허용 합니다. 코드 `SearchOptionsEnum` 사례를 일치 하는 옵션이 추가 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> 열거자입니다. 대/소문자를 일치 하는 옵션은 또한으로 사용할 수는 `MatchCaseOption` 속성입니다.

    ```csharp
    private IVsEnumWindowSearchOptions m_optionsEnum;
    public override IVsEnumWindowSearchOptions SearchOptionsEnum
    {
        get
        {
            if (m_optionsEnum == null)
            {
                List<IVsWindowSearchOption> list = new List<IVsWindowSearchOption>();

                list.Add(this.MatchCaseOption);

                m_optionsEnum = new WindowSearchOptionEnumerator(list) as IVsEnumWindowSearchOptions;
            }
            return m_optionsEnum;
        }
    }

    private WindowSearchBooleanOption m_matchCaseOption;
    public WindowSearchBooleanOption MatchCaseOption
    {
        get
        {
            if (m_matchCaseOption == null)
            {
                m_matchCaseOption = new WindowSearchBooleanOption("Match case", "Match case", false);
            }
            return m_matchCaseOption;
        }
    }
    ```

2. 에 `TestSearchTask` 클래스에 다음 주석 줄를 `OnStartSearch` 메서드:

    ```csharp
    matchCase = m_toolWindow.MatchCaseOption.Value;
    ```

3. 옵션을 테스트 합니다.

    1. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스가 표시 됩니다.

    2. 도구 창에서 입력란의 오른쪽에서 아래쪽 화살표를 선택 합니다.

         합니다 **대/소문자** 확인란이 표시 됩니다.

    3. 선택 된 **대/소문자** 확인란을 선택한 다음 몇 가지 검색을 수행 합니다.

## <a name="to-add-a-search-filter"></a>검색 필터를 추가 하려면
 검색 대상 집합을 정의 하는 사용자를 허용 하는 검색 필터를 추가할 수 있습니다. 예를 들어, 파일 탐색기에서 파일을 수정한 최근 날짜 및 해당 파일 이름 확장명으로 필터링 할 수 있습니다. 이 연습에서는 줄만 필터를 추가 합니다. 사용자가 해당 필터를 선택 하는 경우 검색 호스트 검색 쿼리를 지정 하는 문자열을 추가 합니다. 그런 다음 검색 메서드 내에서 이러한 문자열을 식별 하 고 검색 대상을 적절 하 게 필터링 수 있습니다.

1. 에 *TestSearch.cs* 파일을 다음 코드를 추가 합니다 `TestSearch` 클래스. 코드를 구현 `SearchFiltersEnum` 더하여는 <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter> 지정도 줄만 표시 되도록 검색 결과 필터링 하는 합니다.

    ```csharp
    public override IVsEnumWindowSearchFilters SearchFiltersEnum
    {
        get
        {
            List<IVsWindowSearchFilter> list = new List<IVsWindowSearchFilter>();
            list.Add(new WindowSearchSimpleFilter("Search even lines only", "Search even lines only", "lines", "even"));
            return new WindowSearchFilterEnumerator(list) as IVsEnumWindowSearchFilters;
        }
    }

    ```

     검색 컨트롤 검색 필터를 표시 하는 이제 `Search even lines only`합니다. 사용자가 필터 문자열을 선택 하는 경우 `lines:"even"` 검색 상자에 표시 됩니다. 검색 조건을 다른 필터와 같은 시간에 나타날 수 있습니다. 검색 문자열은 필터 또는 둘 다 후 필터를 하기 전에 나타날 수 있습니다.

2. 에 *TestSearch.cs* 파일에서 다음 메서드를 추가 합니다 `TestSearchTask` 클래스에 있는 `TestSearch` 클래스. 이러한 메서드를 지원 합니다 `OnStartSearch` 메서드를 다음 단계에서 수정할 수 있습니다.

    ```csharp
    private string RemoveFromString(string origString, string stringToRemove)
    {
        int index = origString.IndexOf(stringToRemove);
        if (index == -1)
            return origString;
        else 
             return (origString.Substring(0, index) + origString.Substring(index + stringToRemove.Length)).Trim();
    }

    private string[] GetEvenItems(string[] contentArr)
    {
        int length = contentArr.Length / 2;
        string[] evenContentArr = new string[length];

        int indexB = 0;
        for (int index = 1; index < contentArr.Length; index += 2)
        {
            evenContentArr[indexB] = contentArr[index];
            indexB++;
        }

        return evenContentArr;
    }
    ```

3. 에 `TestSearchTask` 클래스를 업데이트 합니다 `OnStartSearch` 메서드를 다음 코드로 합니다. 이 변경 된 필터를 지원 하기 위한 코드를 업데이트 합니다.

    ```csharp
    protected override void OnStartSearch()
    {
        // Use the original content of the text box as the target of the search. 
        var separator = new string[] { Environment.NewLine };
        string[] contentArr = ((TestSearchControl)m_toolWindow.Content).SearchContent.Split(separator, StringSplitOptions.None);

        // Get the search option. 
        bool matchCase = false;
        matchCase = m_toolWindow.MatchCaseOption.Value;

        // Set variables that are used in the finally block.
        StringBuilder sb = new StringBuilder("");
        uint resultCount = 0;
        this.ErrorCode = VSConstants.S_OK;

        try
        {
            string searchString = this.SearchQuery.SearchString;

            // If the search string contains the filter string, filter the content array. 
            string filterString = "lines:\"even\"";

            if (this.SearchQuery.SearchString.Contains(filterString))
            {
                // Retain only the even items in the array.
                contentArr = GetEvenItems(contentArr);

                // Remove 'lines:"even"' from the search string.
                searchString = RemoveFromString(searchString, filterString);
            }

            // Determine the results. 
            uint progress = 0;
            foreach (string line in contentArr)
            {
                if (matchCase == true)
                {
                    if (line.Contains(searchString))
                    {
                        sb.AppendLine(line);
                        resultCount++;
                    }
                }
                else
                {
                    if (line.ToLower().Contains(searchString.ToLower()))
                    {
                        sb.AppendLine(line);
                        resultCount++;
                    }
                }

                SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));

                // Uncomment the following line to demonstrate the progress bar. 
                // System.Threading.Thread.Sleep(100);
            }
        }
        catch (Exception e)
        {
            this.ErrorCode = VSConstants.E_FAIL;
        }
        finally
        {
            ThreadHelper.Generic.Invoke(() =>
            { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });

            this.SearchResults = resultCount;
        }

        // Call the implementation of this method in the base class. 
        // This sets the task status to complete and reports task completion. 
        base.OnStartSearch();
    }
    ```

4. 코드를 테스트 합니다.

5. 프로젝트를 빌드하고 디버깅을 시작합니다. Visual Studio의 실험적 인스턴스에서 도구 창을 열고 하 고 검색 컨트롤에 있는 아래쪽 화살표를 선택 합니다.

     합니다 **대/소문자 구분** 확인란 및 **도 줄만 검색** 필터 표시 합니다.

6. 필터를 선택 합니다.

     검색 상자에 **줄: "짝수"** , 다음과 같은 결과가 나타납니다.

     좋은 2

     올바른 4

     6 goodbye

7. 삭제할 `lines:"even"` 검색 상자에서 선택 합니다 **대/소문자** 확인란을 선택한 다음 입력 `g` 검색 상자에 합니다.

     다음과 같은 결과가 나타납니다.

     1 이동

     좋은 2

     5 goodbye

8. 검색 상자 오른쪽에 있는 X를 선택 합니다.

     검색의 선택을 취소 하 고 원래 내용을 표시 합니다. 그러나 합니다 **대/소문자** 확인란을 선택 계속 합니다.