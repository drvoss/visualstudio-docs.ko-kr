---
title: SharePoint 프로젝트 시스템의 확장에 데이터 저장 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
helpviewer_keywords:
- SharePoint project items, saving string data
- project items [SharePoint development in Visual Studio], saving string data
- projects [SharePoint development in Visual Studio], saving string data
- SharePoint projects, saving string data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 52b04490a646c7ced27d4a2d7f2344e27cbbae8b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62827247"
---
# <a name="save-data-in-extensions-of-the-sharepoint-project-system"></a>SharePoint 프로젝트 시스템의 확장에 데이터를 저장 합니다.
  SharePoint 프로젝트 시스템을 확장 하는 경우에 SharePoint 프로젝트를 닫은 후 지속 되는 문자열 데이터를 저장할 수 있습니다. 데이터는 일반적으로 특정 프로젝트 항목 또는 프로젝트 자체에 연결 됩니다.

 유지할 필요가 없는 데이터가 있는 경우 모든 개체를 구현 하는 SharePoint 도구 개체 모델에 데이터를 추가할 수 있습니다는 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> 인터페이스입니다. 자세한 내용은 [SharePoint 사용 하 여 사용자 지정 데이터 연결 도구 확장](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)합니다.

## <a name="save-data-that-is-associated-with-a-project-item"></a>프로젝트 항목과 연결 된 데이터를 저장 합니다.
 프로젝트 항목에 추가 하는 속성의 값과 같은 특정 SharePoint 프로젝트 항목을 사용 하 여 연결 된 데이터가 있는 경우 데이터를 저장할 수 있습니다 합니다 *.spdata* 프로젝트 항목에 대 한 파일입니다. 이 위해 사용 하 여 합니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> 의 속성을 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> 개체입니다. 이 속성을 추가 하는 데이터가 저장 되는 **ExtensionData** 요소에는 *.spdata* 프로젝트 항목에 대 한 파일입니다. 자세한 내용은 [ExtensionData 요소](../sharepoint/extensiondata-element.md)합니다.

 다음 코드 예제를 사용 하는 방법에 설명 합니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> 속성 사용자 지정 SharePoint 프로젝트 항목 형식에 정의 된 문자열 속성의 값을 저장 합니다. 더 큰 예제의의 컨텍스트에서이 예제를 보려면 [방법: 사용자 지정 SharePoint 프로젝트 항목 형식에 속성 추가](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)합니다.

 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#14)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#14)]

## <a name="save-data-that-is-associated-with-a-project"></a>프로젝트와 연결 된 데이터를 저장 합니다.
 SharePoint 프로젝트에 추가 하는 속성의 값과 같이 프로젝트 수준 데이터가 있는 경우 프로젝트 파일에 데이터를 저장할 수 있습니다 (합니다 *.csproj* 파일 또는 *.vbproj* 파일) 또는 프로젝트 사용자 옵션 파일 (합니다 *. csproj.user* 파일 또는 *. vbproj.user* 파일). 파일에서 데이터를 저장 하려는 데이터를 사용 하려는 방법에 따라 달라 집니다.

- SharePoint 프로젝트를 여는 모든 개발자가 사용할 수 있도록 데이터를 원하는 경우 프로젝트 파일에 데이터를 저장 합니다. 이 파일은 항상 체크 인 소스 제어 데이터베이스에이 파일의 데이터를 다른 개발자는 프로젝트를 체크 아웃가 사용할 수 있도록 합니다.

- 현재 개발자가 Visual Studio에서 SharePoint 프로젝트에만 사용할 수 있도록 데이터를 원하는 경우 프로젝트 사용자 옵션 파일에 데이터를 저장 합니다. 이 파일은 일반적으로 체크 인 되지 소스 제어 데이터베이스에 아니므로이 파일의 데이터는 프로젝트를 체크 아웃 하는 다른 개발자에 게 사용할 수 없습니다.

### <a name="save-data-to-the-project-file"></a>프로젝트 파일에 데이터를 저장 합니다.
 프로젝트 파일에 데이터를 저장 하려면 변환를 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> 개체를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> 개체를 사용 하 여는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> 메서드. 다음 코드 예제에서는이 메서드를 사용 하 여 프로젝트 파일에는 프로젝트 속성의 값을 저장 하는 방법에 설명 합니다. 큰 샘플의 컨텍스트에서이 예제를 보려면 [방법: SharePoint 프로젝트에 속성 추가](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)합니다.

 [!code-vb[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#3)]
 [!code-csharp[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#3)]

 변환에 대 한 자세한 내용은 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> Visual Studio 자동화 개체 모델 또는 통합 개체 모델의 다른 형식에 대 한 개체 참조 [SharePoint 프로젝트 시스템 형식과 기타 Visual Studio 프로젝트 형식간의변환](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).

### <a name="save-data-to-the-project-user-option-file"></a>프로젝트 사용자 옵션 파일에 데이터를 저장 합니다.
 프로젝트 사용자 옵션 파일에 데이터를 저장 하려면 사용 합니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> 의 속성은 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> 개체입니다. 다음 코드 예제에서는이 속성을 사용 하 여 프로젝트 사용자 옵션 파일에는 프로젝트 속성의 값을 저장 하는 방법에 설명 합니다. 큰 샘플의 컨텍스트에서이 예제를 보려면 [방법: SharePoint 프로젝트에 속성 추가](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)합니다.

 [!code-vb[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#2)]
 [!code-csharp[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#2)]

## <a name="see-also"></a>참고자료
- [SharePoint 프로젝트 시스템 확장](../sharepoint/extending-the-sharepoint-project-system.md)
- [SharePoint 도구 확장과 사용자 지정 데이터 연결](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
- [SharePoint 프로젝트 시스템 형식과 기타 Visual Studio 프로젝트 형식 간의 변환](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
