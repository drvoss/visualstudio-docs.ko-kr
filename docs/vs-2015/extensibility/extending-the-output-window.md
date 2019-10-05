---
title: 출력 창 확장 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2788903c60564d501770616fbe3ad2335e60a250
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204433"
---
# <a name="extending-the-output-window"></a>출력 창 확장
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

합니다 **출력** 창 집합이 읽기/쓰기 텍스트 창이 있습니다. Visual Studio에 기본 제공 이러한 창이 있습니다. **빌드**는 프로젝트에서 빌드에 대 한 메시지를 통신 하 고 **일반**는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE에 대 한 메시지를 통신 합니다. 프로젝트에 대 한 참조를 가져올는 **빌드** 창을 통해 자동으로 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> 인터페이스 메서드 및 Visual Studio에 대 한 직접 액세스를 제공 합니다 **일반** 통해 창을 <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> 서비스입니다. 기본 제공 창 외에도 있습니다 만들고 관리할 수 있습니다 사용자 고유의 사용자 지정 창입니다.  
  
 제어할 수 있습니다.는 **출력** 창을 통해 직접 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> 인터페이스입니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> 에서 제공 하는 인터페이스를 <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> 서비스를 만들기, 검색 및 제거에 대 한 메서드를 정의 **출력** 창입니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> 인터페이스 창이 표시, 숨기기 창 및 해당 텍스트를 조작 하기 위한 메서드를 정의 합니다. 제어 하는 또 다른 방법은 합니다 **출력** 창을 사용 하는 것을 <xref:EnvDTE.OutputWindow> 및 <xref:EnvDTE.OutputWindowPane> Visual Studio 자동화 개체 모델에서 개체입니다. 거의 모든 기능을 캡슐화 하는 이러한 개체는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> 고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> 인터페이스입니다. 또한 합니다 <xref:EnvDTE.OutputWindow> 및 <xref:EnvDTE.OutputWindowPane> 열거를 쉽게 수행할 수 있도록 일부 높은 수준의 기능을 추가 하는 개체를 **출력** 창 창에서 텍스트를 검색 하 합니다.  
  
## <a name="creating-an-extension-that-uses-the-output-pane"></a>출력 창을 사용 하는 확장을 만들기  
 출력 창의 다양 한 측면을 실행 하는 확장을 만들 수 있습니다.  
  
1. 라는 VSIX 프로젝트를 만듭니다 `TestOutput` 메뉴 명령을 사용 하 여 이름이 **TestOutput**합니다. 자세한 내용은 [메뉴 명령을 사용 하 여 확장을 만드는](../extensibility/creating-an-extension-with-a-menu-command.md)합니다.  
  
2. 다음 참조를 추가 합니다.  
  
    1. EnvDTE  
  
    2. EnvDTE80  
  
3. TestOutput.cs, 추가 다음 문을 사용 하 여:  
  
    ```f#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4. TestOutput.cs, ShowMessageBox 메서드를 삭제 합니다. 다음 메서드 스텁을 추가 합니다.  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
    }  
    ```  
  
5. TestOutput 생성자에서 OutputCommandHandler에 명령 처리기를 변경 합니다. 명령을 추가 하는 파트는 다음과 같습니다.  
  
    ```csharp  
    OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
    if (commandService != null)  
    {  
        CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
        EventHandler eventHandler = OutputCommandHandler;  
        MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);  
        commandService.AddCommand(menuItem);  
    }  
    ```  
  
