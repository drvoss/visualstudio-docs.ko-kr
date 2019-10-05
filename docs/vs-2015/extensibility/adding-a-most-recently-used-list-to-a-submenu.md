---
title: 가장 최근에 사용한 되는 하위 메뉴에 목록 추가 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- MRU lists
- menus, creating MRU list
- most recently used
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
caps.latest.revision: 47
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: caccf8923a8614ceedb7198e218ca2bb14bb7ec0
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444871"
---
# <a name="adding-a-most-recently-used-list-to-a-submenu"></a>하위 메뉴에 가장 최근에 사용한 메뉴 목록 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에서 데모 기반 [하위 메뉴에 추가](../extensibility/adding-a-submenu-to-a-menu.md), 동적 목록을 하위 메뉴에 추가 하는 방법을 보여줍니다. 동적 목록 mru (가장 최근에 사용 됨) 목록을 만들기 위한 기본을 형성 합니다.  
  
 동적 메뉴 목록을 메뉴에 자리 표시자를 사용 하 여 시작합니다. 메뉴 표시 되며, 때마다 Visual Studio 통합된 개발 환경 (IDE) 자리 표시자에 표시 되는 모든 명령에 대 한 VSPackage를 요청 합니다. 메뉴의 동적 목록이 어디서 나 발생할 수 있습니다. 그러나 동적 목록은 일반적으로 저장 되 고 하위 메뉴 또는 메뉴 하단에 단독으로 표시 합니다. 이러한 디자인 패턴을 사용 하 여 동적 목록을 확장 하 고 메뉴에서 다른 명령의 위치를 영향을 주지 않고 계약 명령 사용할 수 있습니다. 이 연습에서는 동적 MRU 목록의 하위 메뉴의 나머지 부분에서 줄으로 구분 된 기존 하위 메뉴의 맨 아래에 표시 됩니다.  
  
 기술적으로 동적 목록 도구 모음에도 적용할 수 있습니다. 그러나 것이 좋습니다는 사용을 하므로 사용자가 변경 하는 특정 단계를 수행 하지 않으면 도구 모음 변경 되지 않은 상태로 두어야 합니다.  
  
 이 연습에서는 그 중 하나 선택 될 때마다 순서를 변경 하는 네 개의 항목을 MRU 목록 (선택한 항목 목록의 맨 위로 이동).  
  
 메뉴 및.vsct 파일에 대 한 자세한 내용은 참조 하세요. [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)합니다.  
  
## <a name="prerequisites"></a>전제 조건  
 이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)합니다.  
  
## <a name="creating-an-extension"></a>확장 만들기  
  
- 절차를 따릅니다 [하위 메뉴에 추가](../extensibility/adding-a-submenu-to-a-menu.md) 다음 절차의 수정 된 하위 메뉴를 만들려면.  
  
  이 연습의 절차에서는 VSPackage 이름이 가정 `TopLevelMenu`에 사용 되는 이름입니다 [Visual Studio 메뉴 모음에 메뉴 추가](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)합니다.  
  
## <a name="creating-a-dynamic-item-list-command"></a>동적 항목 목록 명령 만들기  
  
1. TestCommandPackage.vsct를 엽니다.  
  
2. `Symbols` 섹션을 `GuidSymbol` guidTestCommandPackageCmdSet, 노드 추가 대 한 기호를 `MRUListGroup` 그룹 및 `cmdidMRUList` 명령을 다음과 같이 합니다.  
  
    ```csharp  
    <IDSymbol name="MRUListGroup" value="0x1200"/>  
    <IDSymbol name="cmdidMRUList" value="0x0200"/>  
    ```  
  
3. 에 `Groups` 섹션에서 선언 된 그룹의 기존 그룹 항목 뒤에 추가 합니다.  
  
    ```cpp  
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"   
           priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
  
    ```  
  
4. 에 `Buttons` 섹션, 기존 단추 항목 후 새로 선언 된 명령을 나타내는 노드를 추가 합니다.  
  
    ```csharp  
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidMRUList"  
        type="Button" priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MRUListGroup" />  
        <CommandFlag>DynamicItemStart</CommandFlag>  
        <Strings>  
            <CommandName>cmdidMRUList</CommandName>  
            <ButtonText>MRU Placeholder</ButtonText>  
                </Strings>  
    </Button>  
    ```  
  
     `DynamicItemStart` 플래그를 동적으로 생성 하는 명령을 사용 합니다.  
  
5. 프로젝트를 빌드하고 새 명령의 표시를 테스트 하려면 디버깅을 시작 합니다.  
  
     에 **TestMenu** 메뉴에서 새 하위 메뉴를 클릭 **하위 메뉴**, 새 명령에 표시할 **MRU 자리 표시자**합니다. 동적 MRU 명령 목록을 다음 절차에서 구현한 후이 명령을 레이블을 바뀝니다 목록을 하위 메뉴를 열 때마다.  
  
## <a name="filling-the-mru-list"></a>MRU 목록 채우기  
  
1. 기존 명령 Id를 후 TestCommandPackageGuids.cs에서 다음 줄을 추가 합니다 `TestCommandPackageGuids` 클래스 정의 합니다.  
  
    ```csharp  
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file  
    public const uint cmdidMRUList = 0x200;  
    ```  
  
2. TestCommand.cs 추가 다음 문을 사용 하 여 합니다.  
  
    ```csharp  
    using System.Collections;  
    ```  
  
