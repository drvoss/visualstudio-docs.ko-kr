---
title: 안전한 배포
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio], security
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- ClickOnce deployment [Office development in Visual Studio], security
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1000504ad83706bd028af4bd668da7483e478b7a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978378"
---
# <a name="secure-deployment"></a>안전한 배포
  Office 솔루션을 만들 때 개발 컴퓨터를 실행 하도록 프로젝트에서 코드를 허용 하도록 자동으로 업데이트 됩니다. 그러나 솔루션을 배포할 때 인증서를 사용 하 여 솔루션을 서명 하거나 사용 하 여 신뢰 결정의 기준이 되는 증명 정보 제공 해야 합니다는 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 신뢰 프롬프트 키입니다. 자세한 내용은 [Office 솔루션에 신뢰를 부여](../vsto/granting-trust-to-office-solutions.md)합니다.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 문서 수준 사용자 지정 네트워크 위치에 문서를 배포 하는 경우 추가 해야 합니다도 문서 위치 Office 응용 프로그램의 보안 센터에서 신뢰할 수 있는 위치 목록에 있습니다. 최종 사용자 컴퓨터에서 문서 사용 권한을 설정 하는 방법에 대 한 자세한 내용은 참조 하세요. [문서에 신뢰 부여](../vsto/granting-trust-to-documents.md)합니다.

## <a name="prevent-office-solutions-from-running-code"></a>Office 솔루션에서 코드 실행 방지
 관리자는 레지스트리를 사용 하 여 Office 솔루션을 모든 컴퓨터에서 실행 하지 못하도록 수 있습니다. 관리 코드 확장이 있는 Office 솔루션 열릴 때, Visual Studio Tools for Office 런타임 검사에 항목이 있는지 여부를 이름의 `Disabled` 컴퓨터에서 다음 레지스트리 키 중 하나에 존재 합니다.

- **HKEY_CURRENT_USER\Software\Microsoft\VSTO**

- **HKEY_LOCAL_MACHINE\Software\Microsoft\VSTO**

  Office 솔루션 코드 실행을 방지 하려면 만들기를 `Disabled` 하나 또는 둘 다 이러한 레지스트리 키 항목 다음 데이터 형식 및 값 중 하나를 지정 하 고 `Disabled`:

- REG_SZ 또는 REG_EXPAND_SZ "0" (영) 이외의 문자열로 설정 된 경우.

- 0 (영) 이외의 값으로 설정 된 REG_DWORD입니다.

  코드를 실행 하는 Office 솔루션을 사용 하려면 둘 다를 설정 합니다 `Disabled` 항목 0 (영)을 하거나 레지스트리 항목을 삭제 합니다.

## <a name="see-also"></a>참고자료
- [Office 솔루션 배포](../vsto/deploying-an-office-solution.md)
- [실행 하거나 Office 솔루션을 호스트 하는 컴퓨터 준비](https://msdn.microsoft.com/be1b173f-7261-4d74-aa4e-94ccd43db8d8)
- [Office 솔루션 보안](../vsto/securing-office-solutions.md)
