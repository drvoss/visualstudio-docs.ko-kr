---
title: Office 문서에서 데이터 원본을 프로그래밍 방식으로 캐시
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
ms.openlocfilehash: 5e63b478fb16965f639a76dad0cbc3b2715bc7e2
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401409"
---
# <a name="how-to-programmatically-cache-a-data-source-in-an-office-document"></a>방법: Office 문서에서 데이터 원본을 프로그래밍 방식으로 캐시
  호출 하 여 문서의 데이터 캐시에 데이터 개체를 프로그래밍 방식으로 추가할 수 있습니다는 `StartCaching` 와 같은 호스트의 메서드 항목을 <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook>, 또는 <xref:Microsoft.Office.Tools.Excel.Worksheet>합니다. 데이터 개체를 호출 하 여 데이터 캐시에서 제거 된 `StopCaching` 메서드 호스트 항목의 합니다.

 합니다 `StartCaching` 메서드 및 `StopCaching` 메서드 둘 다 개인 되지만 IntelliSense에 나타납니다.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 사용 하는 경우는 `StartCaching` 데이터 캐시를 데이터 개체에 데이터 개체를 추가 하는 방법으로 선언할 필요가 없습니다를 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 특성입니다. 그러나 데이터 개체에는 데이터 캐시에 추가할 특정 요구 사항을 충족 해야 합니다. 자세한 내용은 [데이터 캐시](../vsto/caching-data.md)합니다.

## <a name="to-programmatically-cache-a-data-object"></a>프로그래밍 방식으로 데이터 개체를 캐시 하려면

1. 메서드는 포함 되지 않은 클래스 수준에서 데이터 개체를 선언 합니다. 이 예에서는 가정 선언 하는 한 <xref:System.Data.DataSet> 라는 `dataSet1` 프로그래밍 방식으로 캐시 하려는 합니다.

     [!code-csharp[Trin_VstcoreDataExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#12)]
     [!code-vb[Trin_VstcoreDataExcel#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#12)]

2. 데이터 개체를 인스턴스화하고 호출을 `StartCaching` 메서드 문서 또는 워크시트 인스턴스 및 데이터 개체의 이름을 전달 합니다.

     [!code-csharp[Trin_VstcoreDataExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#13)]
     [!code-vb[Trin_VstcoreDataExcel#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#13)]

## <a name="to-stop-caching-a-data-object"></a>데이터 개체를 캐시를 중지 하려면

1. 호출 된 `StopCaching` 메서드 문서 또는 워크시트 인스턴스 및 데이터 개체의 이름을 전달 합니다. 이 예에서는 있다고 가정를 <xref:System.Data.DataSet> 라는 `dataSet1` 캐싱을 중지 하려는 합니다.

     [!code-csharp[Trin_VstcoreDataExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#14)]
     [!code-vb[Trin_VstcoreDataExcel#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#14)]

    > [!NOTE]
    > 호출 하지 마세요 `StopCaching` 에 대 한 이벤트 처리기에서는 `Shutdown` 문서 또는 워크시트의 이벤트입니다. 시간을 `Shutdown` 이벤트가 발생 하면 너무 늦게 데이터 캐시를 수정 하는 것입니다. 에 대 한 자세한 내용은 합니다 `Shutdown` 이벤트를 참조 하세요 [Events in Office Projects](../vsto/events-in-office-projects.md)합니다.

## <a name="see-also"></a>참고자료

- [데이터 캐시](../vsto/caching-data.md)
- [방법: 오프 라인 이나 서버에서 사용 하기 위해 데이터 캐시](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [방법: 암호로 보호 된 문서의 데이터 캐시](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [서버에 있는 문서의 데이터에 액세스](../vsto/accessing-data-in-documents-on-the-server.md)
- [데이터를 저장 합니다.](../data-tools/saving-data.md)
