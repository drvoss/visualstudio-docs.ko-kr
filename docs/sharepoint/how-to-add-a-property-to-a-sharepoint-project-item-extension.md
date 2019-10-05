---
title: '방법: SharePoint 프로젝트 항목 확장에 속성을 추가 합니다. | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 20a7abaa8c132b3cd1679ab95ed8154b8ca86502
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967242"
---
# <a name="how-to-add-a-property-to-a-sharepoint-project-item-extension"></a>방법: SharePoint 프로젝트 항목 확장에 속성 추가
  Visual Studio에 이미 설치 되어 있는 모든 SharePoint 프로젝트 항목 속성을 추가할 프로젝트 항목 확장을 사용할 수 있습니다. 속성에 표시 합니다 **속성** 창에서 프로젝트 항목을 선택 하는 경우 **솔루션 탐색기**합니다.

 다음 단계는 프로젝트 항목 확장을 이미 만들었다고 가정 합니다. 자세한 내용은 [방법: SharePoint 프로젝트 항목 확장명 만들기](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)합니다.

### <a name="to-add-a-property-to-a-project-item-extension"></a>프로젝트 항목 확장에 속성을 추가 하려면

1. 프로젝트 항목 형식에 추가 하는 속성을 나타내는 공용 속성을 사용 하 여 클래스를 정의 합니다. 프로젝트 항목 형식에 여러 속성을 추가 하려는 경우 동일한 클래스 또는 다른 클래스의 모든 속성을 정의할 수 있습니다.

2. 에 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> 메서드의 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> 구현, 핸들을 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> 의 이벤트를 *projectItemType* 매개 변수입니다.

3. 에 대 한 이벤트 처리기에서 합니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> 이벤트에 속성 클래스의 인스턴스를 추가 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> 이벤트 인수 매개 변수 컬렉션입니다.

## <a name="example"></a>예제
 다음 코드 예제에서는 명명 된 속성을 추가 하는 방법을 보여 줍니다 **속성의 예로** 이벤트 수신기 프로젝트 항목에 있습니다.

 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionproperty.cs#8)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionproperty.vb#8)]

### <a name="understand-the-code"></a>코드 이해
 동일한 인스턴스의 되도록를 `CustomProperties` 클래스 될 때마다 사용 됩니다는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> 이벤트의 발생에 속성 개체를 추가 하는 코드 예제는 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 이 이벤트가 발생 하는 시점에 프로젝트 첫 번째 항목의 속성입니다. 이 이벤트가 다시 발생 될 때마다이 개체를 검색 하는 코드입니다. 사용에 대 한 자세한 내용은 합니다 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 프로젝트 항목을 사용 하 여 데이터를 연결할 속성을 참조 하세요 [SharePoint 사용 하 여 사용자 지정 데이터 연결 도구 확장](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)합니다.

 속성 값을 변경 내용을 유지를 **설정** 에 대 한 접근자 `ExampleProperty` 새 값을 저장 합니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> 의 속성은 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> 개체와 연결 된 속성. 사용에 대 한 자세한 내용은 합니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> 프로젝트 항목을 사용 하 여 데이터를 유지 하는 속성 참조 [SharePoint 프로젝트 시스템의 확장에 데이터를 저장](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)합니다.

### <a name="specify-the-behavior-of-custom-properties"></a>사용자 지정 속성의 동작을 지정
 사용자 지정 속성을 나타나고 동작을 정의할 수 있습니다 합니다 **속성** 창에서 특성을 적용 하 여는 <xref:System.ComponentModel> 속성 정의에 네임 스페이스입니다. 다음 특성은 여러 시나리오에서 유용 합니다.

- <xref:System.ComponentModel.DisplayNameAttribute>: 에 표시 되는 속성의 이름을 지정 합니다 **속성** 창입니다.

- <xref:System.ComponentModel.DescriptionAttribute>: 맨 아래에 표시 되는 설명 문자열을 지정 합니다 **속성** 속성을 선택 하는 경우 창입니다.

- <xref:System.ComponentModel.DefaultValueAttribute>: 속성의 기본값을 지정 합니다.

- <xref:System.ComponentModel.TypeConverterAttribute>: 에 표시 되는 문자열 간에 사용자 지정 변환을 지정 합니다 **속성** 창과 문자열이 아닌 속성 값입니다.

- <xref:System.ComponentModel.EditorAttribute>: 속성을 수정 하는 데 사용자 지정 편집기를 지정 합니다.

## <a name="compile-the-code"></a>코드 컴파일
 이러한 예제에는 다음 어셈블리에 대 한 참조를 사용 하 여 클래스 라이브러리 프로젝트를 필요합니다.

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>확장 배포
 확장 배포를 만들려면를 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 어셈블리 및 확장을 사용 하 여 배포 하려는 다른 파일에 대 한 패키지 (VSIX) 확장 합니다. 자세한 내용은 [Visual Studio에서 SharePoint 도구의 확장을 배포할](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)합니다.

## <a name="see-also"></a>참고자료
- [방법: SharePoint 프로젝트 항목 확장명 만들기](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [방법: SharePoint 프로젝트 항목 확장에 바로 가기 메뉴 항목 추가](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)
- [SharePoint 프로젝트 항목 확장](../sharepoint/extending-sharepoint-project-items.md)
- [연습: SharePoint 프로젝트 항목 형식 확장](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
