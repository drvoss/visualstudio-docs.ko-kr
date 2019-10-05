---
title: 사용자 설정 저장소에 쓰기 | Microsoft Docs
ms.date: 05/23/2019
ms.topic: conceptual
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44380a03b87318be0fdf746c75eff8988ac68267
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318476"
---
# <a name="writing-to-the-user-settings-store"></a>사용자 설정 저장소에 쓰기
사용자 설정은의 것과 같은 쓰기 설정 된 **도구 / 옵션** 대화 상자, 속성 창 및 기타 특정 대화 상자. Visual Studio 확장 적은 양의 데이터를 저장 하려면이 사용할 수 있습니다. 이 연습에서 읽고 써서 사용자 설정 저장소를 Visual studio 외부 도구로 메모장을 추가 하는 방법을 보여 줍니다.

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