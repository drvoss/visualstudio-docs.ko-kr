---
title: 프로세스에 연결할 수 없습니다. | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.remote.unable2attach
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 0468de6c-3ff1-4979-a8c6-8afb53f37547
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0075050b6d24b63ed8380644ad9ec50dd4aa8ec
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737663"
---
# <a name="unable-to-attach-to-the-process"></a>프로세스에 연결할 수 없습니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

프로세스에 연결할 수 없습니다. 서버의 디버거 구성 요소를 이 컴퓨터에 연결할 수 없습니다.  
  
 이 오류가 발생하는 두 가지 일반적인 시나리오가 있습니다.  
  
 **시나리오 1:** 컴퓨터는 Windows XP를 실행 합니다. B 컴퓨터에는 Windows Server 2003이 실행되고 있습니다. B 컴퓨터의 레지스트리에는 다음 DWORD 값이 있습니다.  
  
 `HKLM\Software\Microsoft\MachineDebugManager\AllowLaunchAsOtherUser=1`  
  
 사용자 1이 B 컴퓨터에서 터미널 서버 세션(세션 1)을 시작하고 이 세션에서 관리되는 응용 프로그램을 시작합니다.  
  
 두 컴퓨터의 관리자 인 사용자 2는 컴퓨터 A에 로그온 여기에서 자신이 하려고 B 컴퓨터의 세션 1에서에서 실행 중인 응용 프로그램에 연결  
  
 **시나리오 2:** 두 컴퓨터 모두에서 동일한 암호를 사용 하 여 하나의 사용자 두 컴퓨터 A와 B가 동일한 작업 그룹에 기록 됩니다. 컴퓨터 A에서 실행 하면 디버거는 있으며 B 컴퓨터 A에서 실행 되는 관리 되는 응용 프로그램에 연결 하려고 **네트워크 액세스: 로컬 계정에 대 한 공유 및 보안 모델** 로 설정 **게스트**합니다.  
  
### <a name="to-solve-scenario-1"></a>시나리오 1을 해결하려면  
  
-   디버거와 관리되는 응용 프로그램을 같은 사용자 계정 이름과 암호로 실행합니다.  
  
### <a name="to-solve-scenario-2"></a>시나리오 2를 해결 하려면  
  
1.  **시작** 메뉴 선택 **제어판**합니다.  
  
2.  제어판에서 두 번 클릭 **관리 도구**합니다.  
  
3.  관리 도구 창에서 두 번 클릭 **로컬 보안 정책**합니다.  
  
4.  로컬 보안 정책 창에서 선택 **로컬 정책**합니다.  
  
5.  에 **정책을** 열을 두 번 클릭 **네트워크 액세스: 로컬 계정에 대 한 공유 및 보안 모델**합니다.  
  
6.  에 **네트워크 액세스: 로컬 계정에 대 한 공유 및 보안 모델** 대화 상자에서 로컬 보안 설정을 변경 **클래식**, 클릭 **확인**.  
  
    > [!CAUTION]
    >  보안 모델을 기본으로 변경하면 원치 않는 사용자가 공유 파일 및 DCOM 구성 요소에 액세스할 수 있습니다. 이와 같이 변경하면 원격 사용자가 Guest가 아닌 로컬 사용자 계정을 사용하여 인증할 수 있습니다. 원격 사용자가 로컬 사용자 이름 및 암호를 맞추면 공유하도록 설정한 모든 폴더나 DCOM 개체에 원격 사용자가 액세스할 수 있습니다. 이러한 보안 모델을 사용하는 경우에는 컴퓨터의 모든 사용자 계정이 강력한 암호를 사용하도록 하거나, 디버깅하는 컴퓨터와 디버깅되는 컴퓨터에 대해 격리된 네트워크 아일랜드를 설정하여 무단 액세스를 방지해야 합니다.  
  
7.  모든 창을 닫습니다.  
  
## <a name="see-also"></a>참고 항목  
 [디버거 설정 및 준비](../debugger/debugger-settings-and-preparation.md)



