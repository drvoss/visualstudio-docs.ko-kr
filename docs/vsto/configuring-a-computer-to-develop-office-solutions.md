---
title: Office 솔루션을 개발 하도록 컴퓨터를 구성 합니다.
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, installing tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e559ddfec8570077a78fe980632366b4a57605de
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62930960"
---
# <a name="configure-a-computer-to-develop-office-solutions"></a>Office 솔루션을 개발 하도록 컴퓨터를 구성 합니다.

Microsoft Office용 VSTO 추가 기능 및 사용자 지정을 만들려면 지원되는 버전의 Visual Studio, .NET Framework 및 Microsoft Office를 설치합니다.

|소프트웨어|지원되는 버전|
|--------------|------------------------|
|Visual Studio 2017| 사용 하 여 모든 버전의 **Office/SharePoint 개발** 워크 로드.|
|.NET Framework|-.NET Framework 4 이상|
|Microsoft Office|<ul><li>Office Professional Plus for Office 365를 비롯한 Office의 모든 제품군 버전</li><li>다음의 독립 실행형 애플리케이션<br /><br /> <ul><li>Excel</li><li>InfoPath(Office 2013 및 Office 2010에만 해당)</li><li>Outlook</li><li>PowerPoint</li><li>프로젝트</li><li>Visio</li><li>Word</li></ul></li></ul><br /> Office의 일부분으로 VBA(Visual Basic for Applications)를 설치해야 합니다. **중요:** 간편 실행 버전의 Office 2010 응용 프로그램은 지원되지 않습니다.|

자세한 설치 단계를 참조 하세요. [방법: Office 솔루션을 개발 하도록 컴퓨터를 구성](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)합니다.

## <a name="if-project-templates-dont-appear-or-they-dont-work-in-visual-studio"></a>프로젝트 템플릿이 표시 되지 않거나 Visual Studio에서 작동 하지 않는 경우

지원 되는 버전의 Visual Studio,.NET Framework 및 Microsoft Office 설치 했는데 Office 프로젝트 템플릿 중 하나에 나타나지 Visual Studio **새 프로젝트** 하거나 대화 상자에서 하나를 사용 하려고 할 때 오류가 표시 다음을 확인 합니다.

- 컴퓨터에 Microsoft Office 개발자 도구를 설치했는지 확인합니다.

     Office 개발자 도구, Visual Studio의 선택적 구성 요소는 Visual Studio와 함께 자동으로 설치 됩니다. 설치할 기능을 지정하여 Visual Studio 설치를 사용자 지정하는 경우 설치 중에 **Microsoft Office 개발자 도구** 를 선택하여 도구를 설치해야 합니다.

     이러한 도구가 설치 되어 있는지, Visual Studio 설치 프로그램을 시작 하 고 선택 합니다 **수정** 단추입니다. **Microsoft Office 개발자 도구** 확인란을 선택하고 **업데이트** 단추를 선택합니다.

- 간편 실행 방식으로 제공 되는 office 버전을 실행 하지는 확인 합니다. [방법: Outlook이 컴퓨터에 응용 프로그램을 실행 하려면 클릭 여부를 확인](/previous-versions/office/developer/office-2010/ff864733(v=office.14))합니다.

- Microsoft Office의 버전을 하나만 실행 중인지 확인 합니다.

참조를 계속 문제가 발생 하는 경우 [Office 솔루션 오류에에서 대 한 추가 지원은](../vsto/additional-support-for-errors-in-office-solutions.md)합니다.

## <a name="see-also"></a>참고 항목
- [시작 &#40;Visual Studio에서 Office 개발&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [방법: Office 솔루션을 개발 하도록 컴퓨터를 구성 합니다.](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [방법: Visual Studio Tools for Office 런타임 재배포 가능 패키지 설치](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [방법: Office 주 interop 어셈블리 설치](../vsto/how-to-install-office-primary-interop-assemblies.md)
- [Office 응용 프로그램 및 프로젝트 형식으로 사용할 수 있는 기능](../vsto/features-available-by-office-application-and-project-type.md)