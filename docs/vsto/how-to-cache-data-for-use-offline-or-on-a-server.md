---
title: '방법: 오프 라인 이나 서버에서 사용 하기 위해 데이터 캐시'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], server use
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- offline data [Office development in Visual Studio]
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio], offline use
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 510d923d2503aeb6e07859813537c9094fe25b09
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63419696"
---
# <a name="how-to-cache-data-for-use-offline-or-on-a-server"></a>방법: 오프 라인 이나 서버에서 사용 하기 위해 데이터 캐시
  표시할 수 있습니다 문서에서 캐시할 데이터 항목을 사용할 수 있도록 오프 라인입니다. 또한 따라서 데이터에 대 한 문서에서 문서를 서버에 저장 된 경우 다른 코드를 조작할 수를 합니다.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 코드에서 데이터 항목을 선언한 경우 또는 캐시를 사용 하는 경우 데이터 항목을 표시할 수 있습니다는 <xref:System.Data.DataSet>에서 속성을 설정 하 여 합니다 **속성** 창입니다. 되지 않는 데이터 항목을 캐시 하는 경우는 <xref:System.Data.DataSet> 또는 <xref:System.Data.DataTable>, 문서에서 캐시 되 고 조건을 충족 하는지 확인 합니다. 자세한 내용은 [데이터 캐시](../vsto/caching-data.md)합니다.

> [!NOTE]
> 변수로 표시 되는 Visual Basic을 사용 하 여 만든 데이터 집합 **캐시 된** 하 고 **WithEvents** (에서 끌어 놓은 데이터 집합을 포함 하는 **데이터 원본** 창이 나 **도구 상자** 있는 합니다 **CacheInDocument** 속성이로 설정 **True**) 캐시에 있는 이름으로 접두사가 밑줄. 예를 들어 데이터 집합을 만들고 이름을 **고객이**의 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> 이름은 **_Customers** 캐시에 있습니다. 사용 하는 경우 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 지정 해야이 캐시 된 항목에 액세스 하려면 **_Customers** 대신 **고객**합니다.

### <a name="to-cache-data-in-the-document-using-code"></a>코드를 사용 하 여 문서에서 데이터를 캐시

1. 프로젝트에서 호스트 항목 클래스의 구성원으로 public 필드나 속성의 데이터 항목에 대 한 같은 선언 합니다 `ThisDocumen`Word 프로젝트의 클래스 또는 `ThisWorkbook` Excel 프로젝트의 클래스입니다.

2. 적용 된 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 멤버를 문서의 데이터 캐시에 저장할 데이터 항목을 표시 하는 특성입니다. 다음 예제에서는이 특성에 대 한 필드 선언을 적용을 <xref:System.Data.DataSet>입니다.

     [!code-csharp[Trin_VstcoreDataExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#11)]

3. 데이터 항목의 인스턴스를 만드는 코드를 추가 및 해당 데이터베이스에서 로드 하는 경우.

     데이터 항목은 처음 만들어질 때;만 로드 그런 다음 문서를 사용 하 여 캐시를 유지 하 고 업데이트 하는 다른 코드를 작성 해야 합니다.

### <a name="to-cache-a-dataset-in-the-document-by-using-the-properties-window"></a>속성 창을 사용 하 여 문서에서 데이터 집합 캐시

1. 데이터 집합을 사용 하 여 프로젝트에 데이터 소스를 추가 하 여 예를 들어, Visual Studio 디자이너에서 도구를 사용 하 여 프로젝트에 추가 합니다 **데이터 원본** 창입니다.

2. 아직를 디자이너에서 인스턴스를 선택 되어 있지 않고 데이터 집합의 인스턴스를 만듭니다.

3. 에 **속성** 창에서 설정 합니다 **CacheInDocument** 속성을 **True**합니다.

     자세한 내용은 [Office 프로젝트의 속성](../vsto/properties-in-office-projects.md)합니다.

4. 에 **속성** 창에서 합니다 **한정자** 속성을 **공용** (하며 기본값은 **내부**).

## <a name="see-also"></a>참고자료
- [데이터 캐시](../vsto/caching-data.md)
- [방법: Office 문서에서 데이터 원본을 프로그래밍 방식으로 캐시](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
- [방법: 암호로 보호 된 문서의 데이터 캐시](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [서버에 있는 문서의 데이터에 액세스](../vsto/accessing-data-in-documents-on-the-server.md)
- [데이터를 저장 합니다.](../data-tools/saving-data.md)
