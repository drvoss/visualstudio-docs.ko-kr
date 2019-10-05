---
title: System.Deployment.Application을 사용 하는 ClickOnce 응용 프로그램 디버그 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, debugging
- debugging, ClickOnce applications
- debugging, System.Deployment
- deploying applications [ClickOnce], debugging
ms.assetid: 86f31948-2ca8-47c0-8e8b-c2b817bbf79f
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c0b12faf451d3ed9bb70e2bb1ec6c8503cfb86d5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68187788"
---
# <a name="debugging-clickonce-applications-that-use-systemdeploymentapplication"></a>System.Deployment.Application을 사용하는 ClickOnce 응용 프로그램 디버깅
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 배포를 사용 하면 응용 프로그램 업데이트 되는 방식을 구성할 수 있습니다. 그러나 사용 및 사용자 지정 하는 경우 고급 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 제공한 배포 개체 모델에 액세스 해야 배포 기능을 <xref:System.Deployment.Application>입니다. 사용할 수는 <xref:System.Deployment.Application> 와 같은 고급 작업에 대 한 Api:  
  
- 응용 프로그램에서 "지금 업데이트" 옵션 만들기  
  
- 다양 한 응용 프로그램 구성 요소, 조건부 요청 시 다운로드  
  
- 응용 프로그램에 직접 통합 하는 업데이트  
  
- 클라이언트 응용 프로그램이 항상 최신 상태 인지 보장  
  
  때문에 합니다 <xref:System.Deployment.Application> Api 응용 프로그램으로 배포 되는 경우에 작동 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 사용 하 여 응용 프로그램을 배포 하는 기술 프로젝트를 디버깅 하는 유일한 방법은 것 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]를 연결할 차례로 디버그 하 합니다. 디버거를 연결 하기 어려울 수 있으므로이 코드는 종종 응용 프로그램이 시작 되 고 디버거를 연결 하기 전에 실행 될 때 실행 충분히 초기 합니다. 솔루션을 나누기 (또는 Visual Basic 프로젝트에 대 한 중지) 프로그램 업데이트 확인 코드 또는 주문형으로 코드 앞에 배치 하는 것입니다.  
  
  권장 되는 디버깅 기술을 아래와 같습니다.  
  
1. 시작 하기 전에 기호 (.pdb) 및 원본 파일을 보관 해야 합니다.  
  
2. 응용 프로그램의 버전 1을 배포 합니다.  
  
3. 새 빈 솔루션을 만듭니다. **파일** 메뉴에서 클릭 **새로 만들기**, 한 다음 **프로젝트**. 에 **새 프로젝트** 대화 상자를 엽니다는 **기타 프로젝트 형식** 노드를 선택한 합니다 **Visual Studio 솔루션** 폴더입니다. 에 **템플릿을** 창 **빈 솔루션**합니다.  
  
4. 이 새 솔루션에 대 한 속성에 보관 된 원본 위치를 추가 합니다. **솔루션 탐색기**에서 솔루션 노드를 마우스 오른쪽 단추로 클릭 **속성**합니다. 에 **속성 페이지** 대화 상자에서 **소스 파일 디버그**, 한 다음 보관된 된 소스 코드의 디렉터리를 추가 합니다. 이 고, 그렇지 디버거가 있으므로 원본 파일 경로.pdb 파일에 기록 됩니다 오래 된 소스 파일을 찾이 됩니다. 만료 된 소스 파일을 사용 하는 디버거를 경우 원본 일치 하지 않는 알려 주는 메시지가 표시 됩니다.  
  
5. 디버거에서.pdb 파일을 찾을 수 있는지 확인 합니다. 이러한 응용 프로그램을 배포한 경우 디버거가 찾은 자동으로 합니다. 이 항상 어셈블리 옆에 있는 해당 먼저 찾습니다. 보관 경로를 추가 해야 하는 고, 그렇지는 **기호 파일 (.pdb) 위치** (에서이 옵션에 액세스 하는 **도구** 메뉴에서 클릭 **옵션**를 열고 다음을  **디버깅** 노드를 마우스 클릭 **기호**).  
  
6. 디버그 간에 발생 합니다 `CheckForUpdate` 하 고 `Download` / `Update` 메서드 호출.  
  
    예를 들어 업데이트 코드는 다음과 같을 수 있습니다.  
  
   ```  
       Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
           If My.Application.Deployment.IsNetworkDeployed Then  
  
               If (My.Application.Deployment.CheckForUpdate()) Then  
  
                   My.Application.Deployment.Update()  
                   Application.Restart()  
  
               End If  
  
           End If  
       End Sub  
   ```  
  
7. 버전 2를 배포 합니다.  
  
8. 버전 2 용 업데이트 다운로드 될 때 버전 1 응용 프로그램에 디버거를 연결 하려고 시도 합니다. 또는 사용할 수 있습니다 합니다 `System.Diagnostics.Debugger.Break` 메서드 또는 단순히 `Stop` Visual Basic의 합니다. 물론 프로덕션 코드에서는 이러한 메서드 호출을 하지 유지 해야 합니다.  
  
    예를 들어 Windows Forms 응용 프로그램을 개발 하는 및에 업데이트 논리를 사용 하 여이 메서드에 대 한 이벤트 처리기를 사용 해야 합니다. 이 디버깅 하려면 연결 하기만 하면 단추는 누른 다음 중단점을 설정 하기 전에 (적절 한 보관된 파일을 열고 여기서 중단점을 설정 했는지 확인).  
  
   사용 하 여는 <xref:System.Deployment.Application.ApplicationDeployment.IsNetworkDeployed%2A> 를 호출 하는 속성을 <xref:System.Deployment.Application> Api는 응용 프로그램을 배포 하는 경우에; Api 호출 되지 않도록에서 디버깅 하는 동안 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]합니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:System.Deployment.Application>
