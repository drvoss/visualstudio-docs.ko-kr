---
title: 메뉴 명령을 사용 하 여 확장을 만드는 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
caps.latest.revision: 57
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e3bbf6b3b1ed2565d5e58806bd0935f713ba5bfd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62572889"
---
# <a name="creating-an-extension-with-a-menu-command"></a>메뉴 명령을 사용하여 확장 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에는 메모장을 실행 하는 메뉴 명령을 사용 하 여 확장을 만드는 방법을 보여 줍니다.  
  
## <a name="prerequisites"></a>전제 조건  
 Visual Studio 2015부터 수행 설치 하면 Visual Studio SDK 다운로드 센터에서. Visual Studio 설치에서 선택적 기능으로 포함 됩니다. 또한 VS SDK를 나중에 설치할 수 있습니다. 자세한 내용은 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)합니다.  
  
## <a name="creating-a-menu-command"></a>메뉴 명령 만들기  
  
1. 라는 VSIX 프로젝트를 만듭니다 **FirstMenuCommand**합니다. VSIX 프로젝트 템플릿을 찾을 수 있습니다 합니다 **새 프로젝트** 대화 상자의 **Visual C# / 확장성**합니다.  
  
2. 프로젝트를 열면 라는 사용자 지정 명령 항목 템플릿을 추가 **FirstCommand**합니다. 에 **솔루션 탐색기**, 프로젝트 노드를 마우스 오른쪽 단추로 **추가 / 새 항목**합니다. 에 **새 항목 추가** 대화 상자에서로 이동 **Visual C# / 확장성** 선택한 **사용자 지정 명령**입니다. 에 **이름을** 창의 맨 아래에 있는 필드에 명령 파일 이름을 **FirstCommand.cs**합니다.  
  
3. 프로젝트를 빌드하고 디버깅을 시작합니다.  
  
     Visual Studio의 실험적 인스턴스가 표시 됩니다. 실험적 인스턴스에 대 한 자세한 내용은 참조 하세요. [의 실험적 인스턴스에서](../extensibility/the-experimental-instance.md)합니다.  
  
4. 실험적 인스턴스를 엽니다는 **도구 / 확장 및 업데이트** 창입니다. 표시 되어야 합니다 **FirstMenuCommand** 에서 확장 합니다. (열면 **확장 및 업데이트** Visual Studio 인스턴스에서 작업을 표시 되지 않습니다 **FirstMenuCommand**).  
  
     이제는 **도구** 실험적 인스턴스에서 메뉴. 나타납니다 **FirstCommand 호출** 명령입니다. 이 시점에서 바로 표시 "FirstCommandPackage 내 FirstMenuCommand.FirstCommand.MenuItemCallback()" 라는 메시지 상자가 있습니다. 실제로 다음 섹션에서이 명령에서 메모장을 시작 하는 방법을 살펴보겠습니다.  
  
## <a name="changing-the-menu-command-handler"></a>메뉴 명령 처리기를 변경합니다.  
 이제 메모장을 시작 하려면 명령 처리기를 업데이트 해 보겠습니다.  
  
1. 디버깅을 중지 하 고 작업 인스턴스의 Visual Studio로 다시 이동 합니다. FirstCommand.cs 파일을 열고 다음을 추가 문을 사용 하 여:  
  
    ```csharp  
    using System.Diagnostics;  
    ```  
  
2. 개인 FirstCommand 생성자를 찾습니다. 명령에 명령 후크 되어와 명령 처리기는 지정 된 위치입니다. 명령 처리기의 이름을 StartNotepad에 다음과 같이 변경 합니다.  
  
    ```csharp  
    private FirstCommand(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
         OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(CommandSet, CommandId);  
            // Change to StartNotepad handler.  
            MenuCommand menuItem = new MenuCommand(this.StartNotepad, menuCommandID);  
            commandService.AddCommand(menuItem);  
        }  
    }  
    ```  
  
3. MenuItemCallback 메서드를 제거 하 고 메모장을 바로 시작 하는 StartNotepad 메서드를 추가 합니다.  
  
    ```csharp  
    private void StartNotepad(object sender, EventArgs e)  
    {  
        Process proc = new Process();  
        proc.StartInfo.FileName = "notepad.exe";  
        proc.Start();  
    }  
    ```  
  
4. 이제 사용해 보세요. 프로젝트 디버깅을 시작 하 고 클릭 **도구 / 호출할 FirstCommand**을 합하여 메모장의 인스턴스를 표시 합니다.  
  
     인스턴스를 사용할 수는 <xref:System.Diagnostics.Process> 메모장 뿐 아니라 모든 실행 파일을 실행 하는 클래스입니다. 예를 들어 calc.exe를 사용 하 여 시도 합니다.  
  
