---
title: SharePoint 프로젝트 항목 스키마 참조 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperty element
- SafeControls element
- SafeControl element
- .spdata files
- ExtensionData element
- FeatureProperties element
- ProjectOutputFile element
- Files element
- ProjectItemFolder element
- ProjectItemFile element
- ExtensionDataItem element
- ProjectItem element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bc15ff5c384ec63f99ed50a5f3c700efd7ba3c18
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63007721"
---
# <a name="sharepoint-project-item-schema-reference"></a>SharePoint 프로젝트 항목 스키마 참조
  Visual Studio를 사용 하 여 SharePoint 프로젝트 항목 스키마의 내용을 *.spdata* 파일입니다. *.spdata* 파일 내용 및 SharePoint 프로젝트 항목의 동작을 지정 합니다. SharePoint 프로젝트 항목의 내용에 대 한 자세한 내용은 참조 [항목 템플릿 및 SharePoint 프로젝트 항목에 대 한 프로젝트 템플릿 만들기](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)합니다.

 SharePoint 프로젝트 항목 스키마 ProjectItemModelSchema.xsd 이름이 고은 % Program Files (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas 기본적으로 설치.

 루트 요소는 [ProjectItem](../sharepoint/projectitem-element.md) 요소입니다. 다음 표에서 모든 스키마에서 정의 된 요소를 설명 합니다.

|요소|설명|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|SharePoint 프로젝트 항목에 연관 된 사용자 지정 데이터 항목의 컬렉션을 나타냅니다.|
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|키/값 형식의 SharePoint 프로젝트 항목과 연결 된 사용자 지정 데이터 항목을 나타냅니다. 키와 값을 모두 문자열 이어야 합니다.|
|[FeatureProperties](../sharepoint/featureproperties-element.md)|SharePoint에 배포 될 때 기능을 사용 하 여 포함 된 속성 값의 컬렉션을 나타냅니다. 기능이 배포 된 후에 코드에서 속성 값을 액세스할 수 있습니다.|
|[FeatureProperty](../sharepoint/featureproperty-element.md)|SharePoint에 배포 될 때 기능을 사용 하 여 포함 된 사용자 지정 속성을 나타냅니다. 기능이 배포 된 후에 코드에서 속성을 액세스할 수 있습니다.|
|[파일](../sharepoint/files-element.md)|기능 요소 파일이 나 프로젝트의 출력 예: SharePoint 프로젝트 항목을 함께 배포할 파일을 지정 합니다.|
|[ProjectItem](../sharepoint/projectitem-element.md)|SharePoint 프로젝트 항목을 나타냅니다.|
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|기능 요소를 포함할 파일을 프로젝트 항목을 사용 하 여 SharePoint에 배포 될 때와 같은 SharePoint 파일을 나타냅니다.|
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|매핑된 폴더를 나타냅니다.|
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|SharePoint에 배포할 때 프로젝트 항목과 함께 포함할 프로젝트의 출력을 나타냅니다.|
|[SafeControl](../sharepoint/safecontrol-element.md)|ASPX 컨트롤 또는 SharePoint 사이트의 모든 ASPX 페이지에 액세스 하려면 모든 사용자에 대 한 보안 지정 된 웹 파트를 나타냅니다.|
|[SafeControls](../sharepoint/safecontrols-element.md)|ASPX 컨트롤 및 SharePoint 사이트의 모든 ASPX 페이지에 액세스 하려면 모든 사용자에 대 한 안전한 것으로 지정 된 웹 파트의 컬렉션을 나타냅니다.|

## <a name="see-also"></a>참고자료
- [SharePoint 프로젝트 항목에 대 한 프로젝트 템플릿과 항목 템플릿 만들기](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
