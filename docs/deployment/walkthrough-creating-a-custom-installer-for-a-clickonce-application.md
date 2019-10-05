---
title: ClickOnce 응용 프로그램에 대 한 사용자 지정 설치 관리자 만들기
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, custom installer
- installer [ClickOnce], custom
- deploying applications [ClickOnce], custom installer
- InPlaceHostingManager [ClickOnce], custom installer
- custom installer [ClickOnce]
ms.assetid: fb222cc5-8aeb-4b94-8c49-b93e342f5f69
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e6969490789b4f5747c28f33e91c7d61e97de52e
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263466"
---
# <a name="walkthrough-create-a-custom-installer-for-a-clickonce-application"></a>연습: ClickOnce 응용 프로그램에 대 한 사용자 지정 설치 관리자 만들기
ClickOnce 응용 프로그램에 따라 프로그램 *.exe* 파일을 자동으로 설치 하 고 사용자 지정 설치 관리자에서 업데이트할 수 있습니다. 사용자 지정 설치 관리자는 보안 및 유지 관리 작업에 대 한 사용자 지정 대화 상자를 포함 하 여 설치 하는 동안 사용자 지정 사용자 경험을 구현할 수 있습니다. 설치 작업을 수행 하려면 사용자 지정 설치 관리자를 사용 하 여 <xref:System.Deployment.Application.InPlaceHostingManager> 클래스입니다. 이 연습에는 자동으로 ClickOnce 응용 프로그램을 설치 하는 사용자 지정 설치 관리자를 만드는 방법을 보여 줍니다.

## <a name="prerequisites"></a>전제 조건

### <a name="to-create-a-custom-clickonce-application-installer"></a>사용자 지정 ClickOnce 응용 프로그램 설치 관리자를 만들려면

1. ClickOnce 응용 프로그램에서 System.Deployment 및 System.Windows.Forms에 대 한 참조를 추가 합니다.

2. 응용 프로그램에 새 클래스를 추가 하 고 모든 이름을 지정 합니다. 이 연습에서는 `MyInstaller`라는 이름을 사용합니다.

3. 다음을 추가 합니다 `Imports` 또는 `using` 문을 새 클래스의 맨 위로 이동 합니다.

    ```vb
    Imports System.Deployment.Application
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Deployment.Application;
    using System.Windows.Forms;
    ```

4. 클래스에 다음 메서드를 추가 합니다.

     이러한 메서드는 호출 <xref:System.Deployment.Application.InPlaceHostingManager> 배포 매니페스트를 다운로드 하는 메서드를 설치 하 고 다운로드 하 고 ClickOnce 캐시에 응용 프로그램을 설치 하 고 사용자에 게 적절 한 권한을 어설션 합니다. ClickOnce 응용 프로그램을 신뢰할 수 있는 미리 인지, 아니면 신뢰 결정을 내리도록을 연기할 수는 사용자 지정 설치 관리자를 지정할 수는 <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A> 메서드를 호출 합니다. 이 코드는 미리 응용 프로그램을 신뢰합니다.

    > [!NOTE]
    > 미리 신뢰 하 여 할당 된 사용 권한 사용자 지정 설치 관리자 코드의 사용 권한을 초과할 수 없습니다.

     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.vb)]
     [!code-csharp[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.cs)]

5. 코드에서 설치를 위해 호출 된 `InstallApplication` 메서드. 예를 들어, 클래스 이름을 `MyInstaller`를 호출할 수 있습니다 `InstallApplication` 다음과 같은 방식입니다.

    ```vb
    Dim installer As New MyInstaller()
    installer.InstallApplication("\\myServer\myShare\myApp.application")
    MessageBox.Show("Installer object created.")
    ```

    ```csharp
    MyInstaller installer = new MyInstaller();
    installer.InstallApplication(@"\\myServer\myShare\myApp.application");
    MessageBox.Show("Installer object created.");
    ```

## <a name="next-steps"></a>다음 단계
 ClickOnce 응용 프로그램에는 업데이트 과정에서 표시 하기 위한 사용자 지정 사용자 인터페이스를 포함 하 여 사용자 지정 업데이트 논리를 추가할 수도 있습니다. 자세한 내용은 <xref:System.Deployment.Application.UpdateCheckInfo>을 참조하세요. ClickOnce 응용 프로그램을 숨길 수도 있습니다 시작 메뉴 항목, 바로 가기를 마우스 항목이 프로그램 추가 / 제거를 사용 하 여를 `<customUX>` 요소입니다. 자세한 내용은 [ \<entryPoint > 요소](../deployment/entrypoint-element-clickonce-application.md) 고 <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A>입니다.

## <a name="see-also"></a>참고자료
- [ClickOnce 애플리케이션 매니페스트](../deployment/clickonce-application-manifest.md)
- [\<entryPoint > 요소](../deployment/entrypoint-element-clickonce-application.md)