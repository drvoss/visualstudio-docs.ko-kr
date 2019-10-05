---
title: 사용자 설정 저장소에 쓰기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 764d9b81297c6bbefd1f5fdf7c77e4d514bb5045
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63408495"
---
# <a name="writing-to-the-user-settings-store"></a>사용자 설정 저장소에 쓰기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

사용자 설정은의 것과 같은 쓰기 설정 된 **도구 / 옵션** 대화 상자, 속성 창 및 기타 특정 대화 상자. Visual Studio 확장 적은 양의 데이터를 저장 하려면이 사용할 수 있습니다. 이 연습에서 읽고 써서 사용자 설정 저장소를 Visual studio 외부 도구로 메모장을 추가 하는 방법을 보여 줍니다.  
  
### <a name="backing-up-your-user-settings"></a>사용자 설정 백업  
  
1. 디버그 하는 절차를 반복 하는 외부 도구 설정을 다시 수 있어야 합니다. 이렇게 하려면 필요에 따라 복원할 수 있도록 원래 설정을 저장 해야 합니다.  
  
2. Regedit.exe를 엽니다.  
  
3. Navigate to HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External Tools\\.  
  
    > [!NOTE]
    > \14.0Exp\ 및 없습니다 \14.0 포함 하는 키에서 찾으려는 있는지\\합니다. Visual Studio의 실험적 인스턴스를 실행 하면 사용자 설정과 레지스트리 하이브에 "14.0Exp" 됩니다.  
  
4. \External Tools\ 하위 키를 마우스 오른쪽 단추로 누른 **내보내기**합니다. 했는지 **선택한 분기** 을 선택 합니다.  
  
5. 결과 외부 Tools.reg 파일을 저장 합니다.  
  
6. 외부 도구 설정을 다시 설정 하려는 경우 HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External Tools\ 레지스트리 키를 선택 하 고 클릭 나중 **삭제** 상황에 맞는 메뉴입니다.  
  
7. 경우는 **확인 키 삭제** 대화 상자가 나타나면 **예**합니다.  
  
8. 이전에 저장 된 외부 Tools.reg 파일을 마우스 오른쪽 단추로 클릭, 클릭 **로 열기**를 클릭 하 고 **레지스트리 편집기**합니다.  
  
## <a name="writing-to-the-user-settings-store"></a>사용자 설정 저장소에 쓰기  
  
1. UserSettingsStoreExtension 라는 VSIX 프로젝트를 만들고 UserSettingsStoreCommand 라는 사용자 지정 명령을 추가 합니다. 사용자 지정 명령을 만드는 방법에 대 한 자세한 내용은 참조 하세요. [메뉴 명령을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2. UserSettingsStoreCommand.cs, 추가 다음 문을 사용 하 여:  
  
    ```csharp  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    ```  
  
3. MenuItemCallback에서 메서드의 본문을 삭제 하 고 다음과 같이 설정을 저장 하는 사용자를 가져옵니다.  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
    }  
    ```  
  
4. 이제 메모장 외부 도구로 이미 설정 되어 있는지 여부 확인 합니다. 되는지 확인 하려면 ToolCmd 설정을 "Notepad" 다음과 같은 모든 외부 도구를 통해 반복 해야 합니다.  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
  
        // Find out whether Notepad is already an External Tool.  
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");  
        bool hasNotepad = false;  
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;  
        for (int i = 0; i < toolCount; i++)  
        {  
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)  
            {  
                hasNotepad = true;  
                break;  
            }  
        }  
    }  
  
    ```  
  
5. 메모장 외부 도구로 설정 되지 않은 경우이 같이 설정 합니다.  
  
    ```vb  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
  
        // Find out whether Notepad is already installed.  
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");  
        bool hasNotepad = false;  
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;  
        for (int i = 0; i < toolCount; i++)  
        {  
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)  
            {  
                hasNotepad = true;  
                break;  
            }  
        }  
  
        string message = (hasNotepad) ? "Notepad already installed" : "Installing Notepad";  
         if (!hasNotepad)  
        {  
            userSettingsStore.SetString("External Tools", "ToolTitle" + toolCount, "&Notepad");  
            userSettingsStore.SetString("External Tools", "ToolCmd" + toolCount, "C:\\Windows\\notepad.exe");  
            userSettingsStore.SetString("External Tools", "ToolArg" + toolCount, "");  
            userSettingsStore.SetString("External Tools", "ToolDir" + toolCount, "$(ProjectDir)");  
            userSettingsStore.SetString("External Tools", "ToolSourceKey" + toolCount, "");  
            userSettingsStore.SetUInt32("External Tools", "ToolOpt" + toolCount, 0x00000011);  
  
            userSettingsStore.SetInt32("External Tools", "ToolNumKeys", toolCount + 1);  
        }  
    }  
    ```  
  
6. 코드를 테스트 합니다. 추가 메모장 외부 도구를 롤백해야 레지스트리를 두 번째로 실행 하기 전에 있도록 해야 합니다.  
  
7. 코드를 빌드하고 디버깅을 시작 합니다.  
  
8. 에 **도구** 메뉴에서 클릭 **UserSettingsStoreCommand 호출**합니다. 메모장을 추가 합니다 **도구** 메뉴.  
  
9. 도구에서 메모장을 표시 해야 하는 이제 / 옵션 메뉴를 클릭 하 **메모장** 메모장의 인스턴스를 준비 해야 합니다.
