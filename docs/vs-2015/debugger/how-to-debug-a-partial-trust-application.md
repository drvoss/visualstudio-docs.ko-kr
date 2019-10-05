---
title: '방법: 부분 신뢰 응용 프로그램 디버그 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], partial trust applications
- partial trust applications
- security [Visual Studio], partial trust applications
ms.assetid: 9d30ad92-28ce-4b21-91d8-698474cddf64
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 030fef750cc1e0f0932de32fca1a0ffef56bc8f3
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704479"
---
# <a name="how-to-debug-a-partial-trust-application"></a>방법: 부분 신뢰 응용 프로그램 디버그
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows 및 콘솔 애플리케이션에 적용됩니다.  
  
 [ClickOnce 보안 및 배포](../deployment/clickonce-security-and-deployment.md) 쉽게 활용 하는 부분 신뢰 응용 프로그램을 배포 [코드 액세스 보안](https://msdn.microsoft.com/library/859af632-c80d-4736-8d6f-1e01b09ce127) 컴퓨터에서 리소스에 대 한 액세스를 제한 합니다.  
  
 부분 신뢰 애플리케이션은 어떠한 경로를 통해 설치했는지에 따라 보안 권한 및 동작이 달라지므로 디버깅하기가 어려울 수 있습니다. 부분 신뢰 애플리케이션을 인터넷을 통해 설치한 경우에는 애플리케이션에 권한이 거의 없습니다. 로컬 인트라넷에서 설치한 경우에는 좀 더 많은 권한이 부여되고, 로컬 컴퓨터에서 설치하면 모든 권한이 부여됩니다. 사용자 지정 권한으로 사용자 지정 영역을 설정할 수도 있습니다. 부분 신뢰 애플리케이션은 이러한 임의의 조건 아래에서 디버깅해야 할 수 있습니다. Visual Studio를 사용하면 이와 같은 복잡한 디버깅 작업도 쉽게 수행할 수 있습니다.  
  
 Visual Studio에서 디버그 세션을 시작하기 전에 애플리케이션을 설치하는 데 사용할 영역을 선택하여 시뮬레이션할 수 있습니다. 디버깅을 시작할 때 애플리케이션에는 해당 영역을 통해 설치된 부분 신뢰 애플리케이션에 허용되는 적절한 권한이 부여됩니다. 이렇게 하면 해당 영역에서 애플리케이션을 다운로드한 사용자에게 제공되는 것과 동일한 애플리케이션 동작을 확인할 수 있습니다.  
  
 권한이 없는 작업을 애플리케이션에서 수행하면 예외가 발생합니다. 이 경우 예외 도우미를 사용하면 필요한 권한을 추가할 수 있으므로 충분한 권한을 부여하여 문제 없이 디버깅 세션을 다시 시작할 수 있습니다.  
  
 나중에 디버깅 과정에서 추가했던 권한을 다시 검토할 수 있습니다. 디버깅하는 동안 권한을 추가해야 했다면 대개의 경우 이는 코드의 해당 지점에 사용자 동의 메시지를 추가해야 함을 의미합니다.  
  
> [!NOTE]
> 디버거 시각화 도우미에는 부분 신뢰 애플리케이션에 허용되는 것보다 많은 권한이 필요합니다. 부분 신뢰 코드에서 중지하면 시각화 도우미가 로드되지 않습니다. 시각화 도우미를 사용하여 디버깅하려면 완전 신뢰 코드를 실행해야 합니다.  
  
### <a name="to-choose-a-zone-for-your-partial-trust-application"></a>부분 신뢰 애플리케이션의 영역을 선택하려면  
  
1. **프로젝트** 메뉴 선택 _Projectname_**속성**합니다.  
  
2. 에 *Projectname* 속성 페이지를 클릭 합니다 **보안** 페이지입니다.  
  
3. 선택 **ClickOnce 보안 설정 사용**합니다.  
  
4. 아래 **영역에서 응용 프로그램을 설치할**, 드롭다운 목록 상자를 클릭 하 고 응용 프로그램을 설치 중인 시뮬레이션 하려는 영역을 선택 합니다.  
  
     합니다 **응용 프로그램에 필요한 사용 권한에** 표 형식으로 사용할 수 있는 모든 권한을 표시 합니다. 확인 표시는 애플리케이션에 해당 권한이 부여되어 있음을 나타냅니다.  
  
5. 선택한 영역이 경우 **(사용자 지정)** 에서 올바른 사용자 지정 설정을 선택 합니다 **설정** 열의 **권한을** 표.  
  
6. **확인**을 클릭하여 속성 페이지를 닫습니다.  
  
### <a name="to-add-an-extra-permission-when-a-security-exception-occurs"></a>보안 예외가 발생한 경우 필요한 권한을 추가하려면  
  
1. 합니다 **예외 도우미** 메시지와 함께 대화 상자가 나타납니다. **SecurityException 처리 되지 않았습니다.**  
  
2. 에 **예외 도우미** 대화 상자의 **동작**, 클릭 **프로젝트에 추가 권한**합니다.  
  
3. 합니다 **디버깅 다시 시작** 대화 상자가 나타납니다.  
  
    - 새 사용 권한 사용 하 여 디버깅 세션을 다시 시작 하려면 클릭 **예**합니다.  
  
    - 아직 다시 시작 하지 않으려는 경우 클릭 **No**합니다.  
  
### <a name="to-view-extra-permissions-added-while-debugging"></a>디버깅하는 동안 추가된 권한을 보려면  
  
1. **프로젝트** 메뉴 선택 _Projectname_**속성**합니다.  
  
2. 에 *Projectname* 속성 페이지를 클릭 합니다 **보안** 페이지입니다.  
  
3. 확인 합니다 **응용 프로그램에 필요한 사용 권한에** 표입니다. 추가한 모든 추가 사용 권한을 두 아이콘에는 **포함 된** 열: 포함 된 모든 사용 권한을 적용 되는 일반적인 확인 하 고 "i" 문자가 포함 된 풍선 모양의 추가 아이콘이 있습니다.  
  
4. 세로 스크롤 막대를 사용 하 여 전체를 볼 **응용 프로그램에 필요한 사용 권한에** 표입니다.  
  
## <a name="see-also"></a>참고 항목  
 [ClickOnce 보안 및 배포](../deployment/clickonce-security-and-deployment.md)   
 [디버거 보안](../debugger/debugger-security.md)
