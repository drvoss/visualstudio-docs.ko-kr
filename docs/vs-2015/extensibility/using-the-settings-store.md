---
title: 설정 저장소를 사용 하 여 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4b6c2810a81ada06152faea06e86a27f7907a643
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430105"
---
# <a name="using-the-settings-store"></a>설정 저장소 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

두 가지 종류의 설정 저장 합니다.  
  
- 설정이 읽기 전용으로 Visual Studio 및 VSPackage는 구성 설정입니다. Visual Studio는 모든 알려진된.pkgdef 파일의 설정은이 저장소에 병합합니다.  
  
- 페이지에 표시 되는 것과 같은 쓰기 가능 설정이 사용자 설정 합니다 **옵션** 대화 상자, 속성 페이지 및 기타 특정 대화 상자. Visual Studio 확장에는 적은 양의 데이터의 로컬 저장소에 대 한 이러한 사용할 수 있습니다.  
  
  이 연습에는 구성 설정 저장소에서 데이터를 읽는 방법을 보여 줍니다. 참조 [사용자 설정 저장소에 쓸](../extensibility/writing-to-the-user-settings-store.md) 사용자 설정 저장소에 쓰는 방법에 대 한 설명은 합니다.  
  
## <a name="creating-the-example-project"></a>예제 프로젝트 만들기  
 이 섹션에는 데모에 대 한 메뉴 명령을 사용 하 여 간단한 확장 프로젝트를 만드는 방법을 보여 줍니다.  
  
1. 모든 Visual Studio 확장은 확장 자산을 포함 하는 VSIX 배포 프로젝트를 시작 합니다. 만들기는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 라는 VSIX 프로젝트 `SettingsStoreExtension`합니다. VSIX 프로젝트 템플릿을 찾을 수 있습니다 합니다 **새 프로젝트** 대화 상자의 **Visual C# / 확장성**합니다.  
  
2. 이제 라는 사용자 지정 명령 항목 서식 파일을 추가할 **SettingsStoreCommand**합니다. 에 **새 항목 추가** 대화 상자에서로 이동 **Visual C# / 확장성** 선택한 **사용자 지정 명령**입니다. 에 **이름을** 창의 맨 아래에 있는 필드에 명령 파일 이름을 **SettingsStoreCommand.cs**합니다. 사용자 지정 명령을 만드는 방법에 대 한 자세한 내용은 참조 하세요. [메뉴 명령을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
## <a name="using-the-configuration-settings-store"></a>구성 설정 저장소를 사용 하 여  
 이 섹션에서는 검색 구성 설정을 표시 하는 방법을 보여 줍니다.  
  
1. SettingsStorageCommand.cs 파일에 다음 추가 문을 사용 하 여:  
  
   ```  
   using System.Collections.Generic;  
   using Microsoft.VisualStudio.Settings;  
   using Microsoft.VisualStudio.Shell.Settings;  
   using System.Windows.Forms;  
   ```  
  
2. `MenuItemCallback`, 메서드의 본문을 제거 및 구성 설정 저장소를 가져올 다음이 줄을 추가 합니다.  
  
   ```  
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
   ```  
  
    합니다 <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> 를 통해 관리 되는 도우미 클래스인는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> 서비스입니다.  
  
3. 이제 Windows Phone 도구가 설치 되어 있는지 확인 합니다. 코드는 다음과 같습니다.  
  
   ```  
   private void MenuItemCallback(object sender, EventArgs e)  
   {  
       SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
       SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
       bool arePhoneToolsInstalled = configurationSettingsStore.CollectionExists(@"InstalledProducts\Microsoft Windows Phone Developer Tools");  
       string message = "Microsoft Windows Phone Developer Tools: " + arePhoneToolsInstalled;  
       MessageBox.Show(message);  
   }  
   ```  
  
4. 코드를 테스트 합니다. 프로젝트를 빌드하고 디버깅을 시작합니다.  
  
5. 실험적 인스턴스에서는 **도구** 메뉴에서 클릭 **SettingsStoreCommand 호출**합니다.  
  
    이라는 메시지 상자를 표시 **Microsoft Windows Phone 개발자 도구:** 뒤 **True** 하거나 **False**합니다.  
  
   Visual Studio 시스템 레지스트리에 설정 저장소를 유지합니다.  
  
#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>레지스트리 편집기를 사용 하 여 구성 설정을 확인 하려면  
  
1. Regedit.exe를 엽니다.  
  
2. Navigate to HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts\\.  
  
    > [!NOTE]
    > \14.0Exp_Config\ 및 없습니다 \14.0_Config 포함 하는 키에서 찾으려는 있는지\\합니다. Visual Studio의 실험적 인스턴스를 실행 하면 구성 설정은 레지스트리 하이브 "14.0Exp_Config"에 있습니다.  
  
3. \Installed Products\ 노드를 확장 합니다. 이전 단계에서 메시지 이면 **Microsoft Windows Phone 개발자 도구 설치: True**, \Installed Products\ Microsoft Windows Phone 개발자 도구 노드를 포함 해야 합니다. 메시지 이면 **Microsoft Windows Phone 개발자 도구 설치: False**, \Installed Products\ Microsoft Windows Phone 개발자 도구 노드를 포함 하지 않아야 합니다.
