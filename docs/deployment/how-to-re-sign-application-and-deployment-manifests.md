---
title: '방법: 응용 프로그램 및 배포 매니페스트에 다시 서명 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Office applications, signing manifests
- deploying applications [ClickOnce], signing manifests
- deploying applications, signing manifests
- ClickOnce deployment, signing manifests
- Office development in Visual Studio, signing manifests
ms.assetid: d53bceb9-4d3b-4c22-b909-8f370e7231fb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e934832f20ea7ab11484cdeb345f989aa842e06d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62928348"
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>방법: 애플리케이션 및 배포 매니페스트 다시 서명
Windows Forms 응용 프로그램, Windows Presentation Foundation 응용 프로그램 (xbap) 또는 Office 솔루션에 대 한 응용 프로그램 매니페스트에 대 한 배포 속성을 변경한 후 두 응용 프로그램에 다시 서명 해야 하 고 사용 하 여 배포 매니페스트는 인증서입니다. 이 프로세스를 수행하면 최종 사용자 컴퓨터에 훼손된 파일이 설치되지 않습니다.

 매니페스트를 다시 서명할 수 있습니다 다른 시나리오 고객에 게는 응용 프로그램에 서명 하 고 자체 인증서를 사용 하 여 배포 매니페스트 하는 경우입니다.

## <a name="re-sign-the-application-and-deployment-manifests"></a>애플리케이션 및 배포 매니페스트 다시 서명
 응용 프로그램 매니페스트 파일에 이미 변경 했다고 가정 합니다 (*.manifest*). 자세한 내용은 [방법: 배포 속성을 변경할](https://msdn.microsoft.com/library/66052a3a-8127-4964-8147-2477ef5d1472)합니다.

#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Mage.exe를 사용 하 여 매니페스트에 다시 응용 프로그램 및 배포를 서명 하려면

1. 엽니다는 **Visual Studio 명령 프롬프트** 창입니다.

2. 로그인 하려면 매니페스트 파일이 있는 폴더로 디렉터리를 변경 합니다.

3. 응용 프로그램 매니페스트 파일에 서명 하려면 다음 명령을 입력 합니다. 바꿉니다 *ManifestFileName* 매니페스트 파일 이름 확장명을 사용 하 여 합니다. 바꿉니다 *인증서* 바꾸고 인증서 파일의 상대 또는 정규화 된 경로로 *암호* 인증서의 암호로 바꿉니다.

    ```cmd
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     예를 들어, 추가 기능는 Windows Form 응용 프로그램 또는 Windows Presentation Foundation 브라우저 응용 프로그램에 대 한 응용 프로그램 매니페스트를 서명 하려면 다음 명령을 실행할 수 있습니다. Visual Studio에서 만든 임시 인증서를 프로덕션 환경으로 배포에 대 한 권장 되지 않습니다.

    ```cmd
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

4. 업데이트 하 고 이전 단계 에서처럼 자리 표시자 이름을 대체 배포 매니페스트 파일을 서명 하려면 다음 명령을 입력 합니다.

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     예를 들어, 업데이트 및에 Excel 추가 기능에서 Windows Forms 응용 프로그램을 Windows Presentation Foundation 브라우저 응용 프로그램 배포 매니페스트에 서명 하려면 다음 명령을 실행할 수 있습니다.

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5. 필요에 따라 마스터 배포 매니페스트를 복사 (*게시할\\\<appname >.application*) 버전 배포 디렉터리로 (*publish\Application 파일\\ \<응용 프로그램 이름 > _\<버전 >*).

## <a name="update-and-re-sign-the-application-and-deployment-manifests"></a>업데이트 및 응용 프로그램 및 배포 매니페스트에 다시 서명
 응용 프로그램 매니페스트 파일에 이미 변경 했다고 가정 합니다 (*.manifest*) 하지만 업데이트 된 다른 파일이 있습니다. 파일이 업데이트 될 때 파일을 나타내는 해시도 업데이트 되어야 합니다.

#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Mage.exe를 사용 하 여 매니페스트를 업데이트 하 고 응용 프로그램 및 배포에 다시 서명

1. 엽니다는 **Visual Studio 명령 프롬프트** 창입니다.

2. 로그인 하려면 매니페스트 파일이 있는 폴더로 디렉터리를 변경 합니다.

3. 제거 된 *.deploy* 게시에 있는 파일에서 파일 확장명 출력 폴더입니다.

4. 업데이트 된 파일에 대 한 새 해시를 사용 하 여 응용 프로그램 매니페스트를 업데이트 하 고 응용 프로그램 매니페스트 파일을 서명 하려면 다음 명령을 입력 합니다. 바꿉니다 *ManifestFileName* 매니페스트 파일 이름 확장명을 사용 하 여 합니다. 바꿉니다 *인증서* 바꾸고 인증서 파일의 상대 또는 정규화 된 경로로 *암호* 인증서의 암호로 바꿉니다.

    ```cmd
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     예를 들어, 추가 기능는 Windows Form 응용 프로그램 또는 Windows Presentation Foundation 브라우저 응용 프로그램에 대 한 응용 프로그램 매니페스트를 서명 하려면 다음 명령을 실행할 수 있습니다. Visual Studio에서 만든 임시 인증서를 프로덕션 환경으로 배포에 대 한 권장 되지 않습니다.

    ```cmd
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5. 업데이트 하 고 이전 단계 에서처럼 자리 표시자 이름을 대체 배포 매니페스트 파일을 서명 하려면 다음 명령을 입력 합니다.

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     예를 들어, 업데이트 및에 Excel 추가 기능에서 Windows Forms 응용 프로그램을 Windows Presentation Foundation 브라우저 응용 프로그램 배포 매니페스트에 서명 하려면 다음 명령을 실행할 수 있습니다.

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

6. 추가 된 *.deploy* 응용 프로그램 및 배포 매니페스트 파일 제외 하 고 파일에 다시 파일 확장명입니다.

7. 필요에 따라 마스터 배포 매니페스트를 복사 (*게시할\\\<appname >.application*) 버전 배포 디렉터리로 (*publish\Application 파일\\ \<응용 프로그램 이름 > _\<버전 >*).

## <a name="see-also"></a>참고자료
- [ClickOnce 애플리케이션 보안](../deployment/securing-clickonce-applications.md)
- [ClickOnce 애플리케이션의 코드 액세스 보안](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce 및 Authenticode](../deployment/clickonce-and-authenticode.md)
- [신뢰할 수 있는 애플리케이션 배포 개요](../deployment/trusted-application-deployment-overview.md)
- [방법: ClickOnce 보안 설정 사용](../deployment/how-to-enable-clickonce-security-settings.md)
- [방법: ClickOnce 응용 프로그램에 대 한 보안 영역 설정](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [방법: ClickOnce 응용 프로그램에 대 한 사용자 지정 권한 설정](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [방법: 제한 된 권한으로 ClickOnce 응용 프로그램 디버그](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)
- [방법: ClickOnce 응용 프로그램에 대 한 클라이언트 컴퓨터에 신뢰할 수 있는 게시자 추가](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [방법: ClickOnce 신뢰 프롬프트 동작 구성](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)