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
ms.openlocfilehash: b648134b7ad27a8f622ce270dc0f05e0a7e6516c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72637417"
---
# <a name="walkthrough-create-a-custom-installer-for-a-clickonce-application"></a>연습: ClickOnce 응용 프로그램에 대 한 사용자 지정 설치 관리자 만들기
*.Exe* 파일을 기반으로 하는 모든 ClickOnce 응용 프로그램은 사용자 지정 설치 관리자에서 자동으로 설치 및 업데이트할 수 있습니다. 사용자 지정 설치 관리자는 보안 및 유지 관리 작업을 위한 사용자 지정 대화 상자를 포함 하 여 설치 중에 사용자 지정 사용자 환경을 구현할 수 있습니다. 설치 작업을 수행 하기 위해 사용자 지정 설치 관리자는 <xref:System.Deployment.Application.InPlaceHostingManager> 클래스를 사용 합니다. 이 연습에서는 ClickOnce 응용 프로그램을 자동으로 설치 하는 사용자 지정 설치 관리자를 만드는 방법을 보여 줍니다.

## <a name="prerequisites"></a>Prerequisites

### <a name="to-create-a-custom-clickonce-application-installer"></a>사용자 지정 ClickOnce 응용 프로그램 설치 관리자를 만들려면

1. ClickOnce 응용 프로그램에서 System.object에 대 한 참조를 추가 합니다.

2. 응용 프로그램에 새 클래스를 추가 하 고 이름을 지정 합니다. 이 연습에서는 `MyInstaller`라는 이름을 사용합니다.

3. 새 클래스의 맨 위에 다음 `Imports` 또는 `using` 지시문을 추가 합니다.

    ```vb
    Imports System.Deployment.Application
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Deployment.Application;
    using System.Windows.Forms;
    ```

4. 클래스에 다음 메서드를 추가 합니다.

     이러한 메서드는 <xref:System.Deployment.Application.InPlaceHostingManager> 메서드를 호출 하 여 배포 매니페스트를 다운로드 하 고, 적절 한 권한을 어설션하 며, 사용자에 게 설치 권한을 요청 하 고, ClickOnce 캐시에 응용 프로그램을 다운로드 하 여 설치 합니다. 사용자 지정 설치 관리자는 ClickOnce 응용 프로그램이 미리 신뢰 되도록 지정 하거나 <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A> 메서드 호출에 대 한 트러스트 결정을 연기할 수 있습니다. 이 코드는 응용 프로그램을 미리 신뢰 합니다.

    > [!NOTE]
    > 미리 트러스팅에서 할당 한 사용 권한은 사용자 지정 설치 관리자 코드의 사용 권한을 초과할 수 없습니다.

     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.vb)]
     [!code-csharp[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.cs)]

5. 코드에서 설치를 시도 하려면 `InstallApplication` 메서드를 호출 합니다. 예를 들어 `MyInstaller` 클래스의 이름을 지정 하는 경우 다음과 같은 방법으로 `InstallApplication`를 호출할 수 있습니다.

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
 ClickOnce 응용 프로그램은 업데이트 프로세스 중에 표시할 사용자 지정 사용자 인터페이스를 비롯 한 사용자 지정 업데이트 논리를 추가할 수도 있습니다. 자세한 내용은 <xref:System.Deployment.Application.UpdateCheckInfo>을 참조하십시오. ClickOnce 응용 프로그램은 `<customUX>` 요소를 사용 하 여 표준 시작 메뉴 항목, 바로 가기 및 프로그램 추가/제거 항목을 표시 하지 않을 수도 있습니다. 자세한 내용은 [\<entryPoint > 요소](../deployment/entrypoint-element-clickonce-application.md) 및 <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A>를 참조 하세요.

## <a name="see-also"></a>참조
- [ClickOnce 애플리케이션 매니페스트](../deployment/clickonce-application-manifest.md)
- [\<entryPoint > 요소](../deployment/entrypoint-element-clickonce-application.md)
