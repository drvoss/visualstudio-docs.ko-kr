---
title: '방법: ClickOnce 응용 프로그램에 대 한 업데이트 관리 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.Update
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, managing applications
- ClickOnce deployment, updates
- updating data, ClickOnce
- application updates
ms.assetid: a3f23f05-e7f1-4620-b23c-2d68f9643684
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0754d816104832f92a0be8d754046d1ee18e7a09
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697644"
---
# <a name="how-to-manage-updates-for-a-clickonce-application"></a>방법: ClickOnce 애플리케이션에 대한 업데이트 관리
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램 업데이트를 자동으로 또는 프로그래밍 방식으로 확인할 수 있습니다. 개발자는 업데이트 검사를 수행 하는 방법과 시기, 필수 업데이트 인지 여부 및 업데이트를 확인 하는 위치를 지정 하는 유연성을 많이 해야 합니다.  
  
 응용 프로그램이 시작 된 후 설정 된 간격으로 또는 응용 프로그램 시작 전에 자동으로 업데이트를 확인 하려면 응용 프로그램을 구성할 수 있습니다. 또한을 최소 필수 버전으로 지정할 수 있습니다. 즉, 사용자의 버전이 필수 버전 보다 낮은 경우에 업데이트가 설치 됩니다.  
  
 예: 사용자 요청 이벤트에 따라 프로그래밍 방식으로 업데이트를 확인 하려면 응용 프로그램을 구성할 수 있습니다. 프로그래밍 방식으로 업데이트 확인"하려면" 절차가이 항목에서 사용 하는 코드를 작성 하는 방법을 보여 줍니다는 <xref:System.Deployment.Application.ApplicationDeployment> 업데이트를 확인 하려면 클래스 이벤트를 기반으로 합니다.  
  
 또한 한 위치에서 응용 프로그램을 배포 하 고 다른 업데이트할 수 있습니다. 다른 업데이트 위치를 지정 합니다."하려면" 절차를 참조 하세요.  
  
 자세한 내용은 [ClickOnce 업데이트 전략 선택](../deployment/choosing-a-clickonce-update-strategy.md)을 참조하세요.  
  
 관리 하는 업데이트 동작을 **응용 프로그램 업데이트** 에서 사용할 수 있는 대화 상자를 **게시** 페이지를 **프로젝트 디자이너.**  
  
### <a name="to-check-for-updates-before-the-application-starts"></a>응용 프로그램을 시작 하기 전에 업데이트를 확인 하려면  
  
1. **솔루션 탐색기**에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴에서 **속성**을 클릭합니다.  
  
2. **게시** 탭을 클릭합니다.  
  
3. 클릭 합니다 **업데이트** 버튼을 클릭 합니다 **응용 프로그램 업데이트** 대화 상자.  
  
4. 에 **응용 프로그램 업데이트** 대화 상자에서 확인를 **응용 프로그램의 업데이트 확인** 확인란을 선택 합니다.  
  
5. 에 **응용 프로그램 업데이트를 확인 해야 하는 경우 선택** 섹션에서 **응용 프로그램을 시작 하기 전에**입니다. 이렇게 하면 항상 네트워크에 연결 된 사용자는 최신 업데이트를 사용 하 여 응용 프로그램을 실행 합니다.  
  
### <a name="to-check-for-updates-in-the-background-after-the-application-starts"></a>애플리케이션을 시작한 후 백그라운드에서 업데이트를 확인하려면  
  
1. **솔루션 탐색기**에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴에서 **속성**을 클릭합니다.  
  
2. **게시** 탭을 클릭합니다.  
  
3. 클릭 합니다 **업데이트** 버튼을 클릭 합니다 **응용 프로그램 업데이트** 대화 상자.  
  
4. 에 **응용 프로그램 업데이트** 대화 상자에서 확인 확인란 **응용 프로그램의 업데이트 확인** 선택 합니다.  
  
5. 에 **응용 프로그램 업데이트 확인 해야 하는 경우 선택**를 선택 **응용 프로그램이 시작 된 후**합니다. 응용 프로그램에는 이러한 방식으로 더 빠르게 시작 되 고 백그라운드에서 업데이트를 확인 하 고 업데이트를 사용할 때만 사용자에 게 알립니다. 설치 되 면 응용 프로그램을 다시 시작할 때까지 업데이트 효과 적용 되지 않습니다.  
  
6. 에 **응용 프로그램의 업데이트 확인 빈도 지정** 섹션을 선택 **응용 프로그램을 실행할 때마다 확인** (기본값) 또는 **확인 모든** 선택한 시간 및 숫자 간격을 입력 합니다.  
  
