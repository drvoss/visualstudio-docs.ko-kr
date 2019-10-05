---
title: 설정 저장소에서 서비스 정보 가져오기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cfe754203ae9b4e951de5beef8cd829f9d7716bb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204304"
---
# <a name="getting-service-information-from-the-settings-store"></a>설정 저장소에서 서비스 정보 가져오기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

사용 가능한 모든 서비스 또는 특정 서비스가 설치 되어 있는지 확인 하려면 설정 저장소를 사용할 수 있습니다. 서비스 클래스의 형식을 알고 있어야 합니다.  
  
### <a name="to-list-the-available-services"></a>사용 가능한 서비스를 나열 하려면  
  
1. FindServicesExtension 라는 VSIX 프로젝트를 만들고 FindServicesCommand 라는 사용자 지정 명령을 추가 합니다. 사용자 지정 명령을 만드는 방법에 대 한 자세한 내용은 참조 하세요. [메뉴 명령을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2. FindServicesCommand.cs, 추가 다음 문을 사용 하 여:  
  
    ```vb  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    using System.Windows.Forms;  
    ```  
  
3. 구성 설정 저장소를 가져올 명명 된 서비스 하위를 찾은 다음입니다. 이 컬렉션에는 사용 가능한 모든 서비스가 포함 됩니다. MenuItemCommand 메서드에서 기존 코드를 제거 하 고를 다음으로 바꿉니다.  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
        string message = "Available services:\n";  
        IEnumerable<string> collection = configurationSettingsStore.GetSubCollectionNames("Services");  
        int n = 0;  
        foreach (string service in collection)  
        {  
            message += configurationSettingsStore.GetString("Services\\" + service, "Name", "Unknown") + "\n";  
        }  
  
        MessageBox.Show(message);  
    }  
    ```  
  
4. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스가 표시 됩니다.  
  
5. 실험적 인스턴스에서는 **도구** 메뉴에서 클릭 **FindServicesCommand 호출**합니다.  
  
     서비스를 모두 나열 하는 메시지 상자가 표시 됩니다.  
  
     이러한 설정은 확인 하려면 레지스트리 편집기를 사용할 수 있습니다.  
  
## <a name="finding-a-specific-service"></a>특정 서비스 찾기  
 사용할 수도 있습니다는 <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> 특정 서비스가 설치 되어 있는지 확인 하는 방법입니다. 서비스 클래스의 형식을 알고 있어야 합니다.  
  
1. 이전 절차에서 만든 프로젝트의 MenuItemCallback, 검색에 대 한 구성 설정 저장소를 `Services` 서비스의 GUID로 명명 된 하위 컬렉션 포함 된 컬렉션입니다. 이 예에서 도움말 서비스에 대해 살펴보겠습니다.  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
        string helpServiceGUID = typeof(SVsHelpService).GUID.ToString("B").ToUpper();  
        bool hasHelpService = configurationSettingsStore.CollectionExists("Services\\" + helpServiceGUID);  
        string message = "Help Service Available: " + hasHelpService;  
  
        MessageBox.Show(message);  
    }  
    ```  
  
2. 프로젝트를 빌드하고 디버깅을 시작합니다.  
  
3. 실험적 인스턴스에서는 **도구** 메뉴에서 클릭 **FindServicesCommand 호출**합니다.  
  
     텍스트를 사용 하 여 메시지가 표시 됩니다 **서비스를 사용할 수 하는 데 도움이 되:** 뒤 **True** 하거나 **False**합니다. 이 설정을 확인 하려면 이전 단계에서와 같이 레지스트리 편집기를 사용할 수 있습니다.
