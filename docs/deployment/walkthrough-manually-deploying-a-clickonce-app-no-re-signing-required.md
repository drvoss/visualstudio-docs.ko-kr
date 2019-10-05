---
title: 수동으로 ClickOnce 배포 브랜딩 유지 하는 앱
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- branding
- preserved branding information
- ClickOnce deployment, manually
- multiple ClickOnce deployment and branding
- ClickOnce deployment, SDK tools
- customer deployments
- manual ClickOnce deployments
- manifests [ClickOnce]
- ClickOnce applications, deployed by others
ms.assetid: c21822fb-d4ee-42e4-b72d-41ee9786efe5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 47db202d07fd88bfb5e922964caf2cdd5008c6fd
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263421"
---
# <a name="walkthrough-manually-deploy-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information"></a>연습: 수동으로 다시 서명할 필요가 없습니다 없고 브랜드 정보가 유지 되는 ClickOnce 응용 프로그램 배포
만들 때는 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램 및 고객 게시할 수 있도록 제공 및 배포, 고객에 일반적으로 배포 매니페스트를 업데이트 하 고 다시 서명 해야 했습니다. 여전히 대부분의 경우에는 이러한 방식이 사용 되 고 있지만,.NET Framework 3.5를 사용 하면 만들려는 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 새 배포 매니페스트를 다시 생성할 필요 없이 고객에 게 배포할 수 있는 배포 합니다. 자세한 내용은 [다시 서명 하지 않고 테스트 및 프로덕션 서버용 ClickOnce 배포 응용 프로그램](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md)합니다.

 만들 때는 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램 및 고객 게시할 수 있도록 제공 및 배포, 응용 프로그램 고객의 브랜드를 사용 하거나 브랜딩이 유지할 수 있습니다. 예를 들어, 응용 프로그램을 단일 소유 응용 프로그램인 경우 브랜딩이 유지 하는 것이 좋습니다. 응용 프로그램은 항상 각 고객에 대 한 사용자 지정, 경우에 고객의 브랜드를 사용 하는 것이 좋습니다. .NET Framework 3.5 응용 프로그램 배포를 조직에 부여 하는 경우 사용자의 브랜드를 유지할 수 있습니다, 게시자 정보 및 보안 서명 수 있습니다. 자세한 내용은 [만들 ClickOnce 응용 프로그램 배포를 다른](../deployment/creating-clickonce-applications-for-others-to-deploy.md)합니다.

> [!NOTE]
> 이 연습에서 만든 배포 수동으로 사용 하 여 명령줄 도구 *Mage.exe* 또는 그래픽 도구인 *MageUI.exe*합니다. 수동 배포에 대 한 자세한 내용은 참조 하세요. [연습: 수동으로 ClickOnce 응용 프로그램을 배포](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)합니다.

## <a name="prerequisites"></a>전제 조건
 이 연습의 단계를 수행 하려면 다음이 필요 합니다.

- Windows Forms는 응용 프로그램을 배포할 준비가 되어 있습니다. 이 응용 프로그램으로 간주 됩니다 *WindowsFormsApp1*합니다.

- Visual Studio 또는 Windows SDK입니다.

### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageexe"></a>여러 배포와 브랜딩 지원 Mage.exe를 사용 하 여 ClickOnce 응용 프로그램을 배포 하려면

1. Visual Studio 명령 프롬프트를 열고 또는 [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] 명령 프롬프트, 및를 저장 하는 디렉터리로 변경 하 여 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 파일.

2. 배포의 현재 버전의 이름을 딴 디렉터리를 만듭니다. 선택 가능성이 처음으로 응용 프로그램 배포 하는 경우 **1.0.0.0**합니다.

   > [!NOTE]
   > 배포의 버전 응용 프로그램 파일의 버전과 다를 수 있습니다.

3. 명명 된 하위 디렉터리를 만듭니다 **bin** 실행 파일, 어셈블리, 리소스 및 데이터 파일을 비롯 한 모든 응용 프로그램 파일을 복사 합니다.

4. Mage.exe에 대 한 호출을 사용 하 여 응용 프로그램 매니페스트를 생성 합니다.

   ```cmd
   mage -New Application -ToFile 1.0.0.0\WindowsFormsApp1.exe.manifest -Name "Windows Forms App 1" -Version 1.0.0.0 -FromDirectory 1.0.0.0\bin -UseManifestForTrust true -Publisher "A. Datum Corporation"
   ```

