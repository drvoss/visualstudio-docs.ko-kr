---
title: '방법: Code Center Premium 소스로 사용 하 여 디버그 | Microsoft Docs'
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
- Code Center Premium
- debugging [Visual Studio], Code Center Premium
ms.assetid: 18b4769d-b007-4428-9dae-9e72c283ff0d
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: db9a3e08e14e7fadca6df9e32361c0b042f565e9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438330"
---
# <a name="how-to-debug-with-code-center-premium-source"></a>방법: Code Center Premium 소스로 사용 하 여 디버그
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 디버거를 사용하면 Microsoft MSDN Code Center Premium의 보안 공유 소스를 디버깅할 수 있습니다.  
  
 이 항목에서는 Visual Studio에서 Code Center Premium을 설치하고 소스 코드를 디버깅하는 방법에 대해 설명합니다.  
  
### <a name="to-prepare-for-debugging-with-code-center-premium"></a>Code Center Premium을 사용하여 디버깅할 수 있도록 준비하려면  
  
1. 스마트 카드 판독기를 연결하고 Shared Source Initiative에서 받은 카드를 삽입합니다.  
  
2. Visual Studio를 실행합니다.  
  
3. **도구** 메뉴에서 **옵션**을 클릭합니다.  
  
4. 에 **옵션** 대화 상자를 열고 합니다 **디버깅** 노드를 클릭 **일반**.  
  
5. 선택을 취소 합니다 **내 코드만 사용 (관리 전용)** 확인란 합니다.  
  
6. 선택 **소스 서버 지원 사용**합니다.  
  
7. 명확한 **원래 버전과 정확 하 게 일치 원본 파일 필요한**합니다.  
  
8. 아래는 **디버깅** 노드를 클릭 **기호**합니다.  
  
9. 에 **기호 파일 (.pdb) 위치** 상자에서 지우기 합니다 **Microsoft 기호 서버** 확인란을 선택 하 고 다음 위치를 추가:  
  
     `https://codepremium.msdn.microsoft.com/symbols`  
  
     `src=https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
   > [!NOTE]
   > 후행 슬래시를 포함 해야<strong>/</strong> 경로의 끝입니다.  
  
     이러한 위치를 목록의 맨 위로 이동하여 해당 기호가 가장 먼저 로드되도록 합니다.  
  
   > [!NOTE]
   > 이러한 Code Center Premium 위치는 가장 먼저 나열되어야 처음으로 로드되는 위치가 됩니다. Visual Studio 2010에서 위의 모든 서버를 이동할 수 없습니다는 **Microsoft 기호 서버** 항목 확인란의 선택을 취소 해야 하는 이유입니다.  
   > 
   >  디버그 세션 중에 Microsoft 기호에서 기호를 로드하려면 다음을 수행합니다.  
   > 
   > 1. 에 **디버그** 메뉴 선택 **Windows** 를 선택한 후 **모듈**합니다.  
   >    2.  기호를 원하는 모듈을 선택하고 바로 가기 메뉴를 엽니다. 선택할 **에서 기호 로드** 를 선택한 후 **Microsoft 기호 서버**합니다.  
  
10. 에 **이 디렉터리의 기호 서버에서 기호 캐시** 상자와 같은 위치를 입력 합니다 `C:\symbols` Code Center Premium 위치 기호를 캐시할 수 있습니다. 기호를 캐시하면 디버깅 중 성능이 상당히 개선됩니다.  
  
     이 절차를 완료한 후 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]로 소스 코드를 디버깅하는 데 문제가 발생하면 이전에 캐시된 오래된 기호 파일의 캐시 위치를 확인하고, 오래된 기호 파일을 제거합니다.  
  
11. **확인**을 클릭합니다.  
  
12. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]를 다시 시작하여 설정이 저장되도록 합니다.  
  
### <a name="to-debug-your-source-code-using-attach-to-process"></a>프로세스에 연결 기능을 사용하여 소스 코드를 디버깅하려면  
  
1. 스마트 카드 판독기를 연결하고 Shared Source Initiative에서 받은 카드를 삽입합니다.  
  
2. Visual Studio를 실행합니다.  
  
3. Visual Studio 프로젝트를 엽니다.  
  
4. 에 **도구** 메뉴에서 클릭 **프로세스에 연결**합니다.  
  
5. 에 **프로세스에 연결** 대화 상자, 클릭 **선택**합니다.  
  
6. 에 **코드 형식 선택** 대화 상자의 **다음 코드 형식 검색**를 선택 **네이티브**를 **관리 되는**, 및 **(관리 v4.0)** 합니다.  
  
7. 클릭 **확인** 해제 하는 **코드 형식 선택** 대화 상자.  
  
8. 에 **사용 가능한 프로세스** 상자, 디버깅 하려는 프로세스를 선택 합니다.  
  
9. **연결**을 클릭합니다.  
  
10. 인증서 확인 메시지가 표시 되 면 **확인**합니다. 그런 다음 사용자의 PIN을 입력합니다. Code Center Premium의 사용 조건에 동의합니다(필요한 경우).  
  
     네트워크 속도에 따라 다르지만 기호를 다운로드하는 데는 오랜 시간이 걸릴 수 있습니다. 기호가 모두 다운로드되면 상태 표시줄에서 이를 알 수 있습니다.  
  
11. 솔루션의 관리되는 프로젝트 모두에 대해 연결 단계를 반복합니다.  
  
### <a name="to-debug-source-code-from-an-existing-solution"></a>기존 솔루션에서 소스 코드를 디버깅하려면  
  
1. **솔루션 탐색기**선택한를 솔루션에 대 한 바로 가기 메뉴를 열고 **속성**합니다.  
  
2. 솔루션 속성 페이지 대화 상자에서 선택 **소스 파일 디버그** 에 **공용 속성** 노드.  
  
3. 다음 위치에 추가 합니다 **소스 파일이 포함 된 디렉터리** 목록:  
  
    `https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
   > [!NOTE]
   > 후행 슬래시를 포함 해야<strong>/</strong> 경로의 끝입니다.  
  
