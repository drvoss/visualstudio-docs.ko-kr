---
title: Office 문서의 암호 보호
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- passwords [Office development in Visual Studio], document protections
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e3c9521389ce348a482f35ec95c9766edea49f5f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977902"
---
# <a name="password-protection-on-office-documents"></a>Office 문서의 암호 보호
  암호를 알지 못합니다 사람이 열 수 없습니다 있도록 Microsoft Office Word 문서 및 Microsoft Office Excel 통합 문서에는 암호를 설정 하는 것이 가능 합니다. 이 옵션 이라고 **파일을 열 때 암호**합니다.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 기존 문서 및 있는 통합 문서를 사용 하 여 문서 수준 프로젝트를 만들 수 있습니다 **파일을 열 때 암호** 사용 하도록 설정 합니다. Visual Studio에서 동작은 있는 Word 및 Excel 문서에 대 한 다른 **파일을 열 때 암호** 사용 하도록 설정 합니다.

 사용 하도록 설정 하는 방법은 **열기 암호**, Word 또는 Excel의 도움말을 참조 합니다.

## <a name="behavior-of-excel-and-word"></a>Excel 및 Word의 동작
 Visual Studio에서 Excel 통합 문서를 열 때마다 **파일을 열 때 암호** 사용 Excel 암호를 묻는 있습니다. 솔루션을 빌드할 때 묻는 암호를 다시 빌드하는 동안 문서 열려 있기 때문에.

 Visual Studio에서 Word 문서를 열고 처음 **열기 암호** 활성화 저장할지 확인 암호. 성공적으로 암호를 입력 한 후 **파일을 열 때 암호** 문서에서 제거 됩니다 하 고 문서를 열어 암호를 더 이상 필요 합니다. 솔루션의 문서를 사용 하려는 경우 되기 전에 암호를 요구 하도록 열 수, 사용 하도록 설정 해야 **파일을 열 때 암호** 마지막 빌드 후 솔루션을 배포 하기 전에 합니다.

## <a name="see-also"></a>참고자료
- [문서 수준 솔루션의 문서 보호](../vsto/document-protection-in-document-level-solutions.md)
- [정보 권한 관리 및 관리 코드 확장명 개요](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [방법: 제한 된 권한으로 문서 뒤에서 실행 하는 코드를 허용 합니다.](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [Office 솔루션을 만들고 디자인](../vsto/designing-and-creating-office-solutions.md)
