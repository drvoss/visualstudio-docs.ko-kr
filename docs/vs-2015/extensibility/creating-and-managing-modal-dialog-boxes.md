---
title: 만들기 및 관리 모달 대화 상자 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 29b0066f201fbb791d471d5cfb433d9a335aa775
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62431578"
---
# <a name="creating-and-managing-modal-dialog-boxes"></a>모달 대화 상자 만들기 및 관리
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 내에서 모달 대화 상자를 만들 때 대화 상자의 부모 창 대화 상자 표시 되는 동안 않도록은 다음 대화 상자를 닫은 후 다시 부모 창을 사용 하도록 설정 해야 합니다. 이렇게 하지 않는 경우 오류가 나타날 수 있습니다. "Microsoft Visual Studio 모달 대화 상자가 활성화 되어 있으므로를 종료할 수 없는 합니다. 활성 대화 상자를 닫고 다시 시도 하십시오. "  
  
 이 작업을 수행 하는 방법은 두 가지가 있습니다. 파생 하는 WPF 대화 상자를 사용 하는 경우 권장 되는 방법은 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>를 호출한 다음 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> 대화 상자를 표시 합니다. 이 작업을 수행 하는 경우 부모 창의 모달 상태를 관리할 필요가 없습니다.  
  
 이유 대화 상자를 파생 시킬 수 클래스에서 대화 상자의 WPF, 없는 경우 또는 일부 다른 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>를 호출 하 여 대화 상자의 부모를 가져와야 합니다. 그런 다음 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> 호출 하 여 사용자가 직접 모달 상태를 관리 하 고는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> 메서드를 매개 변수 대화 상자를 표시 하 고 대화 상자를 닫은 후 1 (true)의 매개 변수를 사용 하 여 다시 메서드를 호출 하기 전에 0(false)입니다.  
  
## <a name="creating-a-dialog-box-derived-from-dialogwindow"></a>DialogWindow에서 파생 된 대화 상자 만들기  
  
1. 라는 VSIX 프로젝트를 만듭니다 **OpenDialogTest** 라는 메뉴 명령을 추가 하 고 **OpenDialog**합니다. 이 작업을 수행 하는 방법에 대 한 자세한 내용은 참조 하세요. [메뉴 명령을 사용 하 여 확장을 만드는](../extensibility/creating-an-extension-with-a-menu-command.md)합니다.  
  
2. 사용 하는 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> 클래스에 다음 어셈블리에 대 한 참조를 추가 해야 합니다 (프레임 워크 탭에서를 **참조 추가** 대화 상자):  
  
    - PresentationCore  
  
    - PresentationFramework  
  
    - WindowsBase  
  
    - System.Xaml  
  
3. OpenDialog.cs에서 다음을 추가 `using` 문:  
  
    ```csharp  
    using Microsoft.VisualStudio.PlatformUI;  
    ```  
  
4. 이라는 클래스를 선언 **TestDialogWindow** 에서 파생 되는 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>:  
  
    ```csharp  
    class TestDialogWindow : DialogWindow  
    {. . .}  
    ```  
  
5. 최소화 하 고 대화 상자를 최대화 하는 일을 할 수를 설정 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A> 고 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> 로:  
  
    ```csharp  
    internal TestDialogWindow()  
    {  
        this.HasMaximizeButton = true;  
        this.HasMinimizeButton = true;  
    }  
    ```  
  
6. 에 **OpenDialog.ShowMessageBox** 메서드를 기존 코드를 다음으로 바꿉니다.  
  
    ```csharp  
    TestDialogWindow testDialog = new TestDialogWindow();  
    testDialog.ShowModal();  
    ```  
  
7. 애플리케이션을 빌드 및 실행합니다. Visual Studio의 실험적 인스턴스가 표시 됩니다. 에 **도구** 실험적 인스턴스의 메뉴 라는 명령이 표시 됩니다 **OpenDialog 호출**합니다. 이 명령은 클릭 하면 대화 상자 창이 표시 됩니다. 최소화 하 고 창을 최대화 수 있어야 합니다.  
  
## <a name="creating-and-managing-a-dialog-box-not-derived-from-dialogwindow"></a>만들기 및 관리 DialogWindow에서 파생 되지 않은 대화 상자  
  
1. 이 절차를 따르면 합니다 **OpenDialogTest** 동일한 어셈블리 참조를 사용 하 여 이전 절차에서 만든 솔루션입니다.  
  
2. 다음 추가 `using` 선언 합니다.  
  
    ```csharp  
    using System.Windows;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    ```  
  
3. 라는 클래스를 만듭니다 **TestDialogWindow2** 에서 파생 되는 <xref:System.Windows.Window>:  
  
    ```csharp  
    class TestDialogWindow2 : Window  
    {. . .}  
    ```  
  
4. 개인에 대 한 참조를 추가 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:  
  
    ```  
    private IVsUIShell shell;  
    ```  
  
5. 에 대 한 참조를 설정 하는 생성자를 추가 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:  
  
    ```csharp  
    public TestDialogWindow2(IVsUIShell uiShell)  
    {  
        shell = uiShell;  
    }  
    ```  
  
6. 에 **OpenDialog.ShowMessageBox** 메서드를 기존 코드를 다음으로 바꿉니다.  
  
    ```csharp  
    IVsUIShell uiShell = (IVsUIShell)ServiceProvider.GetService(typeof(SVsUIShell));  
  
    TestDialogWindow2 testDialog2 = new TestDialogWindow2(uiShell);  
    //get the owner of this dialog  
    IntPtr hwnd;  
    uiShell.GetDialogOwnerHwnd(out hwnd);  
    testDialog2.WindowStartupLocation = System.Windows.WindowStartupLocation.CenterOwner;  
    uiShell.EnableModeless(0);  
    try  
    {  
        WindowHelper.ShowModal(testDialog2, hwnd);  
    }  
    finally  
    {  
        // This will take place after the window is closed.  
        uiShell.EnableModeless(1);  
    }  
    ```  
  
7. 애플리케이션을 빌드 및 실행합니다. 에 **도구가** 메뉴 라는 명령이 표시 됩니다 **OpenDialog 호출**합니다. 이 명령은 클릭 하면 대화 상자 창이 표시 됩니다.