## <a name="cleaning-up-the-experimental-environment"></a>실험적 환경 정리  
 여러 확장을 개발 하는 경우에 확장 프로그램 코드의 서로 다른 버전을 사용 하 여 결과 탐색, 실험적 환경의 예상 대로 작동 하지 않을 수 있습니다. 이 경우 재설정 스크립트를 실행 해야 합니다. 라고 **Visual Studio 2015의 실험적 인스턴스 재설정**, 및 Visual Studio SDK의 일부분으로 제공 합니다. 이 스크립트는 처음부터 시작할 수 있도록 실험 환경에서 확장에 대 한 모든 참조를 제거 합니다.  
  
 두 가지 방법 중 하나에서이 스크립트를 가져올 수 있습니다.  
  
1. 데스크톱에서 찾기 **Visual Studio 2015의 실험적 인스턴스 재설정**합니다.  
  
2. 명령줄에서 다음을 실행하세요.  
  
    ```  
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp && PAUSE  
  
    ```  
  
## <a name="deploying-your-extension"></a>확장 프로그램 배포  
 이제 도구 확장을 실행 하는 원하는 방식으로 사용자가 친구 및 동료와 공유 하는 방법에 대 한 생각 하는 시간입니다. 설치 하는 Visual Studio 2015를 갖고 있다면 간단 합니다. 만든.vsix 파일을 보낼 수행 해야 됩니다. 일 릴리스 모드에서 작성 해야 합니다.  
  
 FirstMenuCommand bin 디렉터리에이 확장에 대 한.vsix 파일을 찾을 수 있습니다. 특히를 가정 하 고 릴리스 구성을 빌드하면 됩니다.  
  
 **\<코드 디렉터리 > \FirstMenuCommand\FirstMenuCommand\bin\Release\ FirstMenuCommand.vsix**  
  
 확장을 설치 하려면 친구의 Visual Studio에서 열려 있는 모든 인스턴스를 닫은 다음을 표시 하는.vsix 파일을 두 번 클릭 해야 합니다 **VSIX 설치 관리자**합니다. 파일에 복사 되는 **%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions** 디렉터리입니다.  
  
 친구 Visual Studio를 다시 제공 하는 경우에 FirstMenuCommand 확장을 찾을 수 그 **도구 / 확장 및 업데이트**합니다. 그가 이동할 수 있습니다 **확장 및 업데이트** 를 제거 하거나 너무 확장을 사용 하지 않도록 설정 합니다.  
  
## <a name="next-steps"></a>다음 단계  
 이 연습에서는 Visual Studio 확장을 사용 하 여 수행할 수 있는 작업의 일부만을 살펴보았습니다. Visual Studio 확장을 사용 하 여 수행할 수 있는 다른 (손쉽게) 작업의 짧은 목록을 다음과 같습니다.  
  
1. 간단한 메뉴 명령 사용 하 여 더 많은 작업을 수행할 수 있습니다.  
  
   1. 사용자 고유의 아이콘을 추가 합니다. [메뉴 명령에 아이콘 추가](../extensibility/adding-icons-to-menu-commands.md)  
  
   2. 메뉴 명령의 텍스트를 변경 합니다. [메뉴 명령 텍스트 변경](../extensibility/changing-the-text-of-a-menu-command.md)  
  
   3. 메뉴 바로 가기 명령에 추가 합니다. [메뉴 항목에 바로 가기 키 바인딩](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
  
2. 다른 종류의 명령, 메뉴 및 도구 모음을 추가 합니다. [메뉴 및 명령 확장](../extensibility/extending-menus-and-commands.md)  
  
3. 도구 창을 추가 하 고 기본 제공 Visual Studio 도구 창 확장: [도구 창 확장 및 사용자 지정](../extensibility/extending-and-customizing-tool-windows.md)  
  
4. 기존 코드 편집기에 IntelliSense, 코드 제안 및 기타 기능을 추가 합니다. [편집기 및 언어 서비스 확장](../extensibility/extending-the-editor-and-language-services.md)  
  
5. 옵션 및 속성 페이지 및 사용자 설정 확장 프로그램을 추가 합니다. [확장 속성 및 속성 창](../extensibility/extending-properties-and-the-property-window.md) 고 [사용자 설정 및 옵션 확장](../extensibility/extending-user-settings-and-options.md)  
  
   다른 종류의 확장 프로젝트의 새 형식 만들기와 같은 좀 더 많은 작업이 필요 ([확장 프로젝트](../extensibility/extending-projects.md)), 편집기의 새 형식 만들기 ([만들기 사용자 지정 편집기 및 디자이너](../extensibility/creating-custom-editors-and-designers.md)), 또는 격리 된 셸에서 확장 프로그램 구현: [Visual Studio Shell(격리)](../extensibility/visual-studio-isolated-shell.md)
