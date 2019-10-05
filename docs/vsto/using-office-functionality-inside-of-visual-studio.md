---
title: Visual Studio 내에서 Office 기능 사용
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], document protection
- Office applications [Office development in Visual Studio]
- Office functionality inside Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c47ed9639a33ecdea3451c63b729d959f6855e5d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62982343"
---
# <a name="use-office-functionality-inside-of-visual-studio"></a>Visual Studio 내에서 Office 기능 사용
  문서 수준 프로젝트를 만들면 문서와 연결된 된 응용 프로그램이 호스팅되는 Visual Studio 내에서 디자인 하 고 문서를 직접 작업할 수 있도록 합니다. Microsoft Office 응용 프로그램 Visual Studio에서 열 경우, 일반적으로 예상 대로 작동 합니다. 그러나 응용 프로그램의 기능 중 일부는 다른 또는 액세스할 수 없습니다.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="document-protection"></a>문서 보호
 Microsoft Office Word 및 Microsoft Office Excel 문서 프로젝트에서 사용할 수 있는 보호 기능을 제공 합니다. 그러나 문서 보호 문서 Visual Studio에서 열려 있는 동안 사용 하는 경우 해당 하지 못할 수 있습니다 일부 디자인 변경 하지 못하도록 합니다. 자세한 내용은 [문서 보호 문서 수준 솔루션의](../vsto/document-protection-in-document-level-solutions.md)합니다.

## <a name="information-rights-management"></a>정보 권한 관리
 정보 권한 관리 (IRM)는 Microsoft Office Word 및 Microsoft Office Excel에서 사용할 수 있습니다. IRM 보거나 중요 한 정보를 변경할 권한이 없는 사람이 방지할 수 있습니다. 그러나 IRM은 실행에서 코드를 방해할 수 있습니다. 자세한 내용은 [정보 권한 관리 및 관리 코드 확장명 개요](../vsto/information-rights-management-and-managed-code-extensions-overview.md)합니다.

## <a name="password-protection"></a>암호 보호
 Microsoft Office Word 문서 및 Microsoft Office Excel 통합 문서 암호를 알지 못합니다 사람이 열 수 없습니다 있도록 설정할 수 있습니다. 암호 보호 Word 및 Excel에서 다르게 처리 하며 개발 프로세스에 영향을 줄 수 있습니다. 자세한 내용은 [Office 문서의 암호 보호](../vsto/password-protection-on-office-documents.md)합니다.

## <a name="see-also"></a>참고자료
- [문서 수준 솔루션의 문서 보호](../vsto/document-protection-in-document-level-solutions.md)
- [정보 권한 관리 및 관리 코드 확장명 개요](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Office 문서의 암호 보호](../vsto/password-protection-on-office-documents.md)
- [방법: 코드를 실행 하지 않고 Office 솔루션 열기](../vsto/how-to-open-office-solutions-without-running-code.md)
