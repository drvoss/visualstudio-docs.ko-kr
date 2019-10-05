---
title: '방법: 자체 호스팅된 WCF 서비스 디버그 | Microsoft Docs'
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
- debugging, WCF
- WCF, self-hosted service
- WCF, debugging
ms.assetid: 288922be-ba3f-411e-af50-bba39c9529cc
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e58acc6323f396f9b0755e84b369ce0fdf413c08
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68185173"
---
# <a name="how-to-debug-a-self-hosted-wcf-service"></a>방법: 자체 호스팅 WCF 서비스 디버그
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*자체 호스팅 서비스*는 IIS, WCF 서비스 호스트 또는 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Development Server 내에서 실행되지 않는 WCF 서비스입니다. 자체 호스팅된 WCF를 디버그 하는 가장 쉬운 방법은 구성 하는 것 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 선택 하면 클라이언트와 서버를 시작 하려면 **디버깅 시작** 에 **디버그** 메뉴.  
  
 WCF 서비스가 자체 호스트 하는 내부 또는 NT 서비스와 같은 이러한 방식으로 시작할 수 없는 프로세스 하는 경우이 메서드를 사용할 수 없습니다. 대신, 다음 중 하나를 수행할 수 있습니다.  
  
- 호스팅 프로세스에 디버거를 수동으로 연결 합니다. 자세한 내용은 [실행 중인 프로세스에 연결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)합니다.  
  
     — 또는 —  
  
- 클라이언트에서 디버깅을 시작 하 고 서비스 호출으로 다음 단계입니다. 이 app.config 파일에서 디버깅을 사용 해야 합니다. 자세한 내용은 [WCF 디버깅의 제한 사항](../debugger/limitations-on-wcf-debugging.md)합니다.  
  
### <a name="to-start-both-client-and-host-from-visual-studio"></a>Visual Studio에서 클라이언트와 호스트를 시작 하려면  
  
1. 만들기는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 클라이언트와 서버 프로젝트가 포함 된 솔루션입니다.  
  
2. 선택 하면 클라이언트와 서버 프로세스를 시작 하도록 솔루션 구성 **시작** 에 **디버그** 메뉴.  
  
    1. **솔루션 탐색기**, 솔루션 이름을 마우스 오른쪽 단추로 클릭 합니다.  
  
    2. 클릭 **시작 프로젝트 설정**합니다.  
  
    3. **솔루션 \<이름> 속성** 대화 상자에서 **여러 시작 프로젝트**를 선택합니다.  
  
    4. 에 **여러 개의 시작 프로젝트** 서버 프로젝트에 해당 하는 줄 눈금 클릭 **작업** 선택한 **시작**합니다.  
  
    5. 클라이언트 프로젝트에 해당 하는 줄에서 클릭 **동작** 선택한 **시작**합니다.  
  
    6. **확인**을 클릭합니다.  
  
## <a name="see-also"></a>참고 항목  
 [WCF 서비스 디버그](../debugger/debugging-wcf-services.md)   
 [WCF 디버깅의 제한 사항](../debugger/limitations-on-wcf-debugging.md)   
 [방법: WCF 서비스 한 단계씩 코드 실행](../debugger/how-to-step-into-wcf-services.md)
