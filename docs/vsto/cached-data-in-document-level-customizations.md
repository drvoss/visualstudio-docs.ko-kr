---
title: 문서 수준 사용자 지정의 캐시 된 데이터
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data islands [Office development in Visual Studio]
- view [Office development in Visual Studio]
- caching data [Office development in Visual Studio], about caching data
- data caching [Office development in Visual Studio], about data caching
- data [Office development in Visual Studio], cache
- data [Office development in Visual Studio], document-level solutions
- document-level customizations [Office development in Visual Studio], data model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 62b0d04e37072af1f0053a6e395edcb856a115c1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62939321"
---
# <a name="cached-data-in-document-level-customizations"></a>문서 수준 사용자 지정의 캐시 된 데이터
  문서 수준 사용자 지정의 주된 목적은 Office 문서에는 보기에서 데이터를 분리 하는 것입니다. 데이터 숫자와 텍스트를 포함 하 여 문서에 저장 된 정보를 가리킵니다. 보기는 사용자 인터페이스와 Microsoft Office Word 및 Microsoft Office Excel의 개체 모델을 가리킵니다.

 Visual Studio로 포함 되어야 하는 데이터를 사용 하 여 문서 수준 사용자 지정 보기에서 데이터를 분리를 *데이터 아일랜드*라고도 합니다 *데이터 캐시*합니다. 읽기 또는 Word 또는 Excel을 시작 하지 않고 직접 데이터를 수정할 수 있습니다. Microsoft Office가 설치 되지 않은 서버에 있는 문서의 데이터를 수정 해야 하는 경우에 유용 합니다. Word 및 Excel 클라이언트 환경;에서 사용할 수는 서버에서 실행 되도록 설계 되지 않은 것입니다.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 문서 수준 사용자 지정 하는 방법에 대 한 자세한 내용은 참조 하십시오 [Office 솔루션 개발 개요 &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) 하 고 [문서 수준 사용자 지정 아키텍처](../vsto/architecture-of-document-level-customizations.md).

## <a name="understand-the-cached-data-programming-model"></a>캐시 된 데이터 프로그래밍 모델을 이해
 데이터 아일랜드는 특정 요구 사항을 충족 하는 솔루션의 모든 개체를 포함할 수 있습니다. 이러한 개체에 포함 <xref:System.Data.DataSet> 개체를 <xref:System.Data.DataTable> 개체 및가 serialize 할 수 있는 다른 모든 개체는 <xref:System.Xml.Serialization.XmlSerializer> 클래스입니다. 자세한 내용은 [데이터 캐시](../vsto/caching-data.md)합니다.

 캐시 된 데이터에 대 한 보기를 제공 하려면 Windows Forms 컨트롤을 바인딩할 수 있습니다 하 고 *호스트 컨트롤* 문서 데이터 아일랜드에서 개체를 합니다. 데이터 아일랜드 및 데이터 바인딩된 컨트롤 간의 데이터 바인딩을 동기화를 유지 합니다. 또한 컨트롤에 종속 되는 데이터에 유효성 검사 코드를 추가할 수 있습니다. 자세한 내용은 [Office 솔루션의 컨트롤에 데이터 바인딩](../vsto/binding-data-to-controls-in-office-solutions.md)합니다.

 호스트 컨트롤은 Excel 및 Word 개체 모델에서 네이티브 개체의 버전을 확장 합니다. 네이티브 개체와 달리 관리 되는 데이터 개체에 직접 호스트 컨트롤을 바인딩할 수 있습니다. 자세한 내용은 [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md) 하 고 [Office 문서 개요에서 Windows Forms 컨트롤](../vsto/windows-forms-controls-on-office-documents-overview.md)합니다.

## <a name="access-cached-data-on-the-server"></a>액세스는 서버의 데이터 캐시
 문서의 캐시 된 데이터에 액세스 하려면 사용할 수는 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 클래스입니다. 이 클래스의 일부인는 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], Excel 또는 Word를 실행 하지 않고 서버에서 사용할 수 있습니다. 사용자 문서를 열면 후 캐시 된 데이터를 수정 하 고 데이터에 바인딩되는 모든 컨트롤의 변경 내용을 자동으로 동기화 됩니다 업데이트 된 데이터를 사용 하 여 사용자가 표시 됩니다. 자세한 내용은 [서버에서 문서 데이터에에서 액세스](../vsto/accessing-data-in-documents-on-the-server.md)합니다.

 Excel 및 Word에 클라이언트에서 보기에 서버에서 데이터를 쓸 필요 하지 않습니다. Excel 및 Word도 필요가 없습니다를 서버에 설치 되어야 합니다. 이 향상 된 확장성 및 데이터 아일랜드를 포함 하는 문서의 빠른 일괄 처리를 수행 하는 기능을 제공 합니다.

## <a name="data-caching-for-offline-use"></a>오프 라인 사용을 위한 데이터 캐싱
 오프 라인 시나리오를 지원 데이터 아일랜드에 데이터를 저장 합니다. 사용자는 먼저가 문서를 열거나 문서 서버에서 요청을 하는 경우 데이터 아일랜드 가장 최근 데이터로 채워집니다. 데이터 아일랜드 문서에서 캐시 되 고 오프 라인으로 사용할 수 됩니다. 사용자 (및 코드)는 사용할 수 있는 라이브 연결이 없는 경우에 데이터를 조작할 수 있습니다. 사용자는 다음 작업을 다시 연결 되 면 데이터 변경 내용은 서버 데이터 원본에 다시 전파할 수 있습니다.

## <a name="cached-data-and-custom-xml-parts-compared"></a>캐시 된 데이터와 비교 하는 사용자 지정 XML 부분
 사용자 지정 XML 부분 임의의 XML 문서에 저장 하는 방법으로 2007 Microsoft Office system에서 도입 되었습니다. 사용자 지정 XML 부분의 데이터 캐시와 동일한 시나리오에서 유용 하지만, 일부의 차이점이 데이터 고립 영역 간의 사용자 지정 XML 부분입니다. 사용자 지정 XML 부분에 대 한 자세한 내용은 참조 하세요. [사용자 지정 XML 부분 개요](../vsto/custom-xml-parts-overview.md)합니다.

 다음 표에서 차이점 및 유사점을 보여 줍니다.

||데이터 캐시|사용자 지정 XML 부분|
|-|----------------|----------------------|
|Office 응용 프로그램 사용할 수 있습니다.|다음 응용 프로그램에 대 한 문서 수준 사용자 지정 합니다.<br /><br /> -   Excel<br />-   Word|다음 응용 프로그램에 대 한 문서 수준 및 응용 프로그램 수준 솔루션:<br /><br /> -   Excel<br />-   PowerPoint<br />-   Word|
|어떤 유형의 데이터를 저장할 수 있습니다?|특정 요구 사항을 충족 하는 사용자 지정 어셈블리의 모든 공용 개체입니다. 자세한 내용은 [데이터 캐시](../vsto/caching-data.md)합니다.|모든 XML 데이터입니다.|
|Microsoft Office 응용 프로그램을 시작 하지 않고 데이터에 액세스할 수 있습니다.|사용 하 여 예는 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 에서 제공 하는 클래스는 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]합니다.|클래스를 사용 하 여 예는 <xref:System.IO.Packaging> 네임 스페이스 또는 Open XML 형식 SDK를 사용 하 여 합니다.|

## <a name="see-also"></a>참고자료
- [Office 솔루션의 데이터](../vsto/data-in-office-solutions.md)
- [Visual Studio에서 Office 솔루션의 아키텍처](../vsto/architecture-of-office-solutions-in-visual-studio.md)
