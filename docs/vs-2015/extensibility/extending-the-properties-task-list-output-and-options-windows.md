---
title: 확장 속성, 작업 목록, 출력 및 옵션 Windows | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- properties pane
- task list
- output window
- properties window
- tutorials
- tool windows
ms.assetid: 06990510-5424-44b8-9fd9-6481acec5c76
caps.latest.revision: 38
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cf42be1e62bfb4895d29a61fcadc221d5c14bec9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443912"
---
# <a name="extending-the-properties-task-list-output-and-options-windows"></a>속성, 작업 목록, 출력 및 옵션 창 확장
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio의 모든 도구 창에 액세스할 수 있습니다. 이 연습에서는 새 도구 창에 대 한 정보를 통합 하는 방법을 보여 줍니다 **옵션** 페이지 및의 새 설정 합니다 **속성** 페이지, 그리고에 쓰는 방법은 **작업목록** 하 고 **출력** windows.  
  
## <a name="prerequisites"></a>전제 조건  
 Visual Studio 2015부터 수행 설치 하면 Visual Studio SDK 다운로드 센터에서. Visual Studio 설치에서 선택적 기능으로 포함 됩니다. 또한 VS SDK를 나중에 설치할 수 있습니다. 자세한 내용은 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)합니다.  
  
## <a name="create-an-extension-with-a-tool-window"></a>도구 창으로 확장 프로그램을 만들려면  
  
1. 라는 프로젝트를 만듭니다 **TodoList** 라는 사용자 지정 도구 창 항목 템플릿을 VSIX 템플릿을 사용 하 여 추가한 **TodoWindow**합니다.  
  
    > [!NOTE]
    > 도구 창을 사용 하 여 확장을 만드는 방법에 대 한 자세한 내용은 참조 하세요. [도구 창으로 확장을 만드는](../extensibility/creating-an-extension-with-a-tool-window.md)합니다.  
  
## <a name="set-up-the-tool-window"></a>도구 창 설정  
 새 ToDo 항목을 목록에 새 항목을 추가 하는 단추 및 목록에 항목을 표시 하는 목록 상자를 입력 하는 입력란을 추가 합니다.  
  
1. TodoWindow.xaml, 단추, 텍스트 상자 및 StackPanel 컨트롤 UserControl에서 삭제 합니다.  
  
    > [!NOTE]
    > 이 삭제 되지 않습니다 합니다 **button1_Click** 나중에 재사용 하는 이벤트 처리기입니다.  
  
2. **모든 WPF 컨트롤** 섹션을 **도구 상자**, 끌어를 **캔버스** 그리드 컨트롤.  
  
3. 끌어서를 **텍스트 상자**, **단추**, 및 **ListBox** 캔버스에 있습니다. ListBox, 아래의 아래 그림과 같이 창의 나머지 부분을 채웁니다 및 텍스트 상자 및 단추를 같은 수준에 있도록 요소를 정렬 합니다.  
  
     ![도구 창을 완료](../extensibility/media/t5-toolwindow.png "T5-도구 창")  
  
4. XAML 창에서 단추를 찾고 해당 콘텐츠 속성을 설정 **추가**합니다. 단추 컨트롤에 단추 이벤트 처리기를 추가 하 여 다시 연결을 `Click="button1_Click"` 특성입니다. 캔버스 블록은 다음과 같이 표시 됩니다.  
  
    ```xml  
    <Canvas HorizontalAlignment="Left" Width="306">  
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>  
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>  
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>  
    </Canvas>  
    ```  
  
#### <a name="customize-the-constructor"></a>생성자는 사용자 지정  
  
1. TodoWindowControl.xaml.cs 파일에 다음 추가 문을 사용 하 여:  
  
    ```csharp  
    using System;  
    ```  
  
