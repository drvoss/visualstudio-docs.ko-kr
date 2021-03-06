---
title: 메뉴 명령의 텍스트를 변경 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: df943221fc2f154e8f18007bd5f7ff5454434d84
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39234860"
---
# <a name="change-the-text-of-a-menu-command"></a>메뉴 명령의 텍스트를 변경 합니다.
다음 단계를 사용 하 여 메뉴 명령의 텍스트 레이블을 변경 하는 방법을 보여는 <xref:System.ComponentModel.Design.IMenuCommandService> 서비스입니다.  
  
## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>IMenuCommandService 사용 하 여 메뉴 명령 레이블을 변경합니다.  
  
1.  라는 VSIX 프로젝트를 만듭니다 `MenuText` 메뉴 명령을 사용 하 여 이름이 **ChangeMenuText**합니다. 자세한 내용은 [메뉴 명령을 사용 하 여 확장 프로그램을 만들려면](../extensibility/creating-an-extension-with-a-menu-command.md)합니다.  
  
2.  에 *.vsct* 파일을 추가 `TextChanges` 다음 예와에서 같이를 메뉴 명령에 플래그를 지정 합니다.  
  
    ```xml  
    <Button guid="guidChangeMenuTextPackageCmdSet" id="ChangeMenuTextId" priority="0x0100" type="Button">  
        <Parent guid="guidChangeMenuTextPackageCmdSet" id="MyMenuGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <CommandFlag>TextChanges</CommandFlag>  
        <Strings>  
            <ButtonText>Invoke ChangeMenuText</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
3.  에 *ChangeMenuText.cs* 파일, 메뉴 명령이 표시 되기 전에 호출 되는 이벤트 처리기를 만듭니다.  
  
    ```csharp  
    private void OnBeforeQueryStatus(object sender, EventArgs e)  
    {  
        var myCommand = sender as OleMenuCommand;  
        if (null != myCommand)  
        {  
            myCommand.Text = "New Text";  
        }  
    }  
    ```  
  
     변경 하 여이 메서드는 메뉴 명령의 상태를 업데이트할 수도 있습니다는 <xref:System.ComponentModel.Design.MenuCommand.Visible%2A>, <xref:System.ComponentModel.Design.MenuCommand.Checked%2A>, 및 <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> 속성에는 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 개체입니다.  
  
4.  ChangeMenuText 생성자에서 만드는 코드를 사용 하 여 원래 명령 초기화 및 배치 코드를 바꿉니다를 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> (아닌 `MenuCommand`) 메뉴 명령을 나타냅니다는, 추가 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> 이벤트 처리기를 메뉴를 제공 합니다. 명령 메뉴 명령 서비스입니다.  
  
     처럼 보여야 합니다 다음과 같습니다.  
  
    ```csharp  
    private ChangeMenuText(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
            EventHandler eventHandler = this.ShowMessageBox;  
            OleMenuCommand menuItem = new OleMenuCommand(ShowMessageBox, menuCommandID);  
            menuItem.BeforeQueryStatus +=  
                new EventHandler(OnBeforeQueryStatus);  
            commandService.AddCommand(menuItem);  
        }  
    }  
    ```  
  
5.  프로젝트를 빌드하고 디버깅을 시작합니다. Visual Studio의 실험적 인스턴스가 표시 됩니다.  
  
6.  에 **도구가** 메뉴 라는 명령이 표시 됩니다 **ChangeMenuText 호출**합니다.  
  
7.  명령을 클릭 합니다. 발표 하는 메시지 상자가 표시 됩니다 **MenuItemCallback** 가 호출 되었습니다. 도구 메뉴에 있는 명령의 이름이 이제 참조 해야 메시지 상자를 닫으면 **새 텍스트**합니다.
