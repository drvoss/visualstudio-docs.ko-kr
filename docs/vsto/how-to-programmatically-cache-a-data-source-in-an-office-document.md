---
title: Office 문서의 데이터 소스를 프로그래밍 방식으로 캐시
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- StartCaching method
- data caching [Office development in Visual Studio], programmatically
- data [Office development in Visual Studio], caching
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 241ce42c2d411fdaf611f3a7f2b52eb40c8c32a2
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189586"
---
# <a name="how-to-programmatically-cache-a-data-source-in-an-office-document"></a>방법: Office 문서에서 프로그래밍 방식으로 데이터 소스 캐시
  <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook>또는 <xref:Microsoft.Office.Tools.Excel.Worksheet>와 같은 호스트 항목의 `StartCaching` 메서드를 호출 하 여 문서의 데이터 캐시에 데이터 개체를 프로그래밍 방식으로 추가할 수 있습니다. 호스트 항목의 `StopCaching` 메서드를 호출 하 여 데이터 캐시에서 데이터 개체를 제거 합니다.

 `StartCaching` 메서드와 `StopCaching` 메서드는 모두 private 이지만 IntelliSense에 표시 됩니다.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 `StartCaching` 메서드를 사용 하 여 데이터 개체를 데이터 캐시에 추가 하는 경우에는 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 특성을 사용 하 여 데이터 개체를 선언할 필요가 없습니다. 그러나 데이터 개체는 데이터 캐시에 추가 해야 하는 특정 요구 사항을 충족 해야 합니다. 자세한 내용은 [데이터 캐시](../vsto/caching-data.md)를 참조 하세요.

## <a name="to-programmatically-cache-a-data-object"></a>데이터 개체를 프로그래밍 방식으로 캐시 하려면

1. 메서드 내부가 아닌 클래스 수준에서 데이터 개체를 선언 합니다. 이 예제에서는 프로그래밍 방식으로 캐시 하려는 `dataSet1` 이라는 <xref:System.Data.DataSet>를 선언 하는 것으로 가정 합니다.

     [!code-csharp[Trin_VstcoreDataExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#12)]
     [!code-vb[Trin_VstcoreDataExcel#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#12)]

2. 데이터 개체를 인스턴스화한 다음 문서 또는 워크시트 인스턴스의 `StartCaching` 메서드를 호출 하 고 데이터 개체의 이름을 전달 합니다.

     [!code-csharp[Trin_VstcoreDataExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#13)]
     [!code-vb[Trin_VstcoreDataExcel#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#13)]

## <a name="to-stop-caching-a-data-object"></a>데이터 개체 캐싱을 중지 하려면

1. 문서 또는 워크시트 인스턴스의 `StopCaching` 메서드를 호출 하 고 데이터 개체의 이름을 전달 합니다. 이 예에서는 캐싱을 중지 하려는 `dataSet1` 라는 <xref:System.Data.DataSet> 있다고 가정 합니다.

     [!code-csharp[Trin_VstcoreDataExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#14)]
     [!code-vb[Trin_VstcoreDataExcel#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#14)]

    > [!NOTE]
    > 문서 또는 워크시트의 `Shutdown` 이벤트에 대 한 이벤트 처리기에서 `StopCaching`를 호출 하지 마세요. `Shutdown` 이벤트가 발생 하는 시점에는 너무 늦게 데이터 캐시를 수정할 수 있습니다. `Shutdown` 이벤트에 대 한 자세한 내용은 [Office 프로젝트의 이벤트](../vsto/events-in-office-projects.md)를 참조 하세요.

## <a name="see-also"></a>참조

- [데이터 캐시](../vsto/caching-data.md)
- [방법: 오프 라인 이나 서버에서 사용할 데이터 캐시](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [방법: 암호로 보호 된 문서의 데이터 캐시](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [서버에 있는 문서의 데이터 액세스](../vsto/accessing-data-in-documents-on-the-server.md)
- [데이터 저장](../data-tools/save-data-back-to-the-database.md)