2. TodoWindow에 대 한 공용 참조를 추가 하 고 TodoWindow 매개 변수를 사용 하 여 TodoWindowControl 생성자가 있습니다. 코드는 다음과 같습니다.  
  
    ```csharp  
    public TodoWindow parent;  
  
    public TodoWindowControl(TodoWindow window)  
    {  
        InitializeComponent();  
        parent = window;  
    }  
    ```  
  
3. TodoWindow.cs, TodoWindowControl TodoWindow 매개 변수를 포함 하는 생성자를 변경 합니다. 코드는 다음과 같습니다.  
  
    ```csharp  
    public TodoWindow() : base(null)  
    {  
        this.Caption = "TodoWindow";  
        this.BitmapResourceID = 301;  
        this.BitmapIndex = 1;  
  
         this.Content = new TodoWindowControl(this);  
    }  
    ```  
  
## <a name="create-an-options-page"></a>옵션 페이지 만들기  
 페이지에 제공할 수 있습니다 합니다 **옵션** 대화 상자의 사용자가 도구 창에 대 한 설정을 변경할 수 있도록 합니다. 옵션 페이지 만들기 옵션 및 TodoListPackage.cs 또는 TodoListPackage.vb 파일에서 항목을 설명 하는 두 클래스에 필요 합니다.  
  
1. 라는 클래스를 추가 `ToolsOptions.cs`합니다. 상속 ToolsOptions 클래스 <xref:Microsoft.VisualStudio.Shell.DialogPage>합니다.  
  
   ```csharp  
   class ToolsOptions : DialogPage  
   {  
   }  
   ```  
  
2. 다음 추가 문을 사용 하 여:  
  
   ```csharp  
   using Microsoft.VisualStudio.Shell;  
   ```  
  
3. 이 연습의 옵션 페이지 DaysAhead 라는 하나의 옵션만을 제공 합니다. 라는 private 필드를 추가 **daysAhead** 속성 및 이름이 **DaysAhead** ToolsOptions 클래스:  
  
   ```csharp  
   private double daysAhead;  
  
   public double DaysAhead  
   {  
       get { return daysAhead; }  
       set { daysAhead = value; }  
   }  
   ```  
  
   이제 해야 프로젝트가 옵션 페이지를 인식 합니다.  
  
#### <a name="make-the-options-page-available-to-users"></a>사용자에 게 옵션 페이지를 사용할 수 있도록  
  
1. TodoWindowPackage.cs, 추가 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> TodoWindowPackage 클래스:  
  
    ```csharp  
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]  
    ```  
  
2. ProvideOptionPage 생성자의 첫 번째 매개 변수는 이전에 만들어진 ToolsOptions 클래스의 형식입니다. 범주 이름이 "ToDo" 두 번째 매개 변수를 **옵션** 대화 상자. 세 번째 매개 변수를 "일반"의 이름인의 하위 범주는 **옵션** 옵션 페이지를 사용할 수 있는 대화 상자. 다음 두 매개 변수는 문자열에 대 한 리소스 Id 첫 번째 범주의 이름을 이며 두 번째 하위 범주의 이름입니다. 마지막 매개 변수는 자동화를 사용 하 여이 페이지에 액세스할 수 있는지 여부를 결정 합니다.  
  
     사용자가 옵션 페이지를 열면 다음 그림과 비슷해야 합니다.  
  
     ![옵션 페이지](../extensibility/media/t5optionspage.gif "T5OptionsPage")  
  
     범주 **ToDo** 및 하위 범주 **일반**합니다.  
  
## <a name="make-data-available-to-the-properties-window"></a>속성 창에 데이터를 사용할 수 있도록  
 할 일 목록에 개별 항목에 대 한 정보를 저장 하는 TodoItem 이라는 클래스를 만들어 할 일 목록 정보를 사용할 수 있습니다.  
  
