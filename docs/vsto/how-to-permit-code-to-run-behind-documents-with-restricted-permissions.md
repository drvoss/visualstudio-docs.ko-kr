---
title: 제한 된 권한으로 문서 뒤에서 실행 하는 코드를 허용 합니다.
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Information Rights Management [Office development in Visual Studio]
- permissions [Office development in Visual Studio]
- IRM [Office development in Visual Studio]
- code [Office development in Visual Studio], running behind restricted documents
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 32e42954958fda71d54c3c0ac2685928644e7461
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402254"
---
# <a name="how-to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>방법: 제한 된 권한으로 문서 뒤에서 실행 하는 코드를 허용 합니다.
  문서 또는 통합 문서에 사용 권한을 제한 하도록 Microsoft Office의 정보 권한 관리 (IRM) 기능을 사용할 수 있습니다. 기본적으로 제한 된 Microsoft Office Word 문서 또는 Microsoft Office Excel 통합 문서 코드 실행 허용 되지 않습니다. 솔루션이 작동 하 고 관리 코드 확장 개체 모델에 액세스할 수 있도록 기본값을 변경할 수 있습니다.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 문서 또는 통합 문서의 작성자 이거나 사용 권한 설정을 변경할 수에 대 한 전체 제어 권한이 있어야 합니다.

## <a name="to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>제한 된 권한으로 문서 뒤에서 실행 하는 코드를 허용 하려면

1. Word 또는 Excel에서 문서 또는 통합 문서를 엽니다.

2. 클릭 합니다 **파일** 탭을 가리킵니다 **준비**를 가리킨 **권한 제한**, 클릭 하 고 **제한 된 액세스**합니다.

   > [!NOTE]
   > 처음 사용할 때 Windows Rights Management 클라이언트를 설치 하 라는 메시지가 표시 됩니다. 클라이언트를 설치한 후 단계를 반복 해야 할 수 있습니다.

3. 에 **사용 권한** 대화 상자에서 **이 문서에 대 한 사용 권한을 제한**를 클릭 하 고 **기타 옵션**.

4. 아래 **사용자에 대 한 추가 사용 권한**를 선택 **콘텐츠를 프로그래밍 방식으로 액세스**합니다.

   Word 또는 Excel 개체 모델에 프로그래밍 방식 액세스를 허용 합니다.

## <a name="see-also"></a>참고자료
- [정보 권한 관리 및 관리 코드 확장명 개요](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [문서 수준 솔루션의 문서 보호](../vsto/document-protection-in-document-level-solutions.md)
- [Office 문서의 암호 보호](../vsto/password-protection-on-office-documents.md)
- [Office 솔루션을 만들고 디자인](../vsto/designing-and-creating-office-solutions.md)
- [Office 솔루션 보안](../vsto/securing-office-solutions.md)
- [Office 솔루션 배포](../vsto/deploying-an-office-solution.md)
