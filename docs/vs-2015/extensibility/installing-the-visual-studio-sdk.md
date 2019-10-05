---
title: Visual Studio SDK 설치 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: visual-studio-sdk
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 88a6266a3f5910def0bf5041a37f89c2b3d67416
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63414460"
---
# <a name="installing-the-visual-studio-sdk"></a>Visual Studio SDK 설치
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2015부터 수행 설치 하면 Visual Studio SDK 다운로드 센터에서. Visual Studio 설치에서 선택적 기능으로 포함 됩니다. 또한 VS SDK를 나중에 설치할 수 있습니다.  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Visual Studio 설치의 일부로 Visual Studio SDK 설치  
 Visual Studio 설치에서 VSSDK를 포함 하려는 경우 사용자 지정 설치를 수행 해야 합니다.  
  
> [!NOTE]
> 설치 실행 파일을 Visual Studio SDK 라고 **Visual Studio 확장성 도구**합니다.  
  
1. Visual Studio 2015 설치를 시작 합니다. Visual studio Express 제외한 모든 버전을 설치할 수 있습니다.  
  
2. 첫 번째 화면에서 선택 **사용자 지정**가 아닌 **기본**입니다. **다음**을 클릭합니다.  
  
3. 사용자 지정 기능을 트리 뷰로 표시 됩니다. 오픈 **일반적인 도구**합니다. 나타납니다 **Visual Studio 확장성 도구** 합니다.  
  
     ![VSSDKInstall](../extensibility/media/vssdkinstall.png "VSSDKInstall")  
  
4. 확인할 **Visual Studio 확장성 도구** , 클릭 **다음** 설치를 계속 합니다.  
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Visual Studio를 설치한 후 Visual Studio SDK를 설치 합니다.  
 Visual Studio 설치를 완료 한 후 Visual Studio SDK를 설치 하려는 경우 다음 절차를 따라야 합니다.  
  
1. 로 이동 **제어판 / 프로그램 / 프로그램 및 기능**을 찾아 **Visual Studio 2015**합니다. Visual Studio 2015 Express 제외한 어떤 버전이 든 Visual Studio SDK를 설치할 수 있습니다.  
  
2. 마우스 오른쪽 단추로 클릭 **Visual Studio 2015**를 클릭 하 고 **변경**합니다. 설치 페이지가 나타납니다.  
  
3. 와 동일한 절차에 따라 **Visual Studio 설치의 일부로 Visual Studio SDK 설치** 위에 있습니다.  
  
4. 클릭 합니다 **Visual Studio 확장성 도구** Visual Studio SDK를 설치 하는 링크입니다.  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>솔루션에서 Visual Studio SDK 설치  
 VSSDK를 먼저 설치 하지 않고 확장성 프로젝트를 사용 하 여 솔루션을 열 경우 솔루션 탐색기 위에 강조 표시 된 정보의 막대로 묻는 메시지가 나타납니다. 다음과 유사한 출력이 표시 됩니다.  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>명령줄에서 Visual Studio SDK 설치  
 사용 하 여 명령줄에서 VSSDK를 설치할 수 있습니다 합니다 **/InstallSelectableItems** Visual Studio 설치 관리자를 사용 하 여 전환 합니다. 설치 관리자를 사용 하 여 명령줄 매개 변수를 사용 하는 방법에 대 한 자세한 내용은 참조 하세요 [Visual Studio 2015 설치](../install/install-visual-studio-2015.md)합니다.  
  
 VSSDK Visual Studio 2015 Community 설치 관리자를 사용 하 여 자동으로 설치 하는 방법을 다음과 같습니다.  
  
```  
vs_community.exe /s /installSelectableItems VS_SDK_GROUPV1  
```  
  
 Visual Studio의 설치 된 버전과 일치 하는 Visual Studio 설치 관리자를 사용 해야 하는 참고 합니다. 예를 들어, Visual Studio Enterprise를 컴퓨터에 설치 된 경우 Visual Studio Enterprise (vs_enterprise.exe) 설치 관리자를 실행 해야 합니다.
