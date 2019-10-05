---
title: 도구 모음에 메뉴 컨트롤러 추가 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding menu controllers
- menus, adding menu controllers to toolbars
- menu controllers, adding to toolbars
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
caps.latest.revision: 39
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3c63f6c98153c9f7a9fab171b3caddd57df717cc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184903"
---
# <a name="adding-a-menu-controller-to-a-toolbar"></a>도구 모음에 메뉴 컨트롤러 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습은 합니다 [도구 창에 도구 모음을 추가](../extensibility/adding-a-toolbar-to-a-tool-window.md) 연습 및 도구 창 도구 모음에 메뉴 컨트롤러를 추가 하는 방법을 보여 줍니다. 여기에 나와 있는 단계도 적용할 수 있습니다에서 만든 도구 모음에는 [도구 모음 추가](../extensibility/adding-a-toolbar.md) 연습 합니다.  
  
 메뉴 컨트롤러 분할 컨트롤입니다. 클릭 하 여 실행할 수 있습니다 및 메뉴 컨트롤러의 왼쪽에 마지막으로 사용한 명령을 보여 줍니다. 메뉴 컨트롤러의 오른쪽에 있는 화살표는,를 클릭 하면 추가 명령의 목록을 엽니다. 명령 실행 목록에서 명령을 클릭 하면 시간과 메뉴 컨트롤러의 왼쪽에 있는 명령을 대체 합니다. 이 이렇게 하면에 메뉴 컨트롤러는 항상 목록에서 마지막으로 사용한 명령을 보여 주는 명령 단추 처럼 작동 합니다.  
  
 메뉴에 메뉴 컨트롤러 나타날 수 있지만 도구 모음에서 가장 자주 사용 됩니다.  
  
## <a name="prerequisites"></a>필수 구성 요소  
 Visual Studio 2015부터 수행 설치 하면 Visual Studio SDK 다운로드 센터에서. Visual Studio 설치에서 선택적 기능으로 포함 됩니다. 또한 VS SDK를 나중에 설치할 수 있습니다. 자세한 내용은 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)합니다.  
  
## <a name="creating-a-menu-controller"></a>메뉴 컨트롤러 만들기  
  
#### <a name="to-create-a-menu-controller"></a>메뉴 컨트롤러를 만들려면  
  
1. 에 설명 된 절차를 따릅니다 [도구 창에 도구 모음 추가](../extensibility/adding-a-toolbar-to-a-tool-window.md) 도구 모음에 있는 도구 창을 만들 수 있습니다.  
  
2. TWTestCommandPackage.vsct에서 기호 섹션으로 이동 합니다. GuidSymbol 요소에서 **guidTWTestCommandPackageCmdSet**, 메뉴 컨트롤러, 메뉴 컨트롤러 그룹과 세 가지 메뉴 항목을 선언 합니다.  
  
   ```xml  
   <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />  
   ```  
  
3. 메뉴 섹션에서 메뉴 항목을 마지막 후 메뉴로 메뉴 컨트롤러를 정의 합니다.  
  
   ```xml  
   <Menu guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" priority="0x0100" type="MenuController">  
       <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />  
       <CommandFlag>IconAndText</CommandFlag>  
       <CommandFlag>TextChanges</CommandFlag>  
       <CommandFlag>TextIsAnchorCommand</CommandFlag>  
       <Strings>  
           <ButtonText>Test Menu Controller</ButtonText>  
           <CommandName>Test Menu Controller</CommandName>  
       </Strings>  
   </Menu>  
   ```  
  
    합니다 `TextChanges` 고 `TextIsAnchorCommand` 플래그 마지막 선택한 명령에 맞게 메뉴 컨트롤러를 사용 하도록 설정 하려면 포함 되어야 합니다.  
  
4. 그룹의 마지막 그룹 항목, 다음 섹션의 메뉴 컨트롤러 그룹을 추가 합니다.  
  
   ```xml  
   <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">  
       <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />  
   </Group>  
   ```  
  
    메뉴 컨트롤러 부모로 설정 하면이 그룹에 배치 하는 모든 명령 메뉴 컨트롤러에 표시 됩니다. `priority` 특성을 생략 하면 기본값인 0으로 설정 하는 하기 때문에 메뉴 컨트롤러의 유일한 그룹입니다.  
  
5. 단추 섹션에서 마지막 단추 항목 후 각 메뉴 항목에 대 한 단추 요소를 추가 합니다.  
  
   ```xml  
   <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem1" priority="0x0000" type="Button">  
       <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
       <Icon guid="guidImages" id="bmpPic1" />  
       <CommandFlag>IconAndText</CommandFlag>  
       <Strings>  
           <ButtonText>MC Item 1</ButtonText>  
           <CommandName>MC Item 1</CommandName>  
       </Strings>  
   </Button>  
   <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem2" priority="0x0100" type="Button">  
       <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
       <Icon guid="guidImages" id="bmpPic2" />  
       <CommandFlag>IconAndText</CommandFlag>  
       <Strings>  
           <ButtonText>MC Item 2</ButtonText>  
           <CommandName>MC Item 2</CommandName>  
       </Strings>  
   </Button>  
   <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem3" priority="0x0200" type="Button">  
       <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
       <Icon guid="guidImages" id="bmpPicSearch" />  
       <CommandFlag>IconAndText</CommandFlag>  
       <Strings>  
           <ButtonText>MC Item 3</ButtonText>  
           <CommandName>MC Item 3</CommandName>  
       </Strings>  
   </Button>  
   ```  
  