6. 아래 섹션에서는 출력 창 처리 하는 다른 방법을 보여 주는 다른 방법이 있습니다. OutputCommandHandler() 메서드의 본문에 이러한 메서드를 호출할 수 있습니다. 예를 들어, 다음 코드는 다음 섹션에 지정 된 CreatePane() 메서드를 추가 합니다.  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
        CreatePane(new Guid(), "Created Pane", true, false);  
    }  
    ```  
  
## <a name="creating-an-output-window-with-ivsoutputwindow"></a>IVsOutputWindow를 사용 하 여 출력 창 만들기  
 이 예제에서는 새로 만드는 방법을 보여 줍니다 **출력** 창을 사용 하 여는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> 인터페이스입니다.  
  
```csharp  
void CreatePane(Guid paneGuid, string title,   
    bool visible, bool clearWithSolution)  
{  
    IVsOutputWindow output =   
        (IVsOutputWindow)GetService(typeof(SVsOutputWindow));  
    IVsOutputWindowPane pane;  
  
    // Create a new pane.  
    output.CreatePane(  
        ref paneGuid,   
        title,   
        Convert.ToInt32(visible),   
        Convert.ToInt32(clearWithSolution));  
  
    // Retrieve the new pane.  
    output.GetPane(ref paneGuid, out pane);  
  
     pane.OutputString("This is the Created Pane \n");  
}  
```  
  
 클릭 하면 이전 섹션에 지정 된 확장 프로그램에이 메서드를 추가 하는 경우는 **TestOutput 호출** 명령을 표시 합니다 **출력** 라는 헤더로 창 **출력 표시 보낸 사람: CreatedPane** 와 단어 **생성 창 이것이** 자체 창에서.  
  
## <a name="creating-an-output-window-with-outputwindow"></a>OutputWindow를 사용 하 여 출력 창 만들기  
 만드는 방법을 보여 주는이 예제는 **출력** 창을 사용 하 여는 <xref:EnvDTE.OutputWindow> 개체입니다.  
  
```csharp  
void CreatePane(string title)  
{  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    OutputWindowPanes panes =  
        dte.ToolWindows.OutputWindow.OutputWindowPanes;  
  
    try  
    {  
        // If the pane exists already, write to it.  
        panes.Item(title);  
    }  
    catch (ArgumentException)  
    {  
        // Create a new pane and write to it.  
        return panes.Add(title);  
    }  
}  
```  
  
 하지만 합니다 <xref:EnvDTE.OutputWindowPanes> 검색할 컬렉션 수는 **출력** 가 제목으로 창, 창 제목은 고유 하 게 보장 되지 않습니다. 제목의 고유성을 의구심 있습니다 사용 하 여는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> 해당 GUID가 올바른 창을 검색 하는 방법입니다.  
  
 클릭 하면 이전 섹션에 지정 된 확장 프로그램에이 메서드를 추가 하는 경우는 **호출할 TestOutput** 라는 헤더로 출력 창 표시 되어야 하는 명령 **에서 출력 보기: DTEPane** 와 단어 **DTE 창 추가** 자체 창에서.  
  
## <a name="deleting-an-output-window"></a>삭제 출력 창  
 삭제 하는 방법을 보여 주는이 예제는 **출력** 창 선택 합니다.  
  
```csharp  
void DeletePane(Guid paneGuid)  
{  
    IVsOutputWindow output =  
    (IVsOutputWindow)ServiceProvider.GetService(typeof(SVsOutputWindow));  
  
    IVsOutputWindowPane pane;  
    output.GetPane(ref paneGuid, out pane);  
  
    if (pane == null)  
    {  
        CreatePane(paneGuid, "New Pane\n", true, true);  
    }  
     else  
    {  
        output.DeletePane(ref paneGuid);  
    }  
}  
```  
  
 클릭 하면 이전 섹션에 지정 된 확장 프로그램에이 메서드를 추가 하는 경우는 **호출할 TestOutput** 라는 헤더로 출력 창 표시 되어야 하는 명령 **에서 출력 보기: 새 창을** 와 단어 **생성 창 추가** 자체 창에서. 클릭할 경우 합니다 **TestOutput 호출** 명령을 다시, 창에 삭제 됩니다.  
  
## <a name="getting-the-general-pane-of-the-output-window"></a>출력 창의 일반 창 시작  
 이 예제에는 기본 제공을 가져오는 방법을 보여 줍니다 **일반** 창에는 **출력** 창입니다.  
  
```csharp  
void GetGeneralPane()  
{  
    return (IVsOutputWindowPane)GetService(  
        typeof(SVsGeneralOutputWindowPane));  
}  
```  
  
 클릭 하면 이전 섹션에 지정 된 확장 프로그램에이 메서드를 추가 하는 경우는 **호출 TestOutput** 명령 임을 확인할 수는 **출력** 창에 표시 된 단어 **일반 찾을 수 창** 창에서.  
  
## <a name="getting-the-build-pane-of-the-output-window"></a>출력 창의 빌드 창 시작  
 이 예제에서는 검색 빌드 창에 작성 하는 방법을 보여 줍니다. 빌드 창 기본적으로 활성화 되지 않아도 되므로 활성화 것도 됩니다.  
  
```csharp  
void OutputTaskItemStringExExample(string buildMessage)  
{  
    EnvDTE80.DTE2 dte = (EnvDTE80.DTE2)ServiceProvider.GetService(typeof(EnvDTE.DTE));  
  
    EnvDTE.OutputWindowPanes panes =  
        dte.ToolWindows.OutputWindow.OutputWindowPanes;  
    foreach (EnvDTE.OutputWindowPane pane in panes)  
        {  
            if (pane.Name.Contains("Build"))  
            {  
                pane.OutputString(buildMessage + "\n");  
                pane.Activate();  
                return;  
             }  
        }  
}  
```
