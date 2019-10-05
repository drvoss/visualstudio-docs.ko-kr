---
title: Office 솔루션에 대 한 구성 정보 설정
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], configuration files
- configuration files [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c477068b3aee3325acae0887e11da908d6c33a85
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328895"
---
# <a name="how-to-set-up-configuration-information-for-an-office-solution"></a>방법: Office 솔루션에 대 한 구성 정보 설정
  Office 솔루션에 관련 된 설정을 구성 하려면 구성 파일을 사용할 수 있습니다. 어셈블리 바인딩 정책, 원격 개체, 디버그 및 추적 설정이 같은 설정을 지정할 수 있습니다.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-a-configuration-file-to-your-office-project"></a>Office 프로젝트에 구성 파일을 추가 하려면

1. **프로젝트** 메뉴에서 **새 항목 추가**를 클릭합니다.

2. 에 **범주** 창 클릭 **일반**합니다.

3. 에 **템플릿을** 창 **응용 프로그램 구성 파일**합니다.

4. 에 **이름을** 상자 확장 어셈블리와 동일한 이름을 입력 합니다 *.config*합니다. Excel 프로젝트 어셈블리에 대 한 구성 파일을 호출 하는 예를 들어 *ExcelWorkbook1.dll* 이름은 *ExcelWorkbook1.dll.config*합니다.

5. **추가**를 클릭합니다.

6. 응용 프로그램 구성 파일 스키마에 따라 구성 파일을 만듭니다. 자세한 내용은 [.NET Framework의 구성 파일 스키마](/dotnet/framework/configure-apps/file-schema/index)합니다.

   구성 파일을 사용 하 여 Office 프로젝트를 사용 하는 것에 대 한 없는 특별 한 고려 사항이 있습니다.

## <a name="see-also"></a>참고자료
- [.NET Framework의 구성 파일 스키마](/dotnet/framework/configure-apps/file-schema/index)
- [Office 솔루션을 만들고 디자인](../vsto/designing-and-creating-office-solutions.md)
- [Office 솔루션 배포](../vsto/deploying-an-office-solution.md)
