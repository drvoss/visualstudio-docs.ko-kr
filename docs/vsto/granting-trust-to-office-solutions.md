---
title: Office 솔루션에 신뢰를 부여
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cf7a68d5d3567305e4f70049d76a1c260ddecf25
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62826936"
---
# <a name="grant-trust-to-office-solutions"></a>Office 솔루션에 신뢰를 부여
  Office 솔루션으로 각 대상 컴퓨터의 보안 정책을 수정 신뢰 솔루션 어셈블리, 응용 프로그램 매니페스트, 배포 매니페스트 및 문서에 신뢰를 부여 합니다. 또는 최종 사용자 Office 솔루션에 신뢰를 부여할 수 있습니다.

 응용 프로그램 및 배포 매니페스트에 서명 하 여 Office 솔루션에 대 한 완전 신뢰를 부여할 수 있습니다.

 최종 사용자의 신뢰 여부를 결정 하 여 Office 솔루션에 신뢰를 부여할 수는 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 신뢰 프롬프트.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="Signing"></a> 응용 프로그램 및 배포 매니페스트에 서명 하 여 솔루션 신뢰
 모든 응용 프로그램 및 배포 매니페스트 Office 솔루션 게시자를 식별 하는 인증서를 사용 하 여 서명 해야 합니다. 인증서 신뢰를 결정 하는 것에 대 한 기초를 제공 합니다.

 임시 인증서를 만들어지고 디버깅 하는 동안 솔루션이 실행 되므로 빌드 시간에 신뢰를 부여 합니다. 임시 인증서로 서명 된 솔루션을 게시 하는 경우 신뢰 결정을 내리는 데 최종 사용자 라는 메시지가 표시 됩니다.

 알려져 있고 신뢰할 수 있는 인증서를 사용 하 여 솔루션에 서명 하는 경우 솔루션 신뢰 결정을 내리는 데 최종 사용자에 게 묻지 않고 자동으로 설치 됩니다. 서명 인증서를 얻는 방법에 대 한 자세한 내용은 참조 하세요. [ClickOnce 및 Authenticode](../deployment/clickonce-and-authenticode.md)합니다. 인증서를 얻어 인증서를 신뢰할 수 있는 게시자 목록에 추가 하 여 명시적으로 신뢰 되어야 합니다. 자세한 내용은 [방법: ClickOnce 응용 프로그램에 대 한 클라이언트 컴퓨터에 신뢰할 수 있는 게시자 추가](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)합니다.

 개발자가 임시 인증서를 사용 하 여 솔루션에 로그인 할 경우 관리자로 다시 서명할 수는 알려져 있고 신뢰할 수 있는 인증서를 사용 하 여 사용자 지정 매니페스트 생성 및 편집 도구를 사용 하 여 (*mage.exe*), 중 하나인 합니다 Microsoft.NET Framework 도구입니다. 솔루션을 서명 하는 방법에 대 한 자세한 내용은 참조 하세요. [방법: Office 솔루션에 서명](../vsto/how-to-sign-office-solutions.md) 고 [방법: 애플리케이션 및 배포 매니페스트 서명](../ide/how-to-sign-application-and-deployment-manifests.md)을 참조하세요.

## <a name="TrustPrompt"></a>ClickOnce 신뢰 프롬프트를 사용 하 여 솔루션 신뢰
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 솔루션의 인증서를 신뢰 하는 조직 전체의 정책이 없는 경우 신뢰 결정을 내리는 데 최종 사용자 라는 메시지가 표시 됩니다. 최종 사용자가 솔루션에 신뢰를 부여 하는 경우이 신뢰 결정을 저장 하는 URL 및 공개 키를 포함 하는 포함 목록 항목이 생성 됩니다. 신뢰할 수 있는 사용자 지정을 실행할 때 나중에 최종 사용자에 게 다시 묻지 않습니다.

 관리자가 사용 하지 않도록 설정할 수는 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 신뢰 프롬프트 또는 Authenticode 인증서로 서명 된 솔루션에 대해서만 발생 하도록 해야 합니다. MyComputer, LocalIntranet, 인터넷, TrustedSites, 및 UntrustedSites 영역에 대 한 이러한 설정을 변경 하는 방법에 대 한 자세한 내용은 참조 하세요. [방법: ClickOnce 신뢰 프롬프트 동작 구성](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)을 참조하세요.

## <a name="see-also"></a>참고자료

- [Office 솔루션 보안](../vsto/securing-office-solutions.md)
- [문서에 신뢰를 부여](../vsto/granting-trust-to-documents.md)
- [Office 솔루션 보안 문제 해결](../vsto/troubleshooting-office-solution-security.md)
- [Office 솔루션에 대 한 특정 보안 고려 사항](../vsto/specific-security-considerations-for-office-solutions.md)