3. AddCommand 한 마지막 호출 후 TestCommand 생성자에서 다음 코드를 추가 합니다. `InitMRUMenu` 나중에 정의 될  
  
    ```csharp  
    this.InitMRUMenu(commandService);  
    ```  
  
4. TestCommand 클래스에 다음 코드를 추가 합니다. 이 코드의 MRU 목록에 표시할 항목을 나타내는 문자열 목록을 초기화 합니다.  
  
    ```csharp  
    private int numMRUItems = 4;  
    private int baseMRUID = (int)TestCommandPackageGuids.cmdidMRUList;  
    private ArrayList mruList;  
  
    private void InitializeMRUList()  
    {  
        if (null == this.mruList)  
        {  
            this.mruList = new ArrayList();  
            if (null != this.mruList)  
            {  
                for (int i = 0; i < this.numMRUItems; i++)  
                {  
                    this.mruList.Add(string.Format(CultureInfo.CurrentCulture,  
                        "Item {0}", i + 1));  
                }  
            }  
        }  
    }  
    ```  
  
5. 후 합니다 `InitializeMRUList` 메서드를 추가 합니다 `InitMRUMenu` 메서드. 이 명령 MRU 목록 메뉴를 초기화합니다.  
  
    ```csharp  
    private void InitMRUMenu(OleMenuCommandService mcs)  
    {  
        InitializeMRUList();  
        for (int i = 0; i < this.numMRUItems; i++)  
        {  
            var cmdID = new CommandID(  
                new Guid(TestCommandPackageGuids.guidTestCommandPackageCmdSet), this.baseMRUID + i);  
            var mc = new OleMenuCommand(  
                new EventHandler(OnMRUExec), cmdID);  
            mc.BeforeQueryStatus += new EventHandler(OnMRUQueryStatus);  
            mcs.AddCommand(mc);  
        }  
    }  
    ```  
  
     MRU 목록에 가능한 모든 항목에 대 한 메뉴 명령 개체를 만들어야 합니다. 호출 하 여 IDE `OnMRUQueryStatus` 항목이 더 이상 없을 때까지 MRU 목록의 각 항목에 대 한 메서드. 관리 코드에서 더 이상 항목이 있는지 알아야 IDE에 대 한 유일한 방법은 가능한 모든 항목을 먼저 만드는 것입니다. 표시할 수 있습니다 추가 항목에 표시 되지 않는 상태로 처음 사용 하 여 `mc.Visible = false;` 메뉴 명령을 만든 후 합니다. 이러한 항목 다음 표시할 수 있습니다 나중에 사용 하 여 `mc.Visible = true;` 에 `OnMRUQueryStatus` 메서드.  
  
6. 후 합니다 `InitMRUMenu` 메서드를 다음 추가 `OnMRUQueryStatus` 메서드. 이 각 MRU 항목의 텍스트를 설정 하는 처리기.  
  
    ```csharp  
    private void OnMRUQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                menuCommand.Text = this.mruList[MRUItemIndex] as string;  
            }  
        }  
    }  
    ```  
  
7. 후 합니다 `OnMRUQueryStatus` 메서드를 다음 추가 `OnMRUExec` 메서드. MRU 항목을 선택 하는 것에 대 한 처리기입니다. 이 메서드는 선택한 항목 목록의 맨 위로 이동 하 고 메시지 상자에 선택한 항목을 표시 합니다.  
  
    ```csharp  
    private void OnMRUExec(object sender, EventArgs e)  
    {  
        var menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                string selection = this.mruList[MRUItemIndex] as string;  
                for (int i = MRUItemIndex; i > 0; i--)  
                {  
                    this.mruList[i] = this.mruList[i - 1];  
                }  
                this.mruList[0] = selection;  
                System.Windows.Forms.MessageBox.Show(  
                    string.Format(CultureInfo.CurrentCulture,  
                                  "Selected {0}", selection));  
            }  
        }  
    }  
  
    ```  
  
## <a name="testing-the-mru-list"></a>MRU 목록 테스트  
  
#### <a name="to-test-the-mru-menu-list"></a>최근에 사용한 메뉴 목록 테스트 하려면  
  
1. 프로젝트를 빌드하고 디버깅을 시작합니다  
  
2. 에 **TestMenu** 메뉴에서 클릭 **TestCommand 호출**합니다. 이렇게 명령을 선택 되어 있는지 여부를 나타내는 메시지 상자가 표시 됩니다.  
  
    > [!NOTE]
    > 이 단계는 VSPackage 로드 하 고 올바르게 MRU 목록 표시에 적용 해야 합니다. 이 단계를 건너뛰면 MRU 목록 표시 되지 않습니다.  
  
3. 에 **테스트 메뉴** 메뉴에서 클릭 **하위 메뉴**합니다. 4 개 항목 목록은 구분 기호를 아래 하위 메뉴의 끝에 표시 됩니다. 클릭 하면 **항목 3**, 메시지 상자가 나타나고 "선택한 항목 3" 텍스트를 표시 합니다. (4 개 항목 목록을 표시 되지 않으면 확인 이전 단계의 지침에에서 따르고 있다고 합니다.)  
  
4. 하위 메뉴를 다시 엽니다. 있음을 **항목 3** 목록의 맨 위에 있는 이제는 다른 항목을 한 위치 아래로 푸시한 및 합니다. 클릭 **항목 3** 다시 텍스트 명령 레이블 함께 새 위치로 올바르게 이동 했음을 나타냅니다는 메시지 상자 여전히 "선택한 항목 3"이 표시 되는지 확인 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [메뉴 항목 동적 추가](../extensibility/dynamically-adding-menu-items.md)
