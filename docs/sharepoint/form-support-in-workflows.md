---
title: 워크플로에서 지원 구성 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 704e08524bb9aaf014dbd29e7df7361a7e1bbefe
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967411"
---
# <a name="form-support-in-workflows"></a>워크플로의 폼 지원
  네 가지 유형의 폼 워크플로에서 사용할 수 있습니다: 연결, 시작, 태스크 및 수정 합니다. 이러한 폼 형식 ASPX 양식은 또는 InfoPath 양식에 기반 할 수 있습니다. 수준의 지원 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 다음 표에 설명 된 여러 가지 요인에 따라 다릅니다. 특정 폼을 제공 합니다. 워크플로 양식 유형에 대 한 자세한 내용은 참조 하세요. [워크플로 양식 개요](http://go.microsoft.com/fwlink/?LinkId=185228)합니다.

## <a name="xml-refactoring"></a>XML 리팩터링
 ASPX 연결 또는 시작 폼을 추가 하는 경우는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 워크플로 프로젝트 항목 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 워크플로의 XML을 자동으로 리팩터링하여 *Elements.xml* 연결에 대 한 참조는 특성을 유지 하는 파일 또는 동기화 형식 이름 또는 배포 경로가 업데이트 될 때마다 초기화 폼 또는 폼 삭제 됩니다. 그러나 사용 하는 경우 다른 폼 형식 예: 태스크 또는 수정 양식, 워크플로에서 합니다 *Elements.xml* 파일 리팩터링 되지 않습니다.

## <a name="form-support-in-new-visual-studio-workflows"></a>새 Visual Studio 워크플로의 폼 지원
 다음 표에서 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 에서 만든 워크플로에서 ASPX 또는 InfoPath 폼에 다양 한 폼 형식에 대 한 지원을 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]합니다.

|양식 유형|ASPX 폼을 사용 하 여 Visual Studio에서 만든 워크플로|InfoPath 양식을 사용 하 여 Visual Studio에서 만든 워크플로|
|---------------|---------------------------------------------------------|-----------------------------------------------------------------|
|연결|-를 사용 하 여 워크플로에 추가할 수 있습니다 ASPX 연결 양식을 합니다 **워크플로 연결 양식** 항목 템플릿.<br />- *Elements.xml* 폼 추가, 이름이 변경 되거나 삭제 되거나 배포 경로가 변경 될 때 워크플로 파일은 리팩터링 합니다.<br />-자세한 내용은 참조 [연습: 연결 및 시작 Forms를 사용 하 여 워크플로 만드는](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)합니다.|-InfoPath 연결 양식 템플릿이 없는에서 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]합니다.<br />-간 통합이 없습니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 및 InfoPath 디자이너입니다.<br />- *Elements.xml* 워크플로 파일이 리팩터링 되지 않습니다.|
|시작|사용 하 여 워크플로를 추가할 수 있습니다-ASPX 양식을 합니다 **워크플로 시작 양식** 항목 템플릿.<br />- *Elements.xml* 폼 추가, 이름이 변경 되거나 삭제 되거나 배포 경로가 변경 될 때 워크플로 파일은 리팩터링 합니다.<br />-자세한 내용은 참조 [연습: 연결 및 시작 Forms를 사용 하 여 워크플로 만드는](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)합니다.|-InfoPath 연결 양식 템플릿이 없는에서 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]합니다.<br />-간 통합이 없습니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 및 InfoPath 디자이너입니다.<br />- *Elements.xml* 워크플로 파일이 리팩터링 되지 않습니다.|
|작업|-ASPX 작업 양식 서식 파일은 영어로 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]합니다. 응용 프로그램 페이지를 만들고 코드를 추가 해야 합니다.<br />- *Elements.xml* 워크플로 파일이 리팩터링 되지 않습니다.<br />-자세한 내용은 참조 [워크플로 작업 양식 (SharePoint Foundation)](http://go.microsoft.com/fwlink/?LinkId=187674)|-InfoPath 작업 양식 템플릿이 없는에서 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]합니다.<br />-간 통합이 없습니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 및 InfoPath 디자이너입니다.<br />- *Elements.xml* 워크플로 파일이 리팩터링 되지 않습니다.|
|수정|-ASPX 수정 양식 서식 파일은 영어로 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]합니다. 응용 프로그램 페이지를 만들고 코드를 추가 하면 수정 폼에 추가 해야 합니다.<br />- *Elements.xml* 워크플로 파일이 리팩터링 되지 않습니다. 수동으로 적절 하 게 편집 해야 합니다.<br />-자세한 내용은 참조 [워크플로 수정 양식 (SharePoint Foundation)](http://go.microsoft.com/fwlink/?LinkId=187675)|-InfoPath 수정 양식 템플릿이 없는에서 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]합니다.<br />-간 통합이 없습니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 및 InfoPath 디자이너입니다.<br />- *Elements.xml* 워크플로 파일이 리팩터링 되지 않습니다.|

## <a name="form-support-in-imported-sharepoint-reusable-workflows"></a>가져온된 SharePoint 재사용 가능한 워크플로의 폼 지원
 다음 표에서 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 로 가져올 수 없는 재사용 가능한 워크플로 SharePoint에서 ASPX 또는 InfoPath 폼에 다양 한 폼 형식에 대 한 지원을 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]합니다.

