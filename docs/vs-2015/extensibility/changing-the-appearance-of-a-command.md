---
title: 명령 모양 변경 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4741059410e052c571d77088b9cbe109fb651642
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184500"
---
# <a name="changing-the-appearance-of-a-command"></a>명령 모양 변경
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

명령의 모양을 변경 하 여 사용자에 게 피드백을 제공할 수 있습니다. 예를 들어 명령을 사용할 수 없을 때 다르게 좋습니다. 명령을 사용 가능 여부, 숨기기 또는 표시 하면 또는 확인 하거나 메뉴에서 선택 취소 합니다.  
  
 명령의 모양을 변경 하려면 다음이 작업 중 하나를 수행 합니다.  
  
- 명령 테이블 파일에서 명령 정의에서 적절 한 플래그를 지정 합니다.  
  
- 사용 된 <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> 서비스입니다.  
  
- 구현 된 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스 및 원시 명령 개체를 수정 합니다.  
  
  다음 단계를 찾아 관리 패키지 프레임 워크 (MPF)를 사용 하 여 명령의 모양을 업데이트 하는 방법을 보여 줍니다.  
  
### <a name="to-change-the-appearance-of-a-menu-command"></a>메뉴 명령의 모양을 변경 하려면  
  
1. 지침을 따릅니다 [메뉴 명령 텍스트를 변경](../extensibility/changing-the-text-of-a-menu-command.md) 라는 메뉴 항목을 만들려면 `New Text`합니다.  
  
2. ChangeMenuText.cs 파일에 다음 추가 문을 사용 하 여:  
  
    ```csharp  
    using System.Security.Permissions;  
    ```  
  
3. ChangeMenuTextPackageGuids.cs 파일에 다음 줄을 추가 합니다.  
  
    ```csharp  
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    ```  
  
4. ChangeMenuText.cs 파일에서 ShowMessageBox 메서드의 코드를 다음으로 바꿉니다.  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var command = sender as OleMenuCommand;  
        if (command.Text == "New Text")  
            ChangeMyCommand(command.CommandID.ID, false);}  
    }  
    ```  
  
5. 업데이트 하려는 명령을 가져올는 <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> 개체 및 명령 개체에 적절 한 속성을 설정 합니다. 예를 들어 다음 메서드를 사용 하면 VSPackage 명령에서 지정 된 명령 집합 사용 가능 여부. 다음 코드에서는 이름이 인 항목 메뉴 `New Text` 가 클릭 한 후 사용할 수 없습니다.  
  
    ```csharp  
    public bool ChangeMyCommand(int cmdID, bool enableCmd)  
    {  
        bool cmdUpdated = false;  
        var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService))  
            as OleMenuCommandService;  
        var newCmdID = new CommandID(new Guid(ChangeMenuTextPackageGuids.guidChangeMenuTextPackageCmdSet), cmdID);  
        MenuCommand mc = mcs.FindCommand(newCmdID);  
        if (mc != null)  
        {  
            mc.Enabled = enableCmd;  
            cmdUpdated = true;  
        }  
        return cmdUpdated;    }  
    }  
    ```  
  
6. 프로젝트를 빌드하고 디버깅을 시작합니다. Visual Studio의 실험적 인스턴스가 표시 됩니다.  
  
7. 에 **도구** 메뉴를 클릭 합니다 **ChangeMenuText 호출** 명령. 명령 이름은 시점 **ChangeMenuText 호출**이므로 명령 처리기 ChangeMyCommand()를 호출 하지 않습니다.  
  
8. 에 **도구** 돌아가면 메뉴 **새 텍스트**합니다. 클릭 **새 텍스트**합니다. 명령이 회색 이제 해야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Vspackage에서 사용자 인터페이스 요소를 추가 하는 방법](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [메뉴 및 명령 확장](../extensibility/extending-menus-and-commands.md)   
 [Visual Studio 명령 테이블(.Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