### <a name="to-specify-a-minimum-required-version-for-the-application"></a>응용 프로그램에 대 한 최소 필수 버전을 지정 하려면  
  
1. **솔루션 탐색기**에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴에서 **속성**을 클릭합니다.  
  
2. **게시** 탭을 클릭합니다.  
  
3. 클릭 합니다 **업데이트** 버튼을 클릭 합니다 **응용 프로그램 업데이트** 대화 상자.  
  
4. 에 **응용 프로그램 업데이트** 대화 상자에서 확인를 **응용 프로그램의 업데이트 확인** 확인란을 선택 합니다.  
  
5. 선택 합니다 **이 응용 프로그램에 필요한 최소 버전 지정** 확인란을 선택한 다음 입력 **주요**를 **부**, **빌드**, 및  **수정 버전** 응용 프로그램에 대 한 번호입니다.  
  
### <a name="to-specify-a-different-update-location"></a>다양 한 업데이트 위치를 지정 하려면  
  
1. **솔루션 탐색기**에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴에서 **속성**을 클릭합니다.  
  
2. **게시** 탭을 클릭합니다.  
  
3. 클릭 합니다 **업데이트** 버튼을 클릭 합니다 **응용 프로그램 업데이트** 대화 상자.  
  
4. 에 **응용 프로그램 업데이트** 대화 상자에서 확인를 **응용 프로그램의 업데이트 확인** 확인란을 선택 합니다.  
  
5. 에 **위치를 업데이트** 필드 형식을 사용 하는 정규화 된 URL로 업데이트 위치를 입력 합니다 http://Hostname/ApplicationName, 또는 UNC 경로 형식을 사용 하 \\\Server\ApplicationName, 또는 클릭을 **찾아보기** 단추를 업데이트 위치를 찾습니다.  
  
### <a name="to-check-for-updates-programmatically"></a>프로그래밍 방식으로 업데이트를 확인 하려면  
  
1. **솔루션 탐색기**에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴에서 **속성**을 클릭합니다.  
  
2. **게시** 탭을 클릭합니다.  
  
3. 클릭 합니다 **업데이트** 버튼을 클릭 합니다 **응용 프로그램 업데이트** 대화 상자.  
  
4. 에 **응용 프로그램 업데이트** 대화 상자에서 확인를 **응용 프로그램의 업데이트 확인** 확인란의 선택을 취소 합니다. (필요에 따라 선택할 수 있습니다 수 ClickOnce 런타임에서 자동으로 업데이트 확인을 그리고 프로그래밍 방식으로 업데이트를 확인 하려면이 확인란.)  
  
5. 에 **위치를 업데이트** 필드 형식을 사용 하는 정규화 된 URL로 업데이트 위치를 입력 합니다 http://Hostname/ApplicationName, 또는 UNC 경로 형식을 사용 하 \\\Server\ApplicationName, 또는 클릭을 **찾아보기** 단추를 업데이트 위치를 찾습니다. 업데이트 위치는 자체의 업데이트 된 버전에 대 한 응용 프로그램을 찾을 위치입니다.  
  
6. 업데이트를 확인 하려면 사용자를 선택 하는 Windows 폼에 단추, 메뉴 항목 또는 기타 사용자 인터페이스 항목을 만듭니다. 해당 항목의 이벤트 처리기에서 확인 하 고 업데이트를 설치 하는 메서드를 호출 합니다. Visual Basic 및 Visual의 예제를 찾을 수 있습니다 C# 에서 이러한 메서드에 대 한 코드 [방법: ClickOnce 배포 API를 사용 하 여 프로그래밍 방식으로 응용 프로그램 업데이트 확인](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)합니다.  
  
7. 응용 프로그램을 빌드하십시오.  
  
## <a name="see-also"></a>참고 항목  
 <xref:System.Deployment.Application.ApplicationDeployment>   
 [응용 프로그램 업데이트 대화 상자](https://msdn.microsoft.com/8eca8743-8e68-4d04-bfd5-4dc0a9b2934f)   
 [ClickOnce 업데이트 전략 선택](../deployment/choosing-a-clickonce-update-strategy.md)   
 [ClickOnce 응용 프로그램 게시](../deployment/publishing-clickonce-applications.md)   
 [방법: 게시 마법사를 사용 하 여 ClickOnce 응용 프로그램 게시](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [방법: ClickOnce 배포 API를 사용하여 프로그래밍 방식으로 애플리케이션 업데이트 확인](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)
