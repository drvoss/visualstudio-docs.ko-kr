---
title: '방법: Visual Studio 2015로 확장성 프로젝트 마이그레이션 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, upgrading
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 41bf80c8ae00aa22666750de7b4b23df981c8465
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435929"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2015"></a>방법: Visual Studio 2015로 확장성 프로젝트 마이그레이션
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

확장 프로그램을 업그레이드 하는 방법을 다음과 같습니다.  
  
> [!IMPORTANT]
> Visual Studio의 이전 버전에 대 한 확장 솔루션의 버전을 유지 하려는 경우 업그레이드 전에 복사본을 확인 해야 합니다. 업그레이드 된 버전 이전 상태로 돌아갑니다 어려울 수 있습니다.  
  
#### <a name="to-upgrade-an-extensibility-solution"></a>확장성 솔루션을 업그레이드 하려면  
  
1. 복사를 사용 하 하려면 업그레이드, 새 버전에서 엽니다. 업그레이드는 되돌릴 수 없는 것이 좋습니다 됩니다.  
  
2. 업그레이드를 완료 한 후 새 버전의 devenv.exe 외부 프로그램의 경로 변경 합니다. 프로젝트 노드를 마우스 오른쪽 단추로 클릭 합니다 **솔루션 탐색기**, 선택한 **속성**합니다. 에 **디버그** 탭에서에서 텍스트 찾기 **시작 외부 프로그램** 비슷합니다이 Visual Studio 2015 경로로 devenv.exe의 경로 변경 하 고:  
  
     **%ProgramFiles%\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe**  
  
3. Microsoft.VisualStudio.Shell.14.0.dll에 대 한 참조를 추가 합니다. (에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 합니다 **솔루션 탐색기** 를 선택한 후 **/reference 추가**합니다. 선택 된 **확장** 탭을 확인 한 다음 **Microsoft.VisualStudio.Shell.14.0**.)  
  
4. 솔루션을 빌드합니다. 빌드 파일에 배포 됩니다.  
  
     **%LOCALAPPDATA%\Microsoft\VisualStudio.14.0Exp\Extensions\\< 이름 작성\>\\< 프로젝트 이름\>\\< 프로젝트 버전\>\\**합니다.  
  
#### <a name="to-update-an-extensibility-project-to-nuget-vs-sdk-reference-assemblies"></a>확장성 프로젝트를 NuGet VS SDK 참조 어셈블리를 업데이트 하려면  
  
1. 프로젝트에 필요한 VS SDK 참조 어셈블리를 결정 합니다.  **솔루션 탐색기**에서 프로젝트의 확장 **참조** 노드와 프로젝트 참조 목록 검토 합니다.  VS SDK 참조 어셈블리는 접두사가 **Microsoft.VisualStudio** 이름에서 (예: Microsoft.VisualStudio.Shell.14.0).  
  
2. VS SDK 참조 어셈블리를 선택 하 여 프로젝트에서 제거, 마우스 오른쪽 단추로 클릭 하 고 **제거**합니다.  
  
3. VS SDK 참조 어셈블리의 NuGet 버전을 추가 합니다.  **솔루션 탐색기 참조** 노드를 열고는 **NuGet 패키지 관리...** 대화 상자입니다.  이 대화 상자에 자세히 알아보려면 원한다 면 참조 [대화 상자를 사용 NuGet 패키지 관리](http://docs.nuget.org/Consume/Package-Manager-Dialog)합니다. VS SDK 참조 어셈블리에 게시 되어 [nuget.org](http://www.nuget.org) 하 여 [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility)합니다.  
  
4. 사용 하 여 **nuget.org** 으로 프로그램 **패키지 원본**, 원하는 참조 어셈블리에 일치 하는 NuGet 패키지 이름 검색 (예를 들어: Microsoft.VisualStudio.Shell.14.0) 프로젝트에 설치 합니다.  NuGet은 초기 어셈블리의 종속성을 충족 하기 위해 여러 명의 참조 어셈블리를 추가할 수 있습니다.  
  
     원한다 면 수 추가한 모든 VS SDK 참조 어셈블리를 한 번에 VS SDK를 설치 하 여 [메타 패키지가](http://www.nuget.org/packages/VSSDK_Reference_Assemblies)합니다.  
  
5. NuGet 버전의 VS SDK 빌드 도구를 사용 하 여 전환할 수 있습니다. 이 NuGet 패키지는 [Microsoft.VSSDK.BuildTools](http://www.nuget.org/packages/Microsoft.VSSDK.BuildTools) 한 번에 추가 하 고 프로젝트에 필요한 도구가 포함 되며 대상 컴퓨터에서 VS SDK를 설치 하지 않고 확장성 프로젝트를 빌드할 수 있도록 파일입니다.  
  
> [!NOTE]
> 없는 NuGet 참조 어셈블리 및 도구를 사용 하도록 기존 확장성 프로젝트를 업데이트 하는 필수입니다.  참조 어셈블리 및 VS SDK를 사용 하 여 설치 된 도구를 사용 하 여 빌드를 계속 수 있습니다.