6. 이 시점에서 메뉴 컨트롤러를 살펴볼 수 있습니다. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스를 확인 해야 합니다.  
  
   1. 에 **보기 / 기타 Windows** 메뉴를 열고 **테스트 ToolWindow**합니다.  
  
   2. 도구 창의 도구 모음에 메뉴 컨트롤러 표시 됩니다.  
  
   3. 세 가지 가능한 명령을 보려면 메뉴 컨트롤러의 오른쪽에 있는 화살표를 클릭 합니다.  
  
      명령을 클릭 하면 메뉴 컨트롤러 제목의 명령을 표시할 변경 되는지 확인 합니다. 다음 섹션에서는 이러한 명령을 활성화 하는 코드를 추가 합니다.  
  
## <a name="implementing-the-menu-controller-commands"></a>메뉴 컨트롤러 명령 구현  
  
1. TWTestCommandPackageGuids.cs, 기존 명령 Id 뒤에 세 가지 메뉴 항목에 대 한 명령 Id를 추가 합니다.  
  
    ```csharp  
    public const int cmdidMCItem1 = 0x130;  
    public const int cmdidMCItem2 = 0x131;  
    public const int cmdidMCItem3 = 0x132;  
    ```  
  
2. TWTestCommand.cs, TWTestCommand 클래스의 맨 위에 있는 다음 코드를 추가 합니다.  
  
    ```csharp  
    private int currentMCCommand; // The currently selected menu controller command  
    ```  
  
3. TWTestCommand 생성자에 대 한 마지막 호출 후에 `AddCommand` 메서드를 동일한 처리기를 통해 각 명령에 대 한 이벤트를 라우팅하는 코드를 추가 합니다.  
  
    ```csharp  
    for (int i = TWTestCommandPackageGuids.cmdidMCItem1; i <=  
        TWTestCommandPackageGuids.cmdidMCItem3; i++)  
    {  
        CommandID cmdID = new  
        CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), i);  
        OleMenuCommand mc = new OleMenuCommand(new  
          EventHandler(OnMCItemClicked), cmdID);  
        mc.BeforeQueryStatus += new EventHandler(OnMCItemQueryStatus);  
        commandService.AddCommand(mc);  
        // The first item is, by default, checked.   
        if (TWTestCommandPackageGuids.cmdidMCItem1 == i)  
        {  
            mc.Checked = true;  
            this.currentMCCommand = i;  
        }  
    }  
    ```  
  
4. 선택으로 선택한 명령을 표시할 TWTestCommand 클래스에 이벤트 처리기를 추가 합니다.  
  
    ```csharp  
    private void OnMCItemQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);  
        }  
    }  
    ```  
  
5. 사용자가 메뉴 컨트롤러에서 명령을 선택할 때 MessageBox를 표시 하는 이벤트 처리기를 추가 합니다.  
  
    ```csharp  
    private void OnMCItemClicked(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            string selection;  
            switch (mc.CommandID.ID)  
            {  
                case c.cmdidMCItem1:  
                    selection = "Menu controller Item 1";  
                    break;  
  
                case TWTestCommandPackageGuids.cmdidMCItem2:  
                    selection = "Menu controller Item 2";  
                    break;  
  
                case TWTestCommandPackageGuids.cmdidMCItem3:  
                    selection = "Menu controller Item 3";  
                    break;  
  
                default:  
                    selection = "Unknown command";  
                    break;  
            }  
            this.currentMCCommand = mc.CommandID.ID;  
  
            IVsUIShell uiShell =  
              (IVsUIShell) ServiceProvider.GetService(typeof(SVsUIShell));  
            Guid clsid = Guid.Empty;  
            int result;  
            uiShell.ShowMessageBox(  
                       0,  
                       ref clsid,  
                       "Test Tool Window Toolbar Package",  
                       string.Format(CultureInfo.CurrentCulture,  
                                     "You selected {0}", selection),  
                       string.Empty,  
                       0,  
                       OLEMSGBUTTON.OLEMSGBUTTON_OK,  
                       OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
                       OLEMSGICON.OLEMSGICON_INFO,  
                       0,  
                       out result);  
        }  
    }  
    ```  
  
## <a name="testing-the-menu-controller"></a>메뉴 컨트롤러 테스트  
  
1. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스를 확인 해야 합니다.  
  
2. 엽니다는 **테스트 도구 창** 에 **보기 / 다른 Windows** 메뉴.  
  
     메뉴 컨트롤러 도구 창의 도구 모음에 나타나고 표시 **MC 항목 1**합니다.  
  
3. 메뉴 컨트롤러 단추 왼쪽의 화살표를 클릭 합니다.  
  
     세 항목의 첫 번째 선택한 아이콘 주위에 강조 표시 상자에 표시 됩니다. 클릭 **MC 항목 3**합니다.  
  
     메시지와 함께 대화 상자가 나타납니다 **선택한 메뉴 컨트롤러 항목 3**합니다. 메시지 메뉴 컨트롤러 단추의 텍스트에 해당 하는지 확인 합니다. 메뉴 컨트롤러 단추 표시 **MC 항목 3**합니다.  
  
## <a name="see-also"></a>관련 항목  
 [도구 창에 도구 모음 추가](../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [도구 모음 추가](../extensibility/adding-a-toolbar.md)
