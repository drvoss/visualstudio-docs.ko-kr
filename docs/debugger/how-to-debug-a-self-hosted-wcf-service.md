---
title: '방법: 자체 호스팅 WCF 서비스 디버그 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, self-hosted service
- WCF, debugging
ms.assetid: 288922be-ba3f-411e-af50-bba39c9529cc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12654a6aa1abb34c9813e8d29c7608814021a3f0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72733975"
---
# <a name="how-to-debug-a-self-hosted-wcf-service"></a>방법: 자체 호스팅 WCF 서비스 디버깅
*자체 호스팅 서비스*는 IIS, WCF 서비스 호스트 또는 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Development Server 내에서 실행되지 않는 WCF 서비스입니다. 자체 호스팅 WCF를 디버그 하는 가장 쉬운 방법은 **디버그** 메뉴에서 **디버깅 시작** 을 선택 하는 경우 클라이언트와 서버를 둘 다 시작 하도록 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]를 구성 하는 것입니다.

 WCF 서비스가 내에서 자체 호스팅 이거나 이러한 방식으로 시작할 수 없는 프로세스 (예: NT service) 인 경우에는이 방법을 사용할 수 없습니다. 대신 다음 중 하나를 수행할 수 있습니다.

- 디버거를 호스팅 프로세스에 수동으로 연결 합니다. 자세한 내용은 [실행 중인 프로세스에 연결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)을 참조 하세요.

     — 또는 —

- 클라이언트 디버깅을 시작한 다음 서비스 호출을 한 단계씩 실행 합니다. 이렇게 하려면 app.config 파일에서 디버깅을 사용 하도록 설정 해야 합니다. 자세한 내용은 [WCF 디버깅의 제한 사항](../debugger/limitations-on-wcf-debugging.md)을.

### <a name="to-start-both-client-and-host-from-visual-studio"></a>Visual Studio에서 클라이언트와 호스트를 모두 시작 하려면

1. 클라이언트 및 서버 프로젝트를 모두 포함 하는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 솔루션을 만듭니다.

2. **디버그** 메뉴에서 **시작** 을 선택 하는 경우 클라이언트 및 서버 프로세스를 모두 시작 하도록 솔루션을 구성 합니다.

   1. **솔루션 탐색기**에서 솔루션 이름을 마우스 오른쪽 단추로 클릭 합니다.

   2. **시작 프로젝트 설정**을 클릭 합니다.

   3. **솔루션 \<이름> 속성** 대화 상자에서 **여러 시작 프로젝트**를 선택합니다.

   4. **여러 시작 프로젝트** 표에서 서버 프로젝트에 해당 하는 줄을 클릭 하 고 **작업** 을 클릭 한 다음 **시작**을 선택 합니다.

   5. 클라이언트 프로젝트에 해당 하는 줄에서 **작업** 을 클릭 하 고 **시작**을 선택 합니다.

   6. **확인**을 클릭합니다.

## <a name="see-also"></a>참조
- [WCF 서비스 디버그](../debugger/debugging-wcf-services.md)
- [WCF 디버깅의 제한 사항](../debugger/limitations-on-wcf-debugging.md)
- [방법: WCF 서비스 한 단계씩 실행](../debugger/how-to-step-into-wcf-services.md)