1. 라는 클래스를 추가 `TodoItem.cs`합니다.  
  
     도구 창이 사용자에 게 제공 되 면 ListBox에서 항목 TodoItems로 표현 됩니다. 사용자가 목록 상자에서 이러한 항목 중 하나를 선택 합니다 **속성** 창 항목에 대 한 정보에 표시 됩니다.  
  
     데이터에서 사용할 수 있도록 하는 **속성** 두 가지 특별 한 특성이 있는 공용 속성으로 데이터를 설정 창 `Description` 및 `Category`합니다. `Description` 맨 아래에 표시 되는 텍스트를 **속성** 창입니다. `Category` 여기서 속성이 표시 되는 시기를 결정 합니다 **속성** 창에 표시 되는 **항목별** 보기. 다음 그림에는 **속성** 창은 **항목별** 보기를 **이름** 속성에는 **ToDo 필드** 범주는 선택 및 설명 합니다 **이름을** 속성 창의 맨 아래에 표시 됩니다.  
  
     ![속성 창](../extensibility/media/t5properties.png "T5Properties")  
  
2. 다음 추가 문을 TodoItem.cs 파일을 사용 합니다.  
  
    ```csharp  
    using System.ComponentModel;  
    using System.Windows.Forms;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3. 추가 된 `public` 액세스 한정자를 클래스 선언 합니다.  
  
    ```csharp  
    public class TodoItem  
    {  
    }  
    ```  
  
     이름 및 DueDate 두 속성을 추가 합니다. 하겠습니다 CheckForErrors() 고 UpdateList() 나중입니다.  
  
    ```csharp  
    public class TodoItem  
    {  
        private TodoWindowControl parent;  
        private string name;  
        [Description("Name of the ToDo item")]  
        [Category("ToDo Fields")]  
        public string Name  
        {  
            get { return name; }  
            set  
            {  
                name = value;  
                parent.UpdateList(this);  
            }  
        }  
  
        private DateTime dueDate;  
        [Description("Due date of the ToDo item")]  
        [Category("ToDo Fields")]  
        public DateTime DueDate  
        {  
            get { return dueDate; }  
            set  
            {  
                dueDate = value;  
                parent.UpdateList(this);  
                parent.CheckForErrors();  
            }  
        }  
    }  
    ```  
  
4. 사용자 정의 컨트롤에 대 한 개인 참조를 추가 합니다. 사용자 정의 컨트롤 및 두 일 항목에 대 한 이름을 사용 하는 생성자를 추가 합니다. DaysAhead에 대 한 값을 찾으려면 해당 옵션 페이지 속성을 가져옵니다.  
  
    ```csharp  
    private TodoWindowControl parent;  
  
    public TodoItem(TodoWindowControl control, string itemName)  
    {  
        parent = control;  
        name = itemName;  
        dueDate = DateTime.Now;  
  
        double daysAhead = 0;  
        IVsPackage package = parent.parent.Package as IVsPackage;  
        if (package != null)  
        {  
            object obj;  
            package.GetAutomationObject("ToDo.General", out obj);  
  
            ToolsOptions options = obj as ToolsOptions;  
            if (options != null)  
            {  
                daysAhead = options.DaysAhead;  
            }  
        }  
  
        dueDate = dueDate.AddDays(daysAhead);  
    }  
    ```  
  
5. 때문에 인스턴스를 `TodoItem` 클래스 목록 상자에 저장 되 고 목록 상자를 호출 합니다는 `ToString` 함수를 오버 로드 해야는 `ToString` 함수. 클래스의 종료 되기 전에 생성자 후 TodoItem.cs에 다음 코드를 추가 합니다.  
  
    ```csharp  
    public override string ToString()  
    {  
        return name + " Due: " + dueDate.ToShortDateString();  
    }  
    ```  
  
6. TodoWindowControl.xaml.cs, 스텁 메서드 TodoWindowControl 클래스에 추가 합니다 `CheckForError` 고 `UpdateList` 메서드. 파일의 종료 되기 전에 ProcessDialogChar 후 넣습니다.  
  
    ```csharp  
    public void CheckForErrors()  
    {  
    }  
    public void UpdateList(TodoItem item)  
    {  
    }  
    ```  
  
     `CheckForError` 메서드 부모 개체에 동일한 이름을 가진 메서드를 호출 하 고 해당 메서드는 오류 발생 했을 고 올바르게 처리 하는지 여부를 확인 합니다. `UpdateList` 는 메서드를 호출한 경우; 메서드는 부모 컨트롤의 목록 상자를 업데이트 합니다 `Name` 및 `DueDate` 이 클래스의 변경 내용에 대 한 속성입니다. 나중에 구현 됩니다.  
  
## <a name="integrate-into-the-properties-window"></a>속성 창에 통합  
 이제 목록 상자에 연결 됩니다을 관리 하는 코드를 작성 합니다 **속성** 창입니다.  
  
 단추를 변경 해야 처리기 텍스트를 읽기, TodoItem을 만들기를 클릭 하 고 목록 상자에 추가 합니다.  
  
1. 기존 대체 `button1_Click` 새 TodoItem을 만들고 목록 상자에 추가 하는 코드를 사용 하 여 함수입니다. 나중에 정의 되는 TrackSelection() 호출 합니다.  
  
    ```csharp  
    private void button1_Click(object sender, RoutedEventArgs e)  
    {  
        if (textBox.Text.Length > 0)  
        {  
            var item = new TodoItem(this, textBox.Text);  
            listBox.Items.Add(item);  
            TrackSelection();  
            CheckForErrors();  
        }  
    }  
    ```  
  
2. 디자인 뷰에서 ListBox 컨트롤을 선택 합니다. 에 **속성** 창 클릭 합니다 **이벤트 처리기** 단추 및 SelectionChanged 이벤트를 찾습니다. 사용 하 여 텍스트 상자에 입력 **listBox_SelectionChanged**합니다. 이렇게 SelectionChanged 처리기에 대 한 스텁을 추가 하 고 이벤트에 할당 합니다.  
  
3. TrackSelection() 메서드를 구현 합니다. 가져오려는 해야 하므로 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> 해야 서비스를 <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> 는 TodoWindowControl 액세스할 수 있습니다. TodoWindow 클래스에 다음 메서드를 추가 합니다.  
  
    ```  
    internal object GetVsService(Type service)  
    {  
        return GetService(service);  
    }  
    ```  
  
4. 다음 추가 TodoWindowControl.xaml.cs 문을 사용 하 여:  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
5. SelectionChanged 처리기에서 다음과 같이 입력 합니다.  
  
    ```  
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)  
    {  
        TrackSelection();  
    }  
    ```  
  
6. 이제 TrackSelection 함수를 사용 하 여 통합을 제공 하는 입력 된 **속성** 창입니다. 이 함수는 목록 상자에 항목을 추가 하거나가 ListBox에서 항목을 클릭할 때 호출 됩니다. SelectionContainer에는 ListBox의 콘텐츠를 추가 하 고 전달 하려면 SelectionContainer 합니다 **속성** 창의 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> 이벤트 처리기입니다. TrackSelection 서비스 사용자 인터페이스 (UI)에서 선택한 개체를 추적 하 고 해당 속성 표시  
  
    ```csharp  
    private SelectionContainer mySelContainer;  
    private System.Collections.ArrayList mySelItems;  
    private IVsWindowFrame frame = null;  
  
    private void TrackSelection()  
    {  
        if (frame == null)  
        {  
            var shell = parent.GetVsService(typeof(SVsUIShell)) as IVsUIShell;  
            if (shell != null)  
            {  
                var guidPropertyBrowser = new  
                Guid(ToolWindowGuids.PropertyBrowser);  
                shell.FindToolWindow((uint)__VSFINDTOOLWIN.FTW_fForceCreate,  
                ref guidPropertyBrowser, out frame);  
            }  
        }  
        if (frame != null)  
            {  
                frame.Show();  
            }  
        if (mySelContainer == null)  
        {  
            mySelContainer = new SelectionContainer();  
        }  
  
        mySelItems = new System.Collections.ArrayList();  
  
        var selected = listBox.SelectedItem as TodoItem;  
        if (selected != null)  
        {  
            mySelItems.Add(selected);  
        }  
  
        mySelContainer.SelectedObjects = mySelItems;  
  
        ITrackSelection track = parent.GetVsService(typeof(STrackSelection))  
                                as ITrackSelection;  
        if (track != null)  
        {  
            track.OnSelectChange(mySelContainer);  
        }  
    }  
    ```  
  
     클래스 했으므로 합니다 **속성** 창을 사용 하 여 수를 통합할 수 있습니다 합니다 **속성** 도구 창 사용 하 여 창. 도구 창의 ListBox에서 항목을 마우스 오른쪽 단추로 클릭할 때 합니다 **속성** 창 적절 하 게 업데이트 해야 합니다. 마찬가지로, 사용자의 ToDo 항목을 변경 합니다 **속성** 창 연결된 된 항목을 업데이트 해야 합니다.  
  
7. 이제 TodoWindowControl.xaml.cs에서 UpdateList 함수 코드의 나머지 부분을 추가 합니다. 삭제 하 고 다시 목록 상자에서 수정 된 TodoItem을 추가 해야 합니다.  
  
    ```csharp  
    public void UpdateList(TodoItem item)  
    {  
        var index = listBox.SelectedIndex;  
        listBox.Items.RemoveAt(index);  
        listBox.Items.Insert(index, item);  
        listBox.SelectedItem = index;  
    }  
    ```  
  
8. 코드를 테스트 합니다. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스에서 표시 됩니다.  
  
9. 엽니다는 **도구 / 옵션** 페이지입니다. 왼쪽된 창에서 ToDo 범주를 표시 되어야 합니다. 범주는 사전순으로 나열 됩니다, 그리고 따라서 Ts 아래를 확인 합니다.  
  
10. Todo 옵션 페이지의 DaysAhead 속성이로 설정 되어 표시 됩니다 **0**합니다. 로 변경 **2**합니다.  
  
11. 뷰 / 기타 Windows 메뉴를 열고 **TodoWindow**합니다. 형식 **EndDate** 텍스트 상자를 클릭 **추가**합니다.  
  
12. 목록 상자에서 이틀 오늘 이후의 날짜를 표시 되어야 합니다.  
  
## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>텍스트를 출력 창과 작업 목록에 항목 추가  
 에 대 한 합니다 **작업 목록**, 태스크인 형식의 새 개체를 만들고 해당 작업 개체를 추가 합니다 **작업 목록** 추가 메서드를 호출 하 여 합니다. 쓸 합니다 **출력** 창 개체를 가져오려면 해당 GetPane 메서드를 호출 하면 창과 창 개체의 OutputString 메서드를 호출 합니다.  
  
1. TodoWindowControl.xaml.cs에서를 `button1_Click` 메서드를 가져오는 코드를 추가 합니다 **일반** 창을 **출력** 창 (즉, 기본값) 쓸. 메서드는 다음과 같습니다.  
  
    ```csharp  
    private void button1_Click(object sender, EventArgs e)  
    {  
        if (textBox.Text.Length > 0)  
        {  
            var item = new TodoItem(this, textBox.Text);  
            listBox.Items.Add(item);  
  
            var outputWindow = parent.GetVsService(  
                typeof(SVsOutputWindow)) as IVsOutputWindow;  
            IVsOutputWindowPane pane;  
            Guid guidGeneralPane = VSConstants.GUID_OutWindowGeneralPane;  
            outputWindow.GetPane(ref guidGeneralPane, out pane);  
            if (pane != null)  
            {  
                 pane.OutputString(string.Format(  
                    "To Do item created: {0}\r\n",  
                 item.ToString()));  
        }  
            TrackSelection();  
            CheckForErrors();  
        }  
    }  
    ```  
  
2. 작업 목록에 항목을 추가 하려면를 TodoWindowControl 클래스에 중첩된 된 클래스를 추가 합니다. 중첩된 클래스에서 파생 해야 <xref:Microsoft.VisualStudio.Shell.TaskProvider>합니다. TodoWindowControl 클래스의 끝에 다음 코드를 추가 합니다.  
  
    ```csharp  
    [Guid("72de1eAD-a00c-4f57-bff7-57edb162d0be")]  
    public class TodoWindowTaskProvider : TaskProvider  
    {  
        public TodoWindowTaskProvider(IServiceProvider sp)  
            : base(sp)  
        {  
        }  
    }  
    ```  
  
3. 다음 TodoWindowControl 클래스 CreateProvider() 메서드와 TodoTaskProvider에 대 한 개인 참조를 추가 합니다. 코드는 다음과 같습니다.  
  
    ```csharp  
    private TodoWindowTaskProvider taskProvider;  
    private void CreateProvider()  
    {  
        if (taskProvider == null)  
        {  
            taskProvider = new TodoWindowTaskProvider(parent);  
            taskProvider.ProviderName = "To Do";  
        }  
    }  
    ```  
  
4. 작업 목록, 지우는 ClearError() 및 ReportError() 작업 목록에 항목을 추가 하는 TodoWindowControl 클래스에 추가 합니다.  
  
    ```csharp  
    private void ClearError()  
    {  
        CreateProvider();  
        taskProvider.Tasks.Clear();  
    }  
    private void ReportError(string p)  
    {  
        CreateProvider();  
        var errorTask = new Task();  
        errorTask.CanDelete = false;  
        errorTask.Category = TaskCategory.Comments;  
        errorTask.Text = p;  
  
        taskProvider.Tasks.Add(errorTask);  
  
        taskProvider.Show();  
  
        var taskList = parent.GetVsService(typeof(SVsTaskList))  
            as IVsTaskList2;  
        if (taskList == null)  
        {  
            return;  
        }  
  
        var guidProvider = typeof(TodoWindowTaskProvider).GUID;  
         taskList.SetActiveProvider(ref guidProvider);  
    }  
    ```  
  
5. 이제 다음과 같이 CheckForErrors 메서드를 구현 합니다.  
  
    ```csharp  
    public void CheckForErrors()  
    {  
        foreach (TodoItem item in listBox.Items)  
        {  
            if (item.DueDate < DateTime.Now)  
            {  
                ReportError("To Do Item is out of date: "  
                    + item.ToString());  
            }  
        }  
    }  
    ```  
  
## <a name="trying-it-out"></a>사용해  
  
1. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스가 표시 됩니다.  
  
2. TodoWindow 엽니다 (**보기 / 다른 Windows / TodoWindow**).  
  
3. 텍스트 상자에 입력 하 고 클릭 **추가**합니다.  
  
     기한이 오늘 목록 상자에 추가 된 후 2 일입니다. 오류가 생성 되 고 **작업 목록** (**보기 / 작업 목록**) 없는 항목이 있어야 합니다.  
  
4. 이제에서 설정을 변경 합니다 **도구 / 옵션 / ToDo** 페이지에서 **2** 돌아가기 **0**.  
  
5. 입력에 다른 항목의 **TodoWindow** 클릭 하 고 **추가** 다시 합니다. 이때 오류가 및 항목의 **작업 목록**합니다.  
  
     항목을 추가 하면 초기 날짜 이제 2 일에 설정 됩니다.  
  
6. 에 **보기** 메뉴에서 클릭 **출력** 열려는 합니다 **출력** 창.  
  
     항목을 추가, 메시지에 표시 됩니다 될 때마다 확인 합니다 **작업 목록** 창.  
  
7. ListBox의 항목 중 하나를 클릭 합니다.  
  
     합니다 **속성** 창 항목에 대 한 두 가지 속성을 표시 합니다.  
  
8. 속성 중 하나를 변경 하 고 enter 키를 누릅니다.  
  
     항목 목록 상자에서 업데이트 됩니다.
