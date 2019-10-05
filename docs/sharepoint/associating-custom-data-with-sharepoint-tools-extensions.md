---
title: SharePoint를 사용 하 여 사용자 지정 데이터 연결 도구 확장 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], associating custom data
- project items [SharePoint development in Visual Studio], associating custom data
- SharePoint project items, associating custom data
- SharePoint projects, associating custom data
- SharePoint development in Visual Studio, extensibility features
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9a2c1869791b250fb90c6a634f057797f3c57a62
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62987971"
---
# <a name="associate-custom-data-with-sharepoint-tools-extensions"></a>SharePoint 도구 확장과 사용자 지정 데이터 연결
  SharePoint 도구 확장의 특정 개체에 사용자 지정 데이터를 추가할 수 있습니다. 이 데이터 확장 프로그램의 다른 코드에서 나중에 액세스 하려면 확장 프로그램의 한 부분에 있는 경우에 유용 합니다. 데이터 저장 및 액세스 하는 사용자 지정 방법을 구현 하는 대신 확장의 개체를 사용 하 여 데이터를 연결할 수 있으며 나중에 동일한 개체에서 데이터를 다음 검색할 수 있습니다.

 개체에 사용자 지정 데이터 추가 Visual Studio에서 특정 항목에 관련 된 데이터를 유지 하려는 경우 유용 합니다. SharePoint 도구 확장은 Visual Studio에서 하므로 확장 하지 못할 여러 다른 항목을 사용 하 여 한 번만 로드 됩니다 (프로젝트와 같은 프로젝트 항목 또는 **서버 탐색기** 노드) 언제 든 지 합니다. 특정 항목에만 관련 된 사용자 지정 데이터를 사용 하는 경우 해당 항목을 나타내는 개체에 데이터를 추가할 수 있습니다.

 SharePoint 도구 확장의 개체에 사용자 지정 데이터를 추가 하면 데이터가 유지 되지 않습니다. 데이터는 개체의 수명 동안에 사용할 수 있습니다. 개체는 가비지 수집에서 회수는, 후 데이터가 손실 됩니다.

 SharePoint 프로젝트 시스템의 확장에서는 확장 언로드된 후 지속 되는 문자열 데이터를 저장할 수 있습니다. 자세한 내용은 [SharePoint 프로젝트 시스템의 확장에 데이터를 저장](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)합니다.

## <a name="objects-that-can-contain-custom-data"></a>사용자 지정 데이터를 포함할 수 있는 개체
 구현 하는 SharePoint 도구 개체 모델의 모든 개체에 사용자 지정 데이터를 추가할 수 있습니다는 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> 인터페이스입니다. 이 인터페이스는 속성 하나만 정의 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>, 사용자 지정 데이터 개체의 컬렉션인 합니다. 다음 유형을 구현 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>:

- <xref:Microsoft.VisualStudio.SharePoint.IMappedFolder>

- <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectMember>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>

- <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentContext>

- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>

- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>

- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition>

## <a name="add-and-retrieve-custom-data"></a>추가 및 사용자 지정 데이터를 검색 합니다.
 SharePoint 도구 확장의 개체에 사용자 지정 데이터를 추가 하려면 합니다 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 데이터를 추가 하 고 사용 하 여 개체의 속성을 <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A> 데이터 개체를 추가 하는 방법입니다.

 개체는 SharePoint 도구 확장에서 사용자 지정 데이터를 검색할 가져오기는 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 개체의 다음 메서드 중 하나를 사용 하는 속성:

- <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>. 이 메서드는 반환 **true** 데이터 개체가 있는 경우 또는 **false** 존재 하지 않는 경우. 값 형식 또는 참조 형식의 인스턴스를 검색 하려면이 메서드를 사용할 수 있습니다.

- <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>. 이 메서드가 반환 된 데이터 개체를 종료 하는 경우 또는 **null** 존재 하지 않는 경우. 참조 형식의 인스턴스를 검색에이 메서드를 사용할 수 있습니다.

  다음 코드 예제에서는 특정 데이터 개체는 프로젝트 항목과 연결 된 이미 있는지 여부를 결정 합니다. 데이터 개체는 이미 프로젝트 항목과 연결 된 경우에 개체를 추가 하는 코드는 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 프로젝트 항목의 속성입니다. 더 큰 예제의의 컨텍스트에서이 예제를 보려면 [방법: 사용자 지정 SharePoint 프로젝트 항목 형식에 속성 추가](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)합니다.

  [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#13)]
  [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#13)]

## <a name="see-also"></a>참고자료
- [SharePoint 도구 확장의 프로그래밍 개념 및 기능](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [연습: 항목 템플릿, 1 부를 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [연습: 웹 파트를 표시 하려면 서버 탐색기 확장](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [방법: SharePoint 프로젝트에 속성 추가](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [방법: 사용자 지정 SharePoint 프로젝트 항목 형식에 속성 추가](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
