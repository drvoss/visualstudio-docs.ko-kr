---
title: '방법: 대상 Office 다국어 사용자 인터페이스'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalization [Office development in Visual Studio], user interface targeting
- MUI [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], localization
- Multilingual User Interface [Office development in Visual Studio]
- localization [Office development in Visual Studio], user interface targeting
- Office applications [Office development in Visual Studio], globalization
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c495f8a83b58c53404056befd2227b295c3324d5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62961141"
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>방법: 대상 Office 다국어 사용자 인터페이스
  다국어 사용자 인터페이스 (MUI)에 최종 사용자의 사용자 인터페이스 (UI) 언어를 변경 하는 기능을 제공 하는 Microsoft Office 기능입니다. 예를 들어 스페인어로 영어 UI를 사용 하는 최종 사용자 UI의 언어를 변경할 수 있습니다.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Office의 여러 언어를 사용 하는 사용자가 응용 프로그램을 사용할 경우 자동으로 (사용자가 설치 하 고 올바른 리소스) 하는 경우 사용자의 컴퓨터에 Office가 사용 되는 언어와 일치 하도록 UI 문자열의 언어를 변경 하는 코드를 추가할 수 있습니다.

## <a name="to-check-the-current-office-ui-setting"></a>현재 Office UI 설정을 확인 하려면

1. 사용 된 <xref:System.Threading.Thread.CurrentUICulture%2A> 현재 스레드의 속성입니다. 현재 사용자의 컴퓨터에서 실행 되는 Office 버전에 사용 되는 언어와 일치 하도록 UI 문자열의 언어를 설정 합니다.

     [!code-vb[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#10)]
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#10)]

## <a name="see-also"></a>참고자료
- [방법: 주 interop 어셈블리를 통해 대상 Office 응용 프로그램](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Office 솔루션에서 런타임에 바인딩](../vsto/late-binding-in-office-solutions.md)
