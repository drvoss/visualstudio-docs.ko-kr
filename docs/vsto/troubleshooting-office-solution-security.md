---
title: Office 솔루션 보안 문제 해결
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], troubleshooting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 921bef3514b802672296dda6d680b665f1f42482
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978317"
---
# <a name="troubleshoot-office-solution-security"></a>Office 솔루션 보안 문제 해결
  이 항목에서는 Office 솔루션 보안 작업을 수행할 때 발생할 수 있는 일반적인 문제를 해결 하기 위한 팁을 포함 합니다.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trusted-solutions-cannot-be-installed-from-restricted-sites"></a>제한 된 사이트에서 신뢰할 수 있는 솔루션을 설치할 수 없습니다.
 사용자는 웹 사이트를 Internet Explorer 제한 된 사이트 영역에 표시 된 경우 웹 위치에서 솔루션을 설치할 수 없습니다. 이 솔루션은 신뢰할 수 있는 인증서로 서명 하는 경우에 마찬가지입니다.

 배포 매니페스트의 URL 영역 5 중 하나로 분류할 수 있습니다.

- 내 컴퓨터

- 인터넷

- 로컬 인트라넷

- 신뢰할 수 있는 사이트

- 제한 된 사이트

  배포 매니페스트의 위치 제한 된 사이트 영역에 할당 되 면 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 솔루션을 설치 하지 않습니다. 위치 라고 하 고 수 하는 경우 신뢰할 수 있는, 사용자 수 제한 된 사이트 영역에서 위치를 제거 하 고 솔루션을 설치 합니다. 영역을 관리 하는 방법에 대 한 자세한 내용은 [ClickOnce 신뢰할 수 있는 게시자 구성](http://go.microsoft.com/fwlink/?LinkId=94774)합니다.

## <a name="solutions-cannot-be-installed-from-network-file-shares-or-web-locations-when-internet-explorer-enhanced-security-configuration-or-internet-explorer-7-is-installed"></a>Internet Explorer 7 또는 Internet Explorer 보안 강화 구성을 설치 하는 경우 네트워크 파일 공유 또는 웹 위치에서 솔루션을 설치할 수 없습니다.
 Internet Explorer 향상 된 보안 구성 (IEESC) Windows Server 2003 이상 버전에서는 및 Internet Explorer 7 이상 크게 인터넷을 탐색 하는 사용자의 기능을 제한 합니다. 사용자가 설치 하려고 하면 Office 솔루션에서 네트워크 파일 공유 또는 웹 위치에서 다음 오류 메시지가 발생할 수 있습니다. "인증서 사용에 대 한 배포 매니페스트에 서명 하기 때문에이 응용 프로그램에서 사용자 지정된 기능이 작동 하지 것입니다 *SolutionName* 를 신뢰할 수 없습니다. 관리자에 게 문의에 게 문의 합니다. "

 IEESC 및 Internet Explorer 7 이상을 사용 하 여 배포 매니페스트의 URL은 인터넷 영역에서 분류 되며, 매니페스트 신뢰할 수 있는 게시자 인증서가 있어야 합니다. 또는 솔루션을 설치할 수 없습니다. Ieesc, 기본 동작은 신뢰 결정을 내리는 데 최종 사용자에 게 프롬프트입니다.

 IEESC과 Internet Explorer 7의 효과 관리 하 고 이상 웹 사이트 및 범용 명명 규칙 (UNC) 경로 식별 하려면 신뢰 하 고 (로컬 인트라넷 이나 신뢰할 수 있는 사이트)의 신뢰할 수 있는 보안 영역 중 하나에 추가 합니다. 영역을 관리 하는 방법에 대 한 자세한 내용은 [신뢰할 수 있는 게시자 구성 ClickOnce](http://go.microsoft.com/fwlink/?LinkId=94774)합니다.

## <a name="see-also"></a>참고자료
- [Office 솔루션 보안](../vsto/securing-office-solutions.md)
