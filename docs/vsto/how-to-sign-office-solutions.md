---
title: '방법: Office 솔루션에 서명'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- certificates [Office development in Visual Studio], Office solutions
- security [Office development in Visual Studio], signing Office solutions
- signing manifests [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1fff7555c17f4fdac43de2690f8e133cc32881db
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62971123"
---
# <a name="how-to-sign-office-solutions"></a>방법: Office 솔루션에 서명
  솔루션에 서명 하는 경우에 증거로 인증서를 사용 하 여 솔루션에 신뢰를 부여할 수 있습니다. 여러 솔루션에 대 한 동일한 인증서를 사용할 수 있습니다 하 고 추가 보안 정책 업데이트를 사용 하 여 모든 솔루션 신뢰할 수 있는 됩니다.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 매니페스트 생성 및 편집 도구를 사용 하 여 배포 매니페스트 및 응용 프로그램을 수동으로 편집 하는 경우 (*mage.exe* 하 고 *mageui.exe*)를 사용 하기 전에 매니페스트를 다시 서명 해야 합니다. 자세한 내용은 [방법: 애플리케이션 및 배포 매니페스트 다시 서명](../deployment/how-to-re-sign-application-and-deployment-manifests.md)을 참조하세요.

## <a name="sign-by-using-a-certificate"></a>인증서를 사용 하 여 로그인
 인증서는 고유 키 및 솔루션 게시자의 id를 포함 하는 파일. 인증 기관에서 인증서를 구입 하 고 또는 사용자 고유의 인증서를 만들 하 고, 서명 인증서 기관이 수 있습니다.

 Visual Studio 디버깅을 사용 하려면 임시 인증서를 사용 하 여 Office 솔루션에 서명 합니다. 증명 정보로 배포 된 솔루션에서 임시 인증서를 사용할 해야 있습니다.

### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>인증서를 사용 하 여 Office 솔루션을 로그인

1. 에 **프로젝트** 메뉴에서 클릭 _SolutionName_**속성**합니다.

2. **시그니처** 탭을 클릭합니다.

3. 선택 **ClickOnce 매니페스트 서명**합니다.

4. 클릭 하 여 인증서를 찾습니다 **저장소에서 선택** 또는 **파일에서 선택** 을 인증서로 이동 합니다.

5. 올바른 인증서 사용 되 고 있는지를 확인 하려면 클릭 **자세히** 인증서 정보를 볼 수 있습니다.

## <a name="see-also"></a>참고자료

- [Office 솔루션 보안](../vsto/securing-office-solutions.md)
- [Office 솔루션에 신뢰를 부여](../vsto/granting-trust-to-office-solutions.md)
- [프로젝트 디자이너, 서명 페이지](../ide/reference/signing-page-project-designer.md)