|양식 유형|SharePoint Designer에서 가져온 ASPX 양식은 있는 재사용 가능한 워크플로|SharePoint Designer에서 가져온 InfoPath 양식 있는 재사용 가능한 워크플로|
|---------------|-------------------------------------------------------------------------------| - |
|연결|-형식에서 참조 되는 *Elements.xml* 워크플로 파일입니다.<br />- *Elements.xml* 폼 변경 되거나 삭제 되거나 배포 경로가 변경 될 때 워크플로 파일은 리팩터링 합니다.|-폼을 가져온 되었지만 참조 되지 합니다 *Elements.xml* 워크플로.<br />- *Elements.xml* 워크플로 파일이 리팩터링 되지 않습니다.|
|시작|-폼에서 워크플로 통해 참조 되는 *Elements.xml* 워크플로 파일입니다.<br />- *Elements.xml* 폼 변경 되거나 삭제 되거나 배포 경로가 변경 될 때 워크플로 파일은 리팩터링 합니다.|-폼을 가져온 되었지만 참조 되지 합니다 *Elements.xml* 워크플로.<br />- *Elements.xml* 워크플로 파일이 리팩터링 되지 않습니다. **참고:**  규칙 및 속성 추가 및이 시나리오가 작동 하려면 변경 해야 합니다.|
|작업|-형식에서 참조 되는 *Elements.xml* 워크플로 파일입니다.<br />- *Elements.xml* 워크플로 파일이 리팩터링 되지 않습니다.|-폼을 가져온 되었지만 참조 되지 합니다 *Elements.xml* 워크플로.<br />- *Elements.xml* 워크플로 파일이 리팩터링 되지 않습니다. **참고:**  규칙 및 속성 추가 및이 시나리오가 작동 하려면 변경 해야 합니다.|
|수정|해당 사항 없음. SharePoint Designer에서 ASPX 수정 폼을 만들 수 없습니다.|해당 사항 없음. InfoPath 수정 양식 포함 되지 않은.wsp 파일에서 워크플로 내보낼 때 기본 제공 SharePoint 서버 워크플로 제외 하 고 SharePoint Designer에서 만들 수 없습니다.|

## <a name="see-also"></a>참고자료
- [연습: 연결 및 초기화 폼을 사용 하 여 워크플로 만들기](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)
- [SharePoint 워크플로 솔루션 만들기](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [기존 SharePoint 사이트에서 항목 가져오기](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
