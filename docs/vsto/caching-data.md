---
title: 데이터 캐시
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], about caching data
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c6e0f6d7fcf9920ddb8861712b7c5f8bf04506fc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62939417"
---
# <a name="cache-data"></a>데이터 캐시
  오프 라인으로 또는 Microsoft Office Word 또는 Microsoft Office Excel을 열지 않고 데이터를 사용할 수 있도록 문서 수준 사용자 지정 데이터 개체를 캐시할 수 있습니다. 개체를 캐시 하려면 개체의 특정 요구 사항을 충족 하는 데이터 형식이 있어야 합니다. .NET Framework의 많은 일반적인 데이터 형식을 포함 하는 이러한 요구 사항을 충족 <xref:System.String>하십시오 <xref:System.Data.DataSet>, 및 <xref:System.Data.DataTable>합니다.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 두 가지 방법으로 데이터 캐시에 개체를 추가할 수 있습니다.

- 추가할 개체 데이터 캐시에는 솔루션을 빌드할 때 적용 된 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 특성을 개체 선언 합니다. 자세한 내용은 [방법: 오프 라인 이나 서버에서 사용 하기 위해 데이터를 캐시](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)합니다.

- 런타임에 프로그래밍 방식으로 데이터 캐시에 개체 추가 하려면 사용 합니다 `StartCaching` 와 같은 호스트의 메서드 항목을 합니다 `ThisDocument` 또는 `ThisWorkbook` 클래스입니다. 자세한 내용은 [방법: Office 문서에서 데이터 원본을 프로그래밍 방식으로 캐시](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)합니다.

  데이터 캐시에 개체를 추가한 후에 액세스 하 고 Word 또는 Excel을 시작 하지 않고 캐시 된 데이터를 수정할 수 있습니다. 자세한 내용은 [서버에서 문서 데이터에에서 액세스](../vsto/accessing-data-in-documents-on-the-server.md)합니다.

## <a name="requirements-for-data-objects-to-be-cached"></a>데이터 개체를 캐시에 대 한 요구 사항
 솔루션의 데이터 개체를 캐시 하려면 개체에는 이러한 요구 사항을 충족 해야 합니다.

- 와 같은 공용 읽기/쓰기 필드 또는 호스트 항목의 속성 이어야 합니다 `ThisDocument` 또는 `ThisWorkbook` 클래스입니다.

- 매개 변수가 있는 다른 속성 또는 인덱서가 수 없습니다.

  또한 데이터 개체를 통해 직렬화 할 수 있어야 합니다 <xref:System.Xml.Serialization.XmlSerializer> 클래스 즉, 개체의 형식이 특징이 있어야 합니다.:

- 공용 유형 이어야 합니다.

- 매개 변수가 없는 public 생성자를 있습니다.

- 추가 보안 권한이 필요한 코드를 실행 하지 않습니다.

- 읽기/쓰기 public 속성만 (다른 속성은 무시 됨)을 노출 합니다.

- 다차원 배열 (중첩 된 배열은 허용 됩니다.)를 노출 하지 않습니다.

- 속성 및 필드에서 인터페이스를 반환 하지 않습니다.

- 구현 하지 <xref:System.Collections.IDictionary> 경우 컬렉션입니다.

  데이터 개체를 캐시 하는 경우는 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 개체에 저장 된 XML 문자열로 serialize를 *사용자 지정 XML 부분* 문서의 합니다. 자세한 내용은 [사용자 지정 XML 부분 개요](../vsto/custom-xml-parts-overview.md)합니다.

## <a name="cached-data-size-limits"></a>캐시 된 데이터 크기 제한
 데이터 캐시의 개별 개체의 크기를 문서에서 데이터 캐시에 추가 하는 데이터의 총 크기를 몇 가지 제한이 있습니다. 이러한 한도 초과 하면 응용 프로그램 데이터 캐시에 데이터를 저장할 때 예기치 않게 닫힐 수 있습니다.

 이러한 한도 방지 하려면 다음이 지침을 따르세요.

- 10MB 보다 큰 개체 데이터 캐시에 추가 하지 마세요.

- 단일 문서에서 데이터 캐시에는 100MB 보다 큰 전체 데이터를 추가 하지 마세요.

  이들은 대략적인 값입니다. 정확한 제한 사용 가능한 RAM 및 실행 중인 프로세스의 수를 포함 하 여 여러 가지 요인에 따라 달라 집니다.

## <a name="control-the-behavior-of-cached-objects"></a>캐시 된 개체의 동작을 제어
 캐시 된 개체의 동작을 보다 더 잘 제어를 구현할 수 있습니다는 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> 캐시 된 개체의 형식에 대 한 인터페이스입니다. 예를 들어, 개체 변경 되었을 때 사용자가 알림을 하는 방법을 제어 하려는 경우이 인터페이스를 구현할 수 있습니다. 구현 하는 방법을 보여 주는 코드 예제 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>를 참조 합니다 `ControlCollection` 동적 컨트롤 샘플 Excel 및 Word에서 동적 컨트롤 샘플 클래스 [Office 개발 샘플 및 연습](../vsto/office-development-samples-and-walkthroughs.md)합니다.

## <a name="persist-changes-to-cached-data-in-password-protected-documents"></a>암호로 보호 된 문서에서 캐시 된 데이터의 변경 내용을 유지 합니다.
 암호로 보호 되는 문서에서 데이터 개체를 캐시 하는 경우 캐시 된 데이터 변경 내용이 저장 되지 않습니다. 두 메서드를 재정의 하 여 캐시 된 데이터 변경 내용을 저장할 수 있습니다. 문서를 저장 하는 경우 보호를 일시적으로 제거 하려면 이러한 메서드를 재정의 한 다음 저장 후 보호를 다시 적용 작업이 완료 되었습니다.

 자세한 내용은 [방법: 암호로 보호 된 문서의 데이터 캐시](../vsto/how-to-cache-data-in-a-password-protected-document.md)합니다.

## <a name="prevent-data-loss-when-adding-null-values-to-the-data-cache"></a>데이터 캐시에 null 값을 추가할 때 데이터 손실을 방지합니다
 데이터 캐시에 개체를 추가 하면 캐시 된 개체의 모든 초기화 해야 아닌**null** 문서를 저장 하 고 종료 하기 전에 값입니다. 모든 캐시 된 개체에는 **null** 문서를 저장 하 고 닫은 경우 값을 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 자동으로 데이터 캐시에서 캐시 된 개체를 모두 제거 됩니다.

 사용 하 여 개체를 추가 하는 경우를 **null** 데이터 캐시를 사용 하 여 값을 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 특성 디자인 타임에 사용할 수 있습니다는 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 문서를 열기 전에 캐시 된 데이터를 초기화 하기 위해 클래스 개체입니다. Word 또는 Excel을 최종 사용자가 문서를 열기 전에 설치 하지 않고 서버에서 캐시 된 데이터를 초기화 하려는 경우에 유용 합니다. 자세한 내용은 [서버에서 문서 데이터에에서 액세스](../vsto/accessing-data-in-documents-on-the-server.md)합니다.

## <a name="see-also"></a>참고자료
- [방법: 오프 라인 이나 서버에서 사용 하기 위해 데이터 캐시](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [방법: Office 문서에서 데이터 원본을 프로그래밍 방식으로 캐시](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
- [방법: 암호로 보호 된 문서의 데이터 캐시](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [연습: 캐시 된 데이터 집합을 사용 하 여 마스터-세부 관계를 만들려면](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)
