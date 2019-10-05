---
title: '방법: 코드를 실행 하지 않고 Office 솔루션 열기'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], opening
- opening Office solutions
- bypassing assemblies
- solutions [Office development in Visual Studio], opening
- assemblies [Office development in Visual Studio], bypassing
- Office documents [Office development in Visual Studio, opening without running code
- documents [Office development in Visual Studio], opening without running code
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 366416e4f18435bd01391657eb2fc4f65f8a4d62
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441776"
---
# <a name="how-to-open-office-solutions-without-running-code"></a>방법: 코드를 실행 하지 않고 Office 솔루션 열기
  관리 코드 확장을 사용 하 여 만든 Microsoft Office 솔루션에는 최종 사용자의 Office 응용 프로그램의 보안 설정이 높은를 설정한 경우에 실행 됩니다. Microsoft Office가 아니라 Microsoft.NET Framework에서.NET 어셈블리 코드 보안을 관리 하는 때문입니다.

 그러나 코드를 실행 하지 않고 문서를 열려면 하려는 경우 경우가 있습니다. 예를 들어 문서를 열 때 실행 되는 코드의 내용을 변경 될 수 있습니다 하지만 모양을 문서 코드 변경 되기 전에를 업데이트 하려면. 또는 다른 사람에 특정 정보를 사용 하 여 문서를 송신 하려는 및 코드를 실행 하 고 가능한 경우 콘텐츠를 변경 하지 않으려면입니다.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 문서 또는 어셈블리 코드를 실행 하지 않고 관리 코드 확장을 포함 하는 통합 문서를 여는 방법은 여러 가지가 있습니다.

## <a name="to-bypass-the-assembly-by-using-the-shift-key"></a>Shift 키를 사용 하 여 어셈블리를 무시 하려면

- 문서 및에서 통합 문서를 열면를 **파일** 메뉴를 누른 채 합니다 **Shift** Word 및 Excel 문서를 여는 동안 초기화 이벤트를 발생 하지 않도록 키를 합니다.

    > [!NOTE]
    > 문서 또는 통합 문서를 열면 합니다 **Getting Started** 작업창을 누른 **Shift** 코드가 무시 되지 않습니다. 또한 키를 누른 채 해도 이벤트 문서를 연 후 발생 합니다.

     이 메서드는 코드를 실행 하 고 문서를 먼저 변경 하지 않고 변경할 수 있도록 문서를 열려고 할 경우에 유용 합니다.

## <a name="to-bypass-an-assembly-by-renaming-or-removing-it"></a>이름 바꾸기 또는 제거 하 여 어셈블리를 무시 하려면

- 어셈블리가 있는 컴퓨터에 필요한 권한이 있는 경우에 이름을 바꿀 수도 있고 문서 또는 통합 문서를 찾을 수 없습니다 있도록 어셈블리를 제거할 수 있습니다. 이 Office 문서를 열 때마다 발생 하는 오류가 발생 합니다.

     솔루션을 여러 사용자가 사용 하는 경우이 메서드는 실행 모두에 대 한 솔루션을 방지 합니다. 이 기능은 코드 또는 참조 된 서버에서 문제가 발견 되 고 모든 사용자가 해당 실행을 중지 하려는 경우에 유용할 수 있습니다.

## <a name="see-also"></a>참고자료
- [Office 솔루션 보안](../vsto/securing-office-solutions.md)
- [Office 솔루션 배포](../vsto/deploying-an-office-solution.md)
- [Office 솔루션을 만들고 디자인](../vsto/designing-and-creating-office-solutions.md)
- [Office 솔루션에서 응용 프로그램 및 배포 매니페스트](../vsto/application-and-deployment-manifests-in-office-solutions.md)
