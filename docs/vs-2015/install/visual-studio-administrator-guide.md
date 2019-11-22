---
title: Visual Studio 관리자 가이드 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
caps.latest.revision: 76
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: a59f9f2cb2548d6d40670832e66d4df5c83680df
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295920"
---
# <a name="visual-studio-administrator-guide"></a>Visual Studio Administrator Guide
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

For the latest documentation on Visual Studio, see the [Visual Studio administrator guide](/visualstudio/install/visual-studio-administrator-guide).

You can deploy Visual Studio 2015 on a network as long as each target computer meets the [minimum installation requirements](https://visualstudio.microsoft.com/vs/older-downloads/). [Visual Studio의 오프라인 설치 만들기](../install/create-an-offline-installation-of-visual-studio.md) 페이지에 설명된 대로 /layout 스위치와 함께 설치 파일을 실행한 다음, 로컬 머신에서 네트워크 공유로 복사하면 네트워크 공유를 만들 수 있습니다. If you are using an ISO, you can mount the ISO and share it or copy the ISO to a network share.  
  
 네트워크 공유에서 설치하는 경우 소스 위치가 "기억"됩니다. 이는 클라이언트 컴퓨터 복구 시 클라이언트가 원래 설치된 네트워크 공유로 돌아가야 할 수도 있음을 의미합니다. 조직에서 Visual Studio 2015 클라이언트를 실행하는 예상 수명에 맞도록 네트워크 위치를 신중하게 선택합니다.  
  
## <a name="detection-and-servicing-keys"></a>검색 및 서비스 키  
 레지스트리에 포함된 검색 하위 키를 사용하여 Visual Studio 제품이 컴퓨터에 이미 설치되어 있는지 여부를 확인할 수 있습니다. 자동화된 배포에서 이러한 검색 키를 사용하여 설치를 진행할 필요가 있는지 여부를 확인합니다.  See [Detecting System Requirements](../extensibility/internals/detecting-system-requirements.md)[Detecting System Requirements].  
  
## <a name="avoiding-reboots"></a>재부팅 방지  
 Visual Studio를 배포하기 전에 적절한 Visual Studio 필수 조건을 충족하는지 확인하여 다시 부팅을 줄일 수 있습니다. For the .NET Framework, you might need to reboot computers that are running Windows 8 if you deploy Visual Studio 2015 on them without first installing the .NET Framework 4.6.  
  
 Windows 및 Android 디바이스 에뮬레이션의 경우 Windows 기능 Hyper-V가 아직 설정되어 있지 않으면 컴퓨터를 다시 부팅해야 할 수 있습니다. 웹 개발의 경우 Windows 기능 웹 서버가 아직 설정되어 있지 않으면 컴퓨터를 다시 부팅해야 할 수 있습니다. Office 개발의 경우 Windows 기능을 Windows Identify Foundation이 아직 설정되어 있지 않으면 컴퓨터를 다시 부팅해야 할 수 있습니다. Windows 기능 웹 서버가 아직 설정되어 있지 않으면 컴퓨터를 다시 부팅합니다. Office 개발의 경우 Windows 기능을 Windows Identify Foundation이 아직 설정되어 있지 않으면 컴퓨터를 다시 부팅해야 할 수 있습니다. Windows 기능 검색 및 설치를 자동화하는 방법에 대한 자세한 내용은 [Windows Server 2008 R2의 Server Core 설치를 실행하는 서버에 서버 역할 설치](https://technet.microsoft.com/library/ee441260(v=ws.10).aspx)(영문)를 참조하세요.  
  
## <a name="error-return-codes"></a>오류 반환 코드  
 다음 표에서는 중요한 오류 코드를 보여 줍니다. 자동화에서 이러한 오류 코드를 사용하여 다시 부팅이 필요한지 여부 및 설치 성공 여부를 확인할 수 있습니다. If you receive an error code, consider the troubleshooting steps on the [Install Visual Studio](../install/install-visual-studio-2015.md) page.  
  
|설치 상태|재시작 필요 없음|재시작 필요|설명|  
|------------------|--------------------------|----------------------|-----------------|  
|성공|0x00000000 [0]|0x00000bc2 [3010]|설치 성공|  
|블록|0x80044000 [-2147205120]|0x8004C000 [-2147172352]|보고할 유일한 블록이 “다시 부팅 보류 중”인 경우 완료되는 값은 완료 안 됨-다시 부팅해야 함 값(0x80048bc7)입니다.|  
|취소|0x00000642 [1602]|0x80048642 [-2147187134]|다시 부팅 값이 반환될 때 반환 코드는 1602입니다.|  
|완료 안 됨-다시 부팅해야 함|해당 사항 없음|0x80048bc7 [-2147185721]|설치를 계속하려면 다시 시작해야 합니다.|  
|실패|0x00000643 [1603]|0x80048643 [-2147187133]|다시 부팅 값이 반환될 때 반환 코드는 1603입니다.|  
  
## <a name="interactive-administrator-installer"></a>대화형 관리자 설치 관리자  
 Visual Studio 설치를 기반으로 하여 대화형 설치 관리자를 만드는 경우 Visual Studio 설치 관리자에서 진행률을 볼 수 있습니다. Visual Studio 2015 설치 관리자는 "burn"이라고도 하는 오픈 소스 WiX(Windows Installer XML) chainer 기술을 기반으로 합니다. burn 기술은 burn 및 netfx4라는 두 통신 프로토콜을 지원합니다. For a brief reference, please see the description of the Protocol attribute in the documentation for the ExePackage element at [wixtoolset.org](https://wixtoolset.org/). A review of the WiX open source implementation of this Protocol attribute may be required for integration.  
  
## <a name="controlling-what-is-installed"></a>설치되는 기능 제어  
 최종 사용자가 설치할 수 있는 기능을 제어하려는 경우 관리자 파일 설치와 명령줄 옵션의 두 가지 옵션이 있습니다. 최종 사용자가 Visual Studio 설치 관리자 환경에서 선택할 수 있는 기능을 제한하려는 경우 관리자 파일 설치를 선택합니다. 초기 구성을 만들지만 최종 사용자가 고유한 Visual Studio 설치 관리자 환경을 선택할 수 있게 하려는 경우 명령줄 매개 변수를 선택합니다.  
  
 관리자 파일 환경에 대한 자세한 내용은 [How to: Create and Run an Unattended Installation of Visual Studio](../install/how-to-create-and-run-an-unattended-installation-of-visual-studio.md) 및 [How to: Automatically apply product keys when deploying Visual Studio](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md)을 참조하세요.  For more information on the command-line controls, see the [Use Command-Line Parameters to Install Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) page.  
  
## <a name="specifying-customer-feedback-settings"></a>사용자 의견 설정 지정  

기본적으로 Visual Studio 설치에서는 고객 의견을 허용합니다. 다음 레지스트리 키의 값을 문자열 "0"으로 변경하여 Visual Studio에서 개별 컴퓨터의 고객 의견을 허용하지 않도록 구성할 수 있습니다.  
  
**HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SQM**  
**OptIn**  
  
예를 들어 HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SQM OptIn="0"으로 변경합니다.  
  
## <a name="related-topics"></a>관련 항목  
  
|항목|설명|  
|-----------|-----------------|  
|[방법: Visual Studio의 특정 릴리스 설치](../install/how-to-install-a-specific-release-of-visual-studio.md)|Describes how to install specific configurations of the current version of  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|[방법: Visual Studio 무인 설치 만들기 및 실행](../install/how-to-create-and-run-an-unattended-installation-of-visual-studio.md)|Describes how to install [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in unattended mode.|  
|[방법: Visual Studio를 배포할 때 제품 키를 자동으로 적용](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md)|Describes how to apply product keys when deploying to multiple machines.|  
|[도움말 뷰어 관리자 가이드](../ide/help-viewer-administrator-guide.md)|Provides information about  how to manage local Help installations for network environments that either have or do not have internet access.|  
|[Visual Studio 설치](../install/install-visual-studio-2015.md)|Provides instructions and  links to topics that describe how to install [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|