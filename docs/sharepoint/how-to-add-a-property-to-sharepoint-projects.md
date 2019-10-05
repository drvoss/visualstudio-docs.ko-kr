---
title: '방법: SharePoint 프로젝트에 속성 추가 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a6f1ecd427b1c715649bc2118be5ab384a74c585
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967216"
---
# <a name="how-to-add-a-property-to-sharepoint-projects"></a>방법: SharePoint 프로젝트에 속성 추가
  SharePoint 프로젝트 속성을 추가 하려면 프로젝트 확장을 사용할 수 있습니다. 속성에 표시 된 **속성** 창에서 프로젝트를 선택 하면 **솔루션 탐색기**합니다.

 다음 단계는 프로젝트 확장을 이미 만들었다고 가정 합니다. 자세한 내용은 [방법: SharePoint 프로젝트 확장명 만들기](../sharepoint/how-to-create-a-sharepoint-project-extension.md)합니다.

### <a name="to-add-a-property-to-a-sharepoint-project"></a>SharePoint 프로젝트에 속성을 추가 하려면

1. SharePoint 프로젝트에 추가 하는 속성을 나타내는 공용 속성을 사용 하 여 클래스를 정의 합니다. 여러 속성을 추가 하려는 경우 동일한 클래스 또는 다른 클래스의 모든 속성을 정의할 수 있습니다.

2. 에 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> 메서드의 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 구현, 핸들을 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> 의 이벤트를 *projectService* 매개 변수입니다.

3. 에 대 한 이벤트 처리기에서 합니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> 이벤트에 속성 클래스의 인스턴스를 추가 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A> 이벤트 인수 매개 변수 컬렉션입니다.

## <a name="example"></a>예제
 다음 코드 예제에는 SharePoint 프로젝트에 두 속성을 추가 하는 방법을 보여 줍니다. 프로젝트 사용자 옵션 파일에 해당 데이터를 유지 하는 하나의 속성 (합니다 *. csproj.user* 파일 또는 *. vbproj.user* 파일). 프로젝트 파일에서 해당 데이터를 유지 하는 다른 속성 (*.csproj* 파일 또는 *.vbproj* 파일).

 [!code-vb[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#1)]
 [!code-csharp[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#1)]

### <a name="understand-the-code"></a>코드 이해
 동일한 인스턴스의 되도록를 `CustomProjectProperties` 클래스 될 때마다 사용 됩니다는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> 이벤트의 발생에 속성 개체를 추가 하는 코드 예제는 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 이 이벤트가 발생 시점에 첫 번째 프로젝트의 속성입니다. 이 이벤트가 다시 발생 될 때마다이 개체를 검색 하는 코드입니다. 사용에 대 한 자세한 내용은 합니다 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 프로젝트를 사용 하 여 데이터를 연결할 속성을 참조 하세요 [SharePoint 사용 하 여 사용자 지정 데이터 연결 도구 확장](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)합니다.

 속성 값을 변경 내용을 유지 합니다 **설정** 다음 Api를 사용 하 여 속성에 대 한 접근자:

- `CustomUserFileProperty` 사용 하 여 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> 프로젝트 사용자 옵션 파일에 해당 값을 저장 하는 속성입니다.

- `CustomProjectFileProperty` 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> 프로젝트 파일에 해당 값을 저장 하는 방법입니다.

  이러한 파일에 데이터를 유지 하는 방법에 대 한 자세한 내용은 참조 하세요. [SharePoint 프로젝트 시스템의 확장에 데이터를 저장](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)합니다.

### <a name="specify-the-behavior-of-custom-properties"></a>사용자 지정 속성의 동작을 지정
 사용자 지정 속성을 나타나고 동작을 정의할 수 있습니다 합니다 **속성** 창에서 특성을 적용 하 여는 <xref:System.ComponentModel> 속성 정의에 네임 스페이스입니다. 다음 특성은 여러 시나리오에서 유용 합니다.

- <xref:System.ComponentModel.DisplayNameAttribute>: 에 표시 되는 속성의 이름을 지정 합니다 **속성** 창입니다.

- <xref:System.ComponentModel.DescriptionAttribute>: 맨 아래에 표시 되는 설명 문자열을 지정 합니다 **속성** 속성을 선택 하는 경우 창입니다.

- <xref:System.ComponentModel.DefaultValueAttribute>: 속성의 기본값을 지정 합니다.

- <xref:System.ComponentModel.TypeConverterAttribute>: 에 표시 되는 문자열 간에 사용자 지정 변환을 지정 합니다 **속성** 창과 문자열이 아닌 속성 값입니다.

- <xref:System.ComponentModel.EditorAttribute>: 속성을 수정 하는 데 사용자 지정 편집기를 지정 합니다.

## <a name="compile-the-code"></a>코드 컴파일
 이 예제에는 다음 어셈블리에 대 한 참조가 필요합니다.

- Microsoft.VisualStudio.SharePoint

- Microsoft.VisualStudio.Shell

- Microsoft.VisualStudio.Shell.Interop

- Microsoft.VisualStudio.Shell.Interop.8.0

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>확장 배포
 확장 배포를 만들려면를 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 어셈블리 및 확장을 사용 하 여 배포 하려는 다른 파일에 대 한 패키지 (VSIX) 확장 합니다. 자세한 내용은 [Visual Studio에서 SharePoint 도구의 확장을 배포할](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)합니다.

## <a name="see-also"></a>참고자료
- [SharePoint 프로젝트 확장](../sharepoint/extending-sharepoint-projects.md)
- [방법: SharePoint 프로젝트 확장명 만들기](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [방법: 바로 가기 메뉴 항목을 SharePoint 프로젝트에 추가](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [SharePoint 프로젝트 시스템 확장](../sharepoint/extending-the-sharepoint-project-system.md)