4. 솔루션의 관리되는 프로젝트 각각에 대해 다음을 수행합니다.  
  
   1. 솔루션 탐색기에서 프로젝트에 대 한 바로 가기 메뉴를 열고 선택한 후 **속성**합니다.  
  
   2. 선택 **디버깅할** 를 선택한 후 **비관리 코드 디버깅 사용**합니다.  
  
### <a name="to-debug-your-solution-with-code-center-premium-source"></a>Code Center Premium 소스로 솔루션을 디버깅하려면  
  
1. `Package` 클래스에서 패키지 생성자에 중단점을 설정합니다.  
  
2. 에 `Debug` 메뉴에서 클릭 **디버깅 시작**합니다.  
  
3. 패키지 생성자의 중단점에 도달 하면로 이동 합니다 **호출 스택** 창을 마우스 오른쪽 단추로 클릭 한 다음에서 기호 로드 하려는 어셈블리의 스택 프레임을 클릭 **기호 로드**합니다.  
  
     소스를 로드할 호출 프레임을 두 번 클릭합니다.  
  
### <a name="to-browse-source-code-on-code-center-premium"></a>Code Center Premium에서 소스 코드를 찾아보려면  
  
1. 스마트 카드 판독기를 연결하고 Shared Source Initiative에서 받은 카드를 삽입합니다.  
  
2. Internet Explorer를 시작하고 URL `https://codepremium.msdn.microsoft.com`을 입력합니다.  
  
3. 원하는 소스를 찾습니다.  
  
## <a name="see-also"></a>참고 항목  
 [디버거 설정 및 준비](../debugger/debugger-settings-and-preparation.md)   
 [디버거 보안](../debugger/debugger-security.md)   
 [Code Center Premium](https://www.microsoft.com/en-us/sharedsource/code-center-premium.aspx)