5. 디지털 인증서를 사용 하 여 응용 프로그램 매니페스트에 서명 합니다.

   ```cmd
   mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx
   ```

6. 호출 하 여 배포 매니페스트를 생성 *Mage.exe*합니다. 기본적으로 *Mage.exe* 표시에 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 한다는 온라인 모두 실행할 수 있도록 및 오프 라인 설치 된 응용 프로그램으로 배포 합니다. 응용 프로그램을 사용할 수 있도록의 사용자가 온라인 상태인 경우에 사용 합니다 `-i` 인수 값을 사용 하 여 `f`입니다. 이 응용 프로그램은 여러 배포 기능을 활용 하므로 제외 합니다 `-providerUrl` 인수를 *Mage.exe*합니다. (제외 하 고.NET Framework 버전 3.5 이전 버전에서 `-providerUrl` 에 대해 오프 라인 응용 프로그램 오류가 발생 합니다.)

   ```cmd
   mage -New Deployment -ToFile WindowsFormsApp1.application -Name "Windows Forms App 1" -Version 1.0.0.0 -AppManifest 1.0.0.0\WindowsFormsApp1.manifest
   ```

7. 배포 매니페스트를 서명 하지 않습니다.

8. 자신의 네트워크에서 응용 프로그램을 배포 하는 고객에 게 모든 파일을 제공 합니다.

9. 이 시점에서 고객 자신의 자체 생성 된 인증서를 사용 하 여 배포 매니페스트에 서명 해야 합니다. 예를 들어 Adventure Works 라는 회사에 대 한 고객 작동 하는 경우 그 생성할 수 있습니다 사용 하 여 자체 서명 된 인증서를 *MakeCert.exe* 도구입니다. 다음을 사용 하 여는 *Pvk2pfx.exe* 에서 만든 파일을 결합 하는 도구 *MakeCert.exe* 전달할 수 있는 PFX 파일로 *Mage.exe*합니다.

    ```cmd
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx
    ```

10. 다음은 고객 배포 매니페스트에 서명 하려면이 인증서를 사용 합니다.

    ```cmd
    mage -Sign WindowsFormsApp1.application -CertFile MyCert.pfx
    ```

11. 고객은 사용자에 게 응용 프로그램을 배포합니다.

### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageuiexe"></a>여러 배포 및 MageUI.exe를 사용 하 여 브랜딩 지원을 사용 하 여 ClickOnce 응용 프로그램을 배포 하려면

1. Visual Studio 명령 프롬프트를 열고 또는 [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] 저장할가 있는 디렉터리로 이동한 명령 프롬프트에 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 파일입니다.

2. 명명 된 하위 디렉터리를 만듭니다 **bin** 실행 파일, 어셈블리, 리소스 및 데이터 파일을 비롯 한 모든 응용 프로그램 파일을 복사 합니다.

3. 배포의 현재 버전 하위 디렉터리를 만듭니다. 선택 가능성이 처음으로 응용 프로그램 배포 하는 경우 **1.0.0.0**합니다.

   > [!NOTE]
   > 배포의 버전 응용 프로그램 파일의 버전과 다를 수 있습니다.

4. 이동 합니다 \\ **bin** 2 단계에서 만든 디렉터리에 디렉터리입니다.

5. 그래픽 도구를 시작 *MageUI.exe*합니다.

   ```cmd
   MageUI.exe
   ```

6. 선택 하 여 새 응용 프로그램 매니페스트를 만듭니다 **파일**, **새로 만들기**, **응용 프로그램 매니페스트** 합니다.

7. 기본 **이름을** 탭에서이 배포의 이름 및 버전 번호를 입력 합니다. 또한 값을 제공 **게시자**을 사용할 시작 메뉴에서 응용 프로그램의 바로 가기 링크에 대 한 폴더 이름으로 배포 될 때입니다.

8. 선택 된 **응용 프로그램 옵션** 탭을 클릭 **사용 하 여 응용 프로그램 매니페스트 신뢰 정보에 대 한**합니다. 이 대 한 타사 브랜딩 하는 것이 이렇게 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램입니다.

9. 선택 합니다 **파일** 탭을 클릭 합니다 **찾아보기** 단추 옆에 **응용 프로그램 디렉터리** 입력란.

10. 2 단계에서 만든 응용 프로그램 파일을 포함 하는 디렉터리를 선택 하 고 클릭 **확인** 폴더 선택 대화 상자에서.

11. 클릭 합니다 **채우기** 파일 목록에 모든 응용 프로그램 파일을 추가 하는 단추입니다. 응용 프로그램 실행 파일이 둘 이상 있으면 선택 하 여 시작 응용 프로그램으로이 배포에 대 한 주 실행 파일을 표시할 **진입점** 에서 합니다 **파일 형식** 드롭 다운 목록. (응용 프로그램 실행 파일이 포함 된 경우 *MageUI.exe* 를 표시 합니다.)

12. 선택 된 **필요한 사용 권한에** 탭을 선택한 응용 프로그램에 부여 해야 하는 신뢰 수준입니다. 기본값은 **완전 신뢰**, 대부분의 응용 프로그램에 대 한 적절 한 됩니다.

13. 선택 **파일**하십시오 **저장** 메뉴에서 응용 프로그램 매니페스트에 저장 합니다. 저장할 때 응용 프로그램 매니페스트에 서명 하 라는 메시지가 표시 됩니다.

14. 파일 시스템에 파일로 저장 된 인증서에 있는 경우 사용 합니다 **인증서 파일로 서명** 옵션을 줄임표를 사용 하 여 파일 시스템에서 인증서를 선택 ( **...** ) 단추입니다.

     또는

     인증서가 컴퓨터에서 액세스할 수 있는 인증서 저장소에 보관 되어, 선택는 **저장 된 인증서로 서명 옵션**, 제공 된 목록에서 인증서를 선택 합니다.

15. 선택 **파일**를 **새로 만들기**를 **배포 매니페스트** 배포 매니페스트를 만들려면 메뉴에서 그 다음에 **이름** 탭에서 제공을 이름 및 버전 번호 (**1.0.0.0** 이 예제의).

16. 으로 전환 합니다 **업데이트** 탭 하 고이 응용 프로그램을 업데이트할 빈도 지정 합니다. 응용 프로그램에서 사용 하는 경우는 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 자체 업데이트를 확인 하려면 배포 API 라는 레이블이 있는 확인란의 선택을 취소 **이 응용 프로그램의 업데이트 확인**합니다.

17. 으로 전환 합니다 **응용 프로그램 참조** 탭 합니다. 클릭 하 여이 탭에 있는 값의 모든 미리 채울 수 있습니다 합니다 **매니페스트 선택** 이전 단계에서 만든 단추 및 응용 프로그램 매니페스트를 선택 합니다.

18. 선택할 **저장** 디스크에 배포 매니페스트를 저장 합니다. 저장할 때 응용 프로그램 매니페스트에 서명 하 라는 메시지가 표시 됩니다. 클릭 **취소** 하며 서명 하지 않고 매니페스트를 저장 합니다.

19. 고객에 게 모두 응용 프로그램 파일을 제공 합니다.

20. 이 시점에서 고객 자신의 자체 생성 된 인증서를 사용 하 여 배포 매니페스트에 서명 해야 합니다. 예를 들어 Adventure Works 라는 회사에 대 한 고객 작동 하는 경우 그 생성할 수 있습니다 사용 하 여 자체 서명 된 인증서를 *MakeCert.exe* 도구입니다. 다음을 사용 하 여는 *Pvk2pfx.exe* 에서 만든 파일을 결합 하는 도구 *MakeCert.exe* 전달할 수 있는 PFX 파일로 *MageUI.exe*합니다.

    ```cmd
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx
    ```

21. 생성 된 인증서를 사용 하 여 고객이 이제 배포 매니페스트에 서명에서 배포 매니페스트를 열어 *MageUI.exe*, 한 다음이 저장 합니다. 고객의 선택 서명 대화 상자가 나타나면 **인증서 파일로 서명** 옵션을 선택한 디스크에 저장 한 PFX 파일을 선택 합니다.

22. 고객은 사용자에 게 응용 프로그램을 배포합니다.

## <a name="see-also"></a>참고자료
- [Mage.exe(매니페스트 생성 및 편집 도구)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [MageUI.exe(매니페스트 생성 및 편집 도구, 그래픽 클라이언트)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
- [MakeCert](/windows/desktop/SecCrypto/makecert